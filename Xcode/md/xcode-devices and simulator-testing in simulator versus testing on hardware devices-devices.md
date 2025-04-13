

- Xcode
- Devices and Simulator
-  Testing in Simulator versus testing on hardware devices 

Article

# Testing in Simulator versus testing on hardware devices

Review the differences between Simulator and hardware devices to determine which you should choose to test a scenario.

## Overview

While Simulator is useful for many types of tests, there are significant differences between Simulator and actual hardware devices that you need to consider when you choose which platform to use. These differences fall into several categories:

- General: there are differences in processing, graphics, and network speed.

- Display: there are differences in resolution and color.

- System: there are differences in how the system handles backgrounding your app.

- Hardware: Simulator doesn’t support some hardware features.

- API: Simulator doesn’t support some APIs.

- Metal: there are differences between the device GPU and your computer GPU.

Evaluate the differences to help you determine what features and functionality you can test in Simulator in addition to the testing you perform on hardware devices.

### Evaluate general differences

Use hardware devices to do performance testing for processing, graphics, and networking to ensure accurate results.

Simulator is an app running on a Mac using the computer’s resources including the CPU, memory, and network connection. As a result, Simulator is not an accurate test of an app’s performance, memory usage, and networking speed. Use performance testing results in Simulator to determine relative differences in app functionality. If you encounter performance issues in Simulator but not on a hardware device, see Troubleshooting Simulator launch or animation issues.

Perform user testing on hardware devices when you require real-world results, such as confirming that tap areas are large enough for users to tap, or text in your user interface is legible.

User interaction with a pointer and keyboard is different from using fingers on iOS and watchOS, hand gestures on visionOS, or the focus-based model used on tvOS. After you are satisfied that your app functions correctly in Simulator, test on devices to catch any unexpected issues with user interaction.

### Evaluate display differences

The resolution, or pixels per point, on the hardware device and on the Mac can differ. This results in text and images that appear jagged, especially with smaller text.

Increasing the scale of the Simulator window can make text and images appear clearer.

The color gamut of the Mac screen can differ resulting in inaccurate colors in Simulator.

### Evaluate system differences

Simulator suspends background apps and processes on iOS 11 and later, tvOS 11 and later, and watchOS 4 and later. The debugger can resume a suspended process.

Simulator treats the file system as case-sensitive on HFS+ and APFS formatted volumes.

### Evaluate hardware differences

There is a reliable connection between simulated watchOS and iOS devices because they are both running in the Simulator.

Simulator doesn’t support the following hardware:

- Ambient light sensor

- Audio input, except for using Siri by choosing Device \> Siri

- Barometer

- Bluetooth

- Camera

- Motion support (accelerometer and gyroscope)

- Proximity sensor

### Evaluate API differences

Simulator doesn’t support the following frameworks:

- ARKit

- External Accessory

- HomeKit

- IOSurface

- Media Player

- Message UI

The following features of APIs are not available in Simulator:

- Receiving and sending Apple push notifications. Drag and drop a JSON file with a push notification payload on the simulator to test receiving a push notification.

- The UIBackgroundModes key.

- The UIVideoEditorController class in UIKit.

- Support for Handoff.

### Evaluate Metal differences

Simulator includes a Metal implementation that you can use to start developing your app. For more information on how it differs from a hardware processor, see Developing Metal apps that run in Simulator.

## See Also

### Simulator testing considerations

Sharing data with Simulator

Enter text directly in Simulator, or share location data, images, web addresses, files, or data from the clipboard with Simulator.

Testing complex hardware device scenarios in Simulator

Test hardware device-specific scenarios, such as Face ID or Touch ID authentication, fall detection, getting a memory warning, or location changes.

Identifying graphics and animations issues in Simulator

Reveal performance and display issues in your views with color overlays, and slow down animations to debug and improve them.

