

- AVFoundation
- AVCaptureDeskViewApplication
-  present(completionHandler:) 

Instance Method

# present(completionHandler:)

Launches Desk View with no additional configuration and then performs a completion handler if you specify it.

Mac Catalyst 16.1+macOS 13.0+

``` source
func present(completionHandler: (((any Error)?) -> Void)? = nil)
```

``` source
func present() async throws
```

## Parameters 

`completionHandler`  

The code to perform after the system displays Desk View.

## Discussion

If the Desk View app is already running, this method brings it to the front. If Desk View is in the Dock, this method opens it and brings it to the front.

Desk View launches in setup mode. This mode shows the full field of view of an ultrawide camera with a superimposed trapezoid that indicates the cropped desk region to display. The system displays this region after the user completes setup and starts Desk View.

## See Also

### Presenting the Desk View app

func present(launchConfiguration: AVCaptureDeskViewApplication.LaunchConfiguration, completionHandler: (((any Error)?) -> Void)?)

Launches Desk View with the configuration and completion handler that you specify.

class LaunchConfiguration

An object that configures how to present Desk View.

