- AVSystemRouting  
- AVSystemRouting  
  
Framework  
  
# AVSystemRouting  
  
Send media from your app to a TV, speaker, or other device through a media device extension.  
  
iOS 27.0+ iPadOS 27.0+ Mac Catalyst 27.0+  
  
## Overview  
  
The AVSystemRouting framework lets your app send media to other devices, like TVs and speakers. Media sharing protocol providers distribute media device extensions through their own apps so you don’t need to bundle each device’s SDK in your app.  
When someone selects a device, your app receives an event describing their choice and starts a playback session on that device.  
  
Your app uses the shared AVSystemRouteController and registers an AVSystemRouteControllerObserver to receive routing events. When your app receives an AVSystemRouteEvent with an AVSystemRouteEvent.Reason.activate reason, create an AVSystemRouteSession with a URL and an AVSystemRoute.LaunchMode the device supports. The launch mode either plays the URL on the receiver or launches your app’s counterpart there. Add the session to the event’s AVSystemRoute, then start it; on success, you receive an AVSystemRouteMediaSession for managing playback.  
  
Declare your supported protocols in your app’s Info pane in Xcode using the MDESupportedProtocols key, and add MDESupportsUniversalURLPlayback as needed for URL-based playback.  
  
After starting a session, use the AVSystemRouteMediaSession class’s playback control to manage remote playback and receive state updates. For communication that includes a companion app on the remote device, use the media session’s data channel and implement AVSystemRouteDataDelegate.  
  
AVSystemRouting is the app-side counterpart to the Media Device framework, which provides the extension API that media sharing protocol providers implement. To learn how extension providers register their protocols and handle playback, see Creating a media device extension. The two frameworks communicate through the system, so your app never needs to interact with protocol-specific details directly.  
  
## Topics  
  
### Essentials  
  
Routing media to third-party devices  
  
Respond to routing events and control playback on a TV, speaker, or other media device.  
  
Routing and streaming media to remote devices  
  
Send media from an app to nearby remote playback devices.  
  
class AVSystemRouteController  
  
An object that manages interaction with system routes.  
  
protocol AVSystemRouteControllerObserver  
  
A protocol for observers of a system routing controller.  
  
### Routing events  
  
class AVSystemRouteEvent  
  
An object that represents an event that occurs on a system route.  
  
enum Reason  
  
Values that indicate the reason for a routing event.  
  
### Routes and sessions  
  
class AVSystemRoute  
  
An active media route to a remote device that manages connection and communication for media playback and data exchange.  
  
class AVSystemRouteSession  
  
An object that manages a single media playback session on a remote device.  
  
enum LaunchMode  
  
The mode that determines how media playback launches on a remote device.  
  
### Playback and communication  
  
class AVSystemRouteMediaSession  
  
An object that provides playback controls and a data channel for a session running on a remote device.  
  
class DataChannel  
  
An object that manages bidirectional data communication with a remote application.  
  
protocol AVSystemRouteDataDelegate  
  
A protocol for handling data from a remote application.  
  
### Errors  
  
struct AVSystemRoutingError  
  
An error that an AVSystemRouting operation throws when it fails.  
  
struct AVSystemRoutingError  
