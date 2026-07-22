- NowPlaying  
- MediaSession  
  
Class  
  
# MediaSession  
  
A local Now Playing session that publishes metadata and commands to the system.  
  
iOS 27.0+ iPadOS 27.0+ Mac Catalyst 27.0+ macOS 27.0+ tvOS 27.0+ visionOS 27.0+ watchOS 27.0+  
  
``` swift  
@MainActor  
class MediaSession<Representable> where Representable : MediaSessionRepresentable  
```  
  
## Mentioned in  
  
Publishing media sessions  
  
## Overview  
  
Use a session to represent media playback happening on the current device. The session automatically observes your MediaSessionRepresentable model and syncs changes to the system’s Now Playing interface.  
  
For more information, see Publishing media sessions  
  
Create a session by providing a session representable:  
  
``` swift  
let session = MediaSession(myModel)  
```  
  
Call requestToBecomeApplicationPrimary() to make this your app’s primary Now Playing session when you want to display playback controls:  
  
``` swift  
try await session.requestToBecomeApplicationPrimary()  
```  
  
## Topics  
  
### Initializers  
  
init(Representable)  
  
Creates a new local Now Playing session.  
  
### Instance Properties  
  
var canBecomeApplicationPrimary: Bool  
  
A Boolean value that indicates whether this session can become the app’s primary session.  
  
let id: String  
  
The unique identifier for this session.  
  
var isApplicationPrimary: Bool  
  
A Boolean value that indicates whether this is currently the primary application session.  
  
var isSystemPrimary: Bool  
  
A Boolean value that indicates whether this is currently the primary system session.  
  
### Instance Methods  
  
func requestToBecomeApplicationPrimary() async throws  
  
Attempts to make this session your app’s primary media session.  
  
func requestToBecomeSystemPrimary() async throws  
  
Requests to make this session the primary system media session.  
  
## Relationships  
  
### Conforms To  
  
Copyable  
Escapable  
Identifiable  
Observable  
Sendable  
SendableMetatype  
  
## See Also  
  
### Local sessions  
  
Publishing media sessions  
  
Show your app’s media on the Lock Screen and Control Center.  
  
protocol MediaSessionRepresentable  
  
A protocol that provides content metadata, playback state, and commands for a Now Playing session.  
  
enum MediaSessionError  
  
Errors that can occur during local session operations.  
