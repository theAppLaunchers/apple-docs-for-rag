

- Matter
-  Onboarding a Matter device 

Article

# Onboarding a Matter device

Prepare your app to discover and control a Matter device.

## Overview

If you want your app to interact with a Matter device, you need to commission it. *Commissioning* a Matter device makes it a part of your *fabric*, which is a collection of Matter devices that communicate with each other.

You can securely commission a Matter device using certificates. Generate your own certificates using MTRCertificates or another process. Alternatively, you can provide a root MTRKeypair, and the Matter framework generates certificates for you.

### Obtain the onboarding payload

The MatterSupport framework provides an onboarding payload that you use to discover a device. Implement commissionDevice(in:onboardingPayload:commissioningID:) to obtain the onboarding payload, then securely commission a Matter device using MTRDeviceController. For more information, see Adding Matter support to your ecosystem.

### Provide persistent storage

Implement MTRStorage so that the Matter framework can store and retrieve persistent data, then create an instance of that object and pass it to an instance of MTRDeviceControllerFactoryParams. Set the factory parameter object’s productAttestationAuthorityCertificates to an array of trusted Matter certificates.

Obtain a MTRDeviceControllerFactory shared instance, then call start(_:) and handle any errors that may occur.

```
class MyStorage : NSObject, MTRStorage {
    func storageData(forKey key: String) -> Data? {
        // Return the data for the given key, if any.
    }

    func setStorageData(_ value: Data, forKey key: String) -> Bool {
        // Store the data for the given key. Return true on success,
        // false on failure.
    }

    func removeStorageData(forKey key: String) -> Bool {
        // Remove the given key from the storage. Return true on success,
        // false on failure.
    }
}

// Obtain the controller factory.
let factory = MTRDeviceControllerFactory.sharedInstance()

let storage = MyStorage()
let factoryParams = MTRDeviceControllerFactoryParams(storage: storage)

// Set `factoryParams.productAttestationAuthorityCertificates` to an
// array of trusted Matter PAA certificates.

do {
    // Start the controller factory.
    try factory.start(factoryParams)
} catch {
    // Handle any errors.
}
```

### Set up security for the commissioning

Create an Identity Protection Key (IPK) and save it to iCloud Keychain. You need this IPK every time you start the controller for this fabric.

```
guard let ipk = NSMutableData(length: 16) else {
    return
}

let status = SecRandomCopyBytes(kSecRandomDefault, ipk.count, ipk.mutableBytes)

if status != errSecSuccess {
    // Handle any errors.
} else {
    // Save the IPK in the keychain.
}
```

Next, create MTRDeviceControllerStartupParams. If you’re providing your own operational, intermediate, and root certificates, implement MTROperationalCertificateIssuer and provide it to the controller so you can issue certificates to devices you commission.

```
class MyCertificateIssuer : NSObject, MTROperationalCertificateIssuer
{
    func issueOperationalCertificate(forRequest csrInfo: MTROperationalCSRInfo, attestationInfo: MTRDeviceAttestationInfo, controller: MTRDeviceController) async throws -> MTROperationalCertificateChain {
        // Issue your certificates here.
    }

    var shouldSkipAttestationCertificateValidation: Bool = false    
}

let params = MTRDeviceControllerStartupParams(ipk: ipk, operationalKeypair: myKeypair, operationalCertificate: operationalCertificate, intermediateCertificate: nil, rootCertificate: rootCertificate)
params.operationalCertificateIssuer = MyCertificateIssuer()
params.operationalCertificateIssuerQueue = DispatchQueue(label: "Certificate issuer queue")
```

Otherwise, pass in the IPK, a fabric identifier of your choosing, and the root MTRKeypair you created earlier. In this case, the Matter framework creates the certificates.

```
let params = MTRDeviceControllerStartupParams(ipk: ipk, 
fabricID: fabricID, nocSigner: myRootKeypair)
```

Important

Store the root key and IPK in iCloud Keychain. Make sure you use the same fabric identifier every time you create this controller.

In either case, set `params.vendorID` to your Connectivity Standards Alliance-assigned vendor identifier.

### Commission the Matter device

Before you start commissioning, create a controller. If you’re creating a controller for this fabric for the first time, call createController(onNewFabric:); otherwise, call createController(onExistingFabric:).

```
let controller: MTRDeviceController
do {
    controller = try factory.createController(onNewFabric: params)
} catch {
    do {
        controller = try factory.createController(onExistingFabric: params)
    } catch {
        // Handle errors.
    }
}
```

Implement the delegate methods to receive callbacks as the commissioning progresses, then call setDeviceControllerDelegate(_:queue:) to register the delegate.

Create an MTRSetupPayload with init(onboardingPayload:), then call setupCommissioningSession(with:newNodeID:) with the MTRSetupPayload object and the node ID to assign to the device. When the commissioning session is set up, the framework calls controller(_:commissioningSessionEstablishmentDone:).

Call commissionNode(withID:commissioningParams:) with the node ID and commissioning parameters. When commissioning completes, the framework notifies your delegate with onCommissioningComplete(_:).

```
let nodeID = 1

class MyControllerDelegate : NSObject, MTRDeviceControllerDelegate {
    func controller(_ controller: MTRDeviceController, 
statusUpdate status: MTRCommissioningStatus) {
        // Check for `MTRCommissioningStatus.failed`, and if so, handle it.
    }

    func controller(_ controller: MTRDeviceController, 
commissioningSessionEstablishmentDone error: Error?) {
        // Check for error and handle it.
        do {
            // `myDesiredNodeID` must match the node ID passed to 
            // `setupCommissioningSessionWithPayload`.
            try controller.commissionNode(withID: nodeID,
commissioningParams: MTRCommissioningParameters())
        } catch {
            // Handle failure to start commissioning the node.
        }

        // Keep waiting for `commissioningComplete`.
    }

    func controller(_ controller: MTRDeviceController, 
commissioningComplete error: Error?,
nodeID: NSNumber?) {
        // Check for error and handle it.
        // If no error, node is commissioned with `nodeID` as its node ID.
    }
}

// Create the delegate and set it.
let myDelegate = MyControllerDelegate()
controller.setDevicecontrollerDelegate(myDelegate, queue: )

// Create the `MTRSetupPayload` then start the commissioning.
let payload = MTRSetupPayload.init(onboardingPayload:onboardingPayload)
controller.setupCommissioningSession(with: payload, newNodeID: nodeID)
```

