

- Foundation
- URLSessionConfiguration
-  sessionSendsLaunchEvents 

Instance Property

# sessionSendsLaunchEvents

A Boolean value that indicates whether the app should be resumed or launched in the background when transfers finish.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+macOS 11.0+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
var sessionSendsLaunchEvents: Bool { get set }
```

## Mentioned in 

Downloading files in the background

## Discussion

For configuration objects created using the background(withIdentifier:) method, you can use this property to control the launching behavior for an iOS app. This property is ignored for configuration objects created using other methods.

The default value of this property is true. When the value of this property is true, the system automatically wakes up or launches the iOS app in the background when the session’s tasks finish or require authentication. At that time, the system calls the app delegate’s application(_:handleEventsForBackgroundURLSession:completionHandler:) method, providing it with the identifier of the session that needs attention. If your app had to be relaunched, you can use that identifier to create a new configuration and session object capable of servicing the tasks.

## See Also

### Supporting background transfers

var isDiscretionary: Bool

A Boolean value that determines whether background tasks can be scheduled at the discretion of the system for optimal performance.

var shouldUseExtendedBackgroundIdleMode: Bool

A Boolean value that indicates whether TCP connections should be kept open when the app moves to the background.

Deprecated

