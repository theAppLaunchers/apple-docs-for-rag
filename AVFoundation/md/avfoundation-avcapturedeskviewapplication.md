

- AVFoundation
-  AVCaptureDeskViewApplication 

Class

# AVCaptureDeskViewApplication

An object that programmatically presents Desk View.

Mac Catalyst 16.1+macOS 13.0+

``` source
class AVCaptureDeskViewApplication
```

## Overview

Use this class to programmatically launch Desk View from your app. You can optionally customize the presentation and specifiy an action to take afterward.

Note

Desk View is available in iOS 16 and later on iPhone 11 and later, excluding iPhone SE, for use with a Mac running macOS 13 and later.

The following example shows how to configure and present Desk View with a completion handler:

```
let deskView = AVCaptureDeskViewApplication()
let configuration = AVCaptureDeskViewApplication.LaunchConfiguration()

// Use the previously set frame.
configuration.mainWindowFrame = .zero

// Execute the completion handler when the user starts Desk View.
configuration.requiresSetUpModeCompletion = true

// Launch Desk View with a configuration and completion handler.
deskView.present(launchConfiguration: configuration) { error in
    // Perform error handling and additional tasks.
}
```

## Topics

### Presenting the Desk View app

func present(completionHandler: (((any Error)?) -> Void)?)

Launches Desk View with no additional configuration and then performs a completion handler if you specify it.

func present(launchConfiguration: AVCaptureDeskViewApplication.LaunchConfiguration, completionHandler: (((any Error)?) -> Void)?)

Launches Desk View with the configuration and completion handler that you specify.

class LaunchConfiguration

An object that configures how to present Desk View.

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

### Continuity camera

Supporting Continuity Camera in your tvOS app

Capture high-quality photos, video, and audio in your Apple TV app by connecting an iPhone or iPad as a continuity device.

Supporting Continuity Camera in your macOS app

Enable high-quality photo and video capture by using an iPhone camera as an external capture device.

