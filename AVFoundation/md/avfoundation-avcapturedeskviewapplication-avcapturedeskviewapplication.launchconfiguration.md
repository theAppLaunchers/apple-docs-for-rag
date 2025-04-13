

- AVFoundation
- AVCaptureDeskViewApplication
-  AVCaptureDeskViewApplication.LaunchConfiguration 

Class

# AVCaptureDeskViewApplication.LaunchConfiguration

An object that configures how to present Desk View.

Mac Catalyst 16.1+macOS 13.0+

``` source
class LaunchConfiguration
```

## Overview

Use this object to specify the frame for Desk View when it launches, and when to execute the completion handler. You can specify whether to perform the completion handler as soon as Desk View is visible to the user, or only after they start Desk View.

## Topics

### Customizing the presentation

var mainWindowFrame: CGRect

The frame for Desk View after it launches.

var requiresSetUpModeCompletion: Bool

A Boolean value that specifies whether the system requires the user to complete setup mode before it executes the completion handler.

## Relationships

### Inherits From

- NSObject

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSObjectProtocol

## See Also

### Presenting the Desk View app

func present(completionHandler: (((any Error)?) -> Void)?)

Launches Desk View with no additional configuration and then performs a completion handler if you specify it.

func present(launchConfiguration: AVCaptureDeskViewApplication.LaunchConfiguration, completionHandler: (((any Error)?) -> Void)?)

Launches Desk View with the configuration and completion handler that you specify.

