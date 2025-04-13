

- SwiftUI
- AnimationCompletionCriteria
-  logicallyComplete 

Type Property

# logicallyComplete

The animation has logically completed, but may still be in its long tail.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+watchOS 10.0+

``` source
static let logicallyComplete: AnimationCompletionCriteria
```

## Discussion

If a subsequent change occurs that creates additional animations on properties with `logicallyComplete` completion callbacks registered, then those callbacks will fire when the animations from the change that they were registered with logically complete, ignoring the new animations.

## See Also

### Getting the completion criteria

static let removed: AnimationCompletionCriteria

The entire animation is finished and will now be removed.

