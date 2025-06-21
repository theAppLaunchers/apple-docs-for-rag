*   [Updates](/documentation/updates)
*   XPC updates

Article

# XPC updates

Learn about important changes to XPC.

## [Overview](/documentation/Updates/XPC#Overview)

Browse notable changes in [XPC](https://developer.apple.com/documentation/xpc).

## [March 2024](/documentation/Updates/XPC#March-2024)

### [Security](/documentation/Updates/XPC#Security)

*   Test whether the peer executable that communicates with your app over an XPC connection has an expected entitlement by calling [`xpc_connection_set_peer_entitlement_exists_requirement(_:_:)`](/documentation/XPC/xpc_connection_set_peer_entitlement_exists_requirement\(_:_:\)), and whether it has a specific value for an entitlement by calling [`xpc_connection_set_peer_entitlement_matches_value_requirement(_:_:_:)`](/documentation/XPC/xpc_connection_set_peer_entitlement_matches_value_requirement\(_:_:_:\)).
    
*   Test whether the peer executable that communicates with your app over an XPC connection is an Apple platform binary with a given signing identifier by calling [`xpc_connection_set_peer_platform_identity_requirement(_:_:)`](/documentation/XPC/xpc_connection_set_peer_platform_identity_requirement\(_:_:\)).
    
*   Test whether your Apple Developer team signed the peer executable that communicates with your app over an XPC connection by calling [`xpc_connection_set_peer_team_identity_requirement(_:_:)`](/documentation/XPC/xpc_connection_set_peer_team_identity_requirement\(_:_:\)).
    
*   Test whether the peer executable that communicates with your app over an XPC connection satisfies a lightweight code requirement by calling [`xpc_connection_set_peer_lightweight_code_requirement(_:_:)`](/documentation/XPC/xpc_connection_set_peer_lightweight_code_requirement\(_:_:\)).
    

## [June 2023](/documentation/Updates/XPC#June-2023)

*   Create XPC services using native Swift syntax. Use [`XPCListener`](/documentation/XPC/XPCListener) to create an XPC server that listens for messages from other processes. Use [`XPCSession`](/documentation/XPC/XPCSession) to create clients that connect to servers and exchange messages.
    
*   For C and Objective-C projects, use the corresponding [`xpc_listener_t`](/documentation/XPC/xpc_listener_t) and [`xpc_session_t`](/documentation/XPC/xpc_session_t-10if0) APIs.
    
*   In Xcode, use the updated XPC services target template to choose whether you want to use the high-level [`NSXPCConnection`](/documentation/Foundation/NSXPCConnection) or the low-level `libXPC` APIs.
    

## [See Also](/documentation/Updates/XPC#see-also)

### [Technology updates](/documentation/Updates/XPC#Technology-updates)

[

Accelerate updates](/documentation/updates/accelerate)

Learn about important changes to Accelerate.

[

Accessibility updates](/documentation/updates/accessibility)

Learn about important changes to Accessibility.

[

ActivityKit updates](/documentation/updates/activitykit)

Learn about important changes in ActivityKit.

[

AdAttributionKit Updates](/documentation/updates/adattributionkit)

Learn about important changes to AdAttributionKit.

[

App Clips updates](/documentation/updates/appclips)

Learn about important changes in App Clips.

[

App Intents updates](/documentation/updates/appintents)

Learn about important changes in App Intents.

[

AppKit updates](/documentation/updates/appkit)

Learn about important changes to AppKit.

[

Apple Intelligence updates](/documentation/updates/apple-intelligence)

Learn about important changes to Apple Intelligence.

[

AppleMapsServerAPI Updates](/documentation/updates/applemapsserverapi)

Learn about important changes to AppleMapsServerAPI.

[

Apple Pencil updates](/documentation/updates/applepencil)

Learn about important changes to Apple Pencil.

[

ARKit updates](/documentation/updates/arkit)

Learn about important changes to ARKit.

[

Audio Toolbox updates](/documentation/updates/audiotoolbox)

Learn about important changes to Audio Toolbox.

[

AuthenticationServices updates](/documentation/updates/authenticationservices)

Learn about important changes to AuthenticationServices.

[

AVFAudio updates](/documentation/updates/avfaudio)

Learn about important changes to AVFAudio.

[

AVFoundation updates](/documentation/updates/avfoundation)

Learn about important changes to AVFoundation.