Collection

*   [DriverKit](/documentation/driverkit)
*   DriverKit sample code

# DriverKit sample code

Explore projects that demonstrate how to write macOS device drivers with the DriverKit family of frameworks.

## [Overview](/documentation/DriverKit/driverkit-sample-code#overview)

The DriverKit SDK provide a stable, secure platform on which to build device drivers for macOS and iPadOS. It provides the interfaces you need to support many types of hardware, including USB devices, HID devices, networking devices, audio devices, and more. Package your custom code in a DriverKit extension, which runs in user space and communicates with the kernel through the framework APIs. To install your DriverKit extension on macOS, deliver it inside an app and install it using the [System Extensions](/documentation/SystemExtensions) framework. For projects that run on iPadOS, the system locates the driver in your app bundle and installs the driver for you.

The DriverKit SDK includes several practical examples that show you how to write a typical driver. Use these samples as a starting point to write your own custom drivers. The SDK’s classes provide the base code you need to support standard hardware protocols such as USB, HID, Ethernet, PCI, Thunderbolt, and more. Use your custom driver code to support proprietary features of your hardware devices.

## [Topics](/documentation/DriverKit/driverkit-sample-code#topics)

### [Essentials](/documentation/DriverKit/driverkit-sample-code#Essentials)

[

Communicating between a DriverKit extension and a client app](/documentation/driverkit/communicating-between-a-driverkit-extension-and-a-client-app)

Send and receive different kinds of data securely by validating inputs and asynchronously by storing and using a callback.

### [Audio samples](/documentation/DriverKit/driverkit-sample-code#Audio-samples)

[

Creating an audio device driver](/documentation/AudioDriverKit/creating-an-audio-device-driver)

Implement a configurable audio input source as a driver extension that runs in user space in macOS and iPadOS.

### [HID samples](/documentation/DriverKit/driverkit-sample-code#HID-samples)

[

Handling Stylus Input from a Human Interface Device](/documentation/HIDDriverKit/handling-stylus-input-from-a-human-interface-device)

Process stylus-related input from a human interface device and dispatch events to the system.

[

Handling Keyboard Events from a Human Interface Device](/documentation/HIDDriverKit/handling-keyboard-events-from-a-human-interface-device)

Process keyboard-related data from a human interface device and dispatch events to the system.

### [Networking samples](/documentation/DriverKit/driverkit-sample-code#Networking-samples)

[

Connecting a network driver](/documentation/pcidriverkit/connecting_a_network_driver)

Create an Ethernet driver that interfaces with the system’s network protocol stack.