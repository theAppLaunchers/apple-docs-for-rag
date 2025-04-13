

- Group Activities
- GroupSession
-  requestForegroundPresentation() 

Instance Method

# requestForegroundPresentation()

Tells the system that your app needs to be in the foreground to continue an activity.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+

``` source
final func requestForegroundPresentation()
```

## Discussion

Call this method if your app is in the background and can’t start the activity without the participant’s assistance. For example, you might call the method if your app requires the participant’s credentials to play back a shared media file. Don’t call this method if you’re able to start the activity without assistance. When you call this method, the system asks the participant to continue the activity in your app.

To create a smoother user experience, the system might launch your app in the background when starting an activity. Apps can start activities in either the foreground or background, but you might configure your app differently when in the background. For example, when in the background, you play media files in a picture-in-picture window instead of a fullscreen interface. This method lets you notify the user when a background solution isn’t possible.

The session must be in the GroupSession.State.waiting or GroupSession.State.joined state when you call this method. If it isn’t, this method does nothing.

