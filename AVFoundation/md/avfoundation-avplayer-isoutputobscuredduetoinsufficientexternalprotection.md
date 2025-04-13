

- AVFoundation
- AVPlayer
-  isOutputObscuredDueToInsufficientExternalProtection 

Instance Property

# isOutputObscuredDueToInsufficientExternalProtection

A Boolean value that indicates whether output is being obscured because of insufficient external protection.

iOS 6.0+iPadOS 6.0+Mac Catalyst 13.1+macOS 10.12+tvOS 9.0+visionOS 1.0+

``` source
nonisolated
var isOutputObscuredDueToInsufficientExternalProtection: Bool { get }
```

## Discussion

Items that incorporate copy protection or other forms of security might have their visual content obscured by the player object if the current device configuration does not meet the requirements for protecting the item. This property reports whether the player is currently obscuring the item. If the current item does not require external protection or if the device configuration sufficiently protects the item, the value of this property is set to false.

You can use this property to determine whether to change your app’s user interface to reflect the change in visibility. You can observe changes to the value of this property using key-value observing.

