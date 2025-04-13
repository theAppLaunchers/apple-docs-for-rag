

- AppKit
- NSApplication
- NSApplication.ActivationOptions
-  activateIgnoringOtherApps Deprecated

Type Property

# activateIgnoringOtherApps

The application is activated regardless of the currently active app.

macOS 10.6–14.0Deprecated

``` source
static var activateIgnoringOtherApps: NSApplication.ActivationOptions { get }
```

Deprecated

Use NSApplication method activate() instead.

## Discussion

By default, activation deactivates the calling app (assuming it was active), and then the new app is activated only if there’s no currently active application. This prevents the new app from stealing focus from the user, if the app is slow to activate and the user has switched to a different app in the interim. However, if you specify activateIgnoringOtherApps, the application is activated regardless of the currently active app, potentially stealing focus from the user.

Important

You should **rarely pass this flag** because stealing key focus produces a poor user experience.

