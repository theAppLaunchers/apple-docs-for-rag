

- Network Extension
- Local push connectivity
-  Maintaining a Reliable Network Connection 

Article

# Maintaining a Reliable Network Connection

Implement your Local Push Connectivity app to ensure delivery of notifications.

## Overview

By implementing Local Push Connectivity, your app can perform many of the tasks provided by Apple Push Notification Service (APNs), even on restricted or isolated networks where APNs is unavailable. Create push notifications by delivering messages from a server to your client, which then uses a local notification or CallKit to alert the user.

When you adopt Local Push Connectivity, you’re responsible for establishing and maintaining a reliable connection between your server and your client. To keep the connection viable, use the following best practices to maintain your client’s life cycle and connect over the local network.

### Implement the Push Provider App Extension Life Cycle

To implement Local Push Connectivity on a local network, create both a local server and an app that receives notifications from this server. Create an instance of NEAppPushManager when your client app starts up, and set its matchSSIDs property to a set of known Wi-Fi network SSIDs

To receive notifications from your server, create an app extension that extends NEAppPushProvider. When the user’s device joins one of the registered networks, the sytem automatically launches your push provider extension.

After your push provider extension launches, the system calls its start(completionHandler:) method. Use this callback to set up the connection to your server and call the completion handler, passing in an error if the connection failed. The following example attempts to get the host name from the push provider’s providerConfiguration, and calls a method to connect to the host.

```
override func start(completionHandler: @escaping (Error?) -> Void) {
    guard let host = providerConfiguration?["host"] as? String else {
        let error = MyPushProviderError("Provider configuration is missing value for key: `host`")
        completionHandler(error)
        return
    }

    myChannel.setHost(host)
    myChannel.connect()

    completionHandler(nil)
}
```

Ensure that the extension can launch when the system needs it and can continue running, because both are essential for your app extension to participate in local push connectivity. Use the following guidelines when writing your extension:

- Your extension must maintain a small memory footprint, or the system may terminate it. Use the Allocations and Leaks templates in Xcode Instruments to analyze your extension’s “dirty” memory usage and identify any memory leaks.

- Your extension continues to run as long as the device remains connected to the registered SSID. If the extension crashes, or if the system terminates it for using too much memory, iOS relaunches it.

- The user’s device can’t reconnect to a secure Wi-Fi network until the first unlock after it boots, because the device needs access to protected Wi-Fi credentials stored in the Keychain.

- When the device leaves the known Wi-Fi network, the system calls your push provider’s stop(with:completionHandler:) method. Implement this method to disconnect from the server and release any previously allocated resources.

- Confirm that your NEAppPushProvider implementation doesn’t create a retain cycle with itself. After you call the `completionHandler` that the system passes to stop(with:completionHandler:), the Network Extension framework releases your NEAppPushProvider instance. This instance typically deallocates from memory when released, but if the instance has a retain cycle with itself, it fails to deallocate and wastes memory. Failure to deallocate can also cause the system to have two or more instances of your push provider, leading to inconsistent behavior. Use Instruments or add a logging statement to `deinit` to verify that your NEAppPushProvider deinitializes when expected.

### Establish and Monitor the Network Connection

As shown in the previous section, your client extension creates its connection to your server in your implementation of the push provider’s start(completionHandler:) method. Use the Network framework to create and maintain this connection. The Network framework is an ideal choice to implement Local Push Connectivity, because it provides features like path monitors, TLS negotiation, and support for custom protocol framers.

Ensure each side of the connection monitors the health of the other side:

- Have your server periodically send heartbeat messages to the client. This ensures the push provider remains responsive, even when the user isn’t actively using the device. The push provider must acknowledge these messages, so the server can rapidly detect when the client disconnects unexpectedly.

- Your push provider must implement the handleTimerEvent() callback method, which the framework calls every 60 seconds. Implement this method to check the status of the connection on the client end.

The following example implements handleTimerEvent() by checking the last time the client received a heartbeat message from the server. If it exceeds the expected interval, it cancels the current connection and reconnects to the server.

```
override func handleTimerEvent() {
    dispatchQueue.async { [weak self] in
        guard let self = self, self.isRunning else {
            return
        }

        let expirationTime = self.lastCheckinTime.advanced(by: self.interval)

        if .now() >= expirationTime {
            self.logger.log("Heartbeat didn't check in within the interval of \(self.interval), calling network session disconnect.")
            self.session?.disconnect()
        }
    }
}
```

### Optimize the Network Architecture

If the Wi-Fi network is under your control, configure the network to better support your app’s client-server connection. Start by ensuring limited radio frequency congestion. Measure this by determining channel utilzation, which ideally is 40% or less. One symptom of congestion is a high number of frame retransmissions; which ideally is as low as possible, typically not more than 15% of all traffic.

Consider enabling roaming enhancements to reduce the network’s overall latency burden, if compatible with your network deployment. Roaming enhancements such as 802.11r Fast Transition Roaming, 802.11k Radio Resource Measurement, and 802.11v Wireless Network Management help devices roam more quickly after reaching their roam trigger threshold. For more information on these standards, see the support articles Wi-Fi network roaming with 802.11k, 802.11r, and 802.11v on iOS and About wireless roaming for enterprise.

If you deploy virtual LANs, ensure that clients on the LAN have a route to the server.

## See Also

### Essentials

class NEAppPushManager

An object that configures a push provider and manages its life cycle.

class NEAppPushProvider

An object that creates and maintains a persistent network connection to a local push server.

Receiving Voice and Text Communications on a Local Network

Provide voice and text communication on a local network isolated from Apple Push Notification service by adopting Local Push Connectivity.

