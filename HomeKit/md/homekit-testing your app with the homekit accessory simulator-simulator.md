

- HomeKit
-  Testing your app with the HomeKit Accessory Simulator 

Article

# Testing your app with the HomeKit Accessory Simulator

Install the HomeKit Accessory Simulator to help you debug your HomeKit-enabled app.

## Overview

While developing your HomeKit-enabled app, you might not have physical access to all the kinds of accessories that you want your app to control. To test your app, install the HomeKit Accessory Simulator (HAS) to simulate any accessories you don’t have, or to help automate your testing process.

HAS runs on your Mac, simulating accessories that you define as a supplement to any physical accessories in your network. You can create accessories with both standard and custom services and characteristics. You can use your Mac’s camera to simulate network cameras and video doorbells. You can also create bridges and bridged accessories to represent more complex network architectures.

### Download the HomeKit Accessory Simulator

You download the HAS as part of the *Additional Tools for Xcode* package found on the More Downloads for Apple Developers page, which is part of the Apple developer portal. Choose the version of the package that matches your version of Xcode.

As a convenience, Xcode provides a link to the download page from the Capabilities pane. Xcode displays a button embedded in the HomeKit capability that takes you directly to the download page in Safari.

After downloading the disk image file, open it and navigate to the `Hardware` folder. Drag the `HomeKitAccessorySimulator.app` from there to your `Applications` folder. Double-click to launch the simulator.

### Add accessories, services, and characteristics

Accessories in a home automation network are physical devices like light bulbs or garage door openers. Accessories provide control points called services. For example, a garage door opener might offer a door opener and a light. Each service, in turn, has characteristics—the values that describe and control the service. The light has a power state (on or off), a brightness level, and so on. Accessories also have hidden services, like the accessory information service that provides manufacturing information.

In the HomeKit Accessory Simulator, define accessories that you can use with your app. For details, see the *HomeKit Accessory Simulation Help*, accessible through the simulator’s `Help` menu.

**Add an accessory.** Assign a name and provide other identifying details. An accessory isn’t typically the user’s main focus, but does serve as a logical container for the services that the user cares about. When you create an accessory, HAS adds the accessory information service by default based on the information you provide.

**Add one or more services to the accessory.** Add as many additional services as you need, potentially including hidden services. For each, specify a service type using one of the standard values in Accessory Service Types, or using a custom service with a new, unique identifier. Give each service a unique name. For user-visible services, the user might later change the name using the Home app, or using your app.

**Add or modify service characteristics.** HAS populates standard services with a set of standard characteristics for that service, but you can adjust these to match the specific devices you want to model. For example, if a light bulb offers a fade-to-off feature with configurable timing, you might add a custom characteristic indicating the fade rate. The Home app doesn’t expose custom characteristics to the user, but you can control them from your own app.

### Associate the accessory with the network

To be able to access simulated accessories from a HomeKit enabled app, you associate them with a home network. You can do this from any device on your local area network running the Home app, which is installed on all iOS devices by default. The accessory becomes part of the logged-in user’s home network. From the Home or Rooms tab, tap the plus button and choose Add Accessory. Then follow the instructions in the dialog that appears.

Alternatively, you can call the addAndSetupAccessories(completionHandler:) method from your app.

```
home?.addAndSetupAccessories(completionHandler: { error in
    if let error = error {
        // Handle error
    } else {
        self.tableView.reloadData()
    }
})
```

This generates the same accessory association flow as the one presented in the Home app, and produces the same result. Doing it from within your app offers the advantage of being able to work on the iOS Simulator, where the Home app isn’t available.

Important

If you add an accessory on a device, including an iOS Simulator, without a logged-in iCloud account, the accessory is isolated to that device. This means that if you add an accessory to an iPhone simulator and then switch over to using an iPad simulator, you have to reassociate the accessory for it to appear in the new environment.

### Observe and change characteristic values

After the simulated accessory is part of the home automation network, you can find it and control it from your app just as you would a real accessory.

Changes that you make to characteristics in your app show up immediately in HAS. For example, if you let the user switch a light bulb off in your app with a toggle switch, the state of the light bulb changes right away in the HAS interface to match. When you implement accessory delegate methods like accessory(_:service:didUpdateValueFor:), changes made with HAS show up in your app right away as well.

## See Also

### Home Manager

Configuring a home automation device

Give users a familiar experience when they manage HomeKit accessories.

class HMHomeManager

The manager for a collection of one or more of a user’s homes.

