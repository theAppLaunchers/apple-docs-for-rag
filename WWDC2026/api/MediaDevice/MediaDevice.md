# MediaDevice  
  
- MediaDevice  
-  Media Device  
  
Framework  
  
# Media Device  
  
Let people stream media from any iOS app to your playback hardware through the media device picker.  
  
iOS 27.0+ iPadOS 27.0+ Mac Catalyst 27.0+  
  
## Overview  
  
Media Device lets you make your playback hardware available to the system. People can then stream to it from any iOS app, selecting your device from the media device picker. The picker is the same UI people use for AirPlay and Bluetooth output. You build a MediaDeviceExtension that the system loads when someone opens the picker, and your extension handles discovery, connection, and playback on behalf of the system.  
  
Note  
  
Your extension and the container app require the com.apple.developer.media-device-extension entitlement.  
  
The extension life cycle follows three phases: discovery, activation, and playback. During discovery, your extension reports available devices to the system through MediaDeviceRoutingManager. Your devices appear in the media device picker that media apps present to people. When someone selects one of your devices, the system creates a MediaOutputSession and asks your extension to connect. After your extension connects and calls activatedDevice(_:session:), the system notifies supporting media apps about the selected device, and they can call playback APIs such as startSession(_:identifier:url:).  
  
Your extension may also register to receive real-time audio and video samples by conforming to RealtimeSampleHandling. To capture those samples, follow Creating an Audio Server Driver Plug-in for audio, and use ScreenCaptureKit for video.  
  
Media Device works with AVSystemRouting, which provides the API for media apps. Media apps use AVSystemRouteController to observe route changes, and AVSystemRoute to control playback while your extension handles the protocol-specific communication with the hardware.  
  
## Topics  
  
### Essentials  
  
Creating a media device extension  
  
Provide a way for people to find, connect to, and control your media device by adding a device extension in your iOS app.  
  
Routing media to third-party devices  
  
Respond to routing events and control playback on a TV, speaker, or other media device.  
  
protocol MediaDeviceExtension  
  
A protocol that defines the requirements of a media device extension that discovers, activates, and plays media on a remote device.  
  
protocol MediaDeviceExtensionConfiguration  
  
Configuration for the app extension.  
  
### Device discovery and management  
  
struct MediaOutputDevice  
  
Represents a discoverable media output device such as a TV, speaker, or streaming stick.  
  
struct Capabilities  
  
Defines the media capabilities supported by a MediaOutputDevice.  
  
enum DeviceType  
  
A device type used for display in user interfaces.  
  
enum VolumeControl  
  
Defines the type of volume control supported by an output device or group.  
  
struct AuthorizationMethod  
  
Specifies what kind of authorization UI to present when connecting to a device.  
  
### Session and system communication  
  
class MediaOutputSession  
  
Represents a media output session for playing content on a remote device.  
  
class MediaDeviceRoutingManager  
  
An object used by a MediaDeviceExtension to report device discovery, state changes, and playback events back to the system.  
  
protocol RealtimeSampleHandling  
  
A protocol that extends a media device extension to support realtime sample delivery.  
  
struct MediaDeviceError  
  
An error returned by MediaDeviceExtension operations.  
