

- UIKit
- UIDevice
-  playInputClick() 

Instance Method

# playInputClick()

Plays an input click in an enabled input view.

iOS 4.2+iPadOS 4.2+Mac Catalyst 13.1+tvOS

``` source
@MainActor
func playInputClick()
```

## Discussion

Use this method to play the standard system keyboard click in response to a user tapping in a custom input or keyboard accessory view. A click plays only if the user has enabled keyboard clicks in Settings \> Sounds, and only if the input view is itself enabled and visible.

To enable a custom input or accessory view for input clicks, perform the following two steps:

1.  Adopt the UIInputViewAudioFeedback protocol in your input view class.

2.  Implement the enableInputClicksWhenVisible delegate method to return true.

For more information, see Text Programming Guide for iOS.

