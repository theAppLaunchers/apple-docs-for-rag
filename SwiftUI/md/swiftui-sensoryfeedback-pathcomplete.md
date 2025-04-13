

- SwiftUI
- SensoryFeedback
-  pathComplete 

Type Property

# pathComplete

Indicates a drawn path has completed and/or recognized.

iOS 17.5+iPadOS 17.5+Mac Catalyst 17.5+macOS 14.5+tvOS 17.5+watchOS 10.5+

``` source
static let pathComplete: SensoryFeedback
```

## Discussion

Use this to provide feedback for closed shape drawing or similar actions. It should supplement the user experience, since only some platforms will play feedback in response to it.

Only plays feedback on iOS.

## See Also

### Indicating changes and selections

static let alignment: SensoryFeedback

Indicates the alignment of a dragged item.

static let decrease: SensoryFeedback

Indicates that an important value decreased below a significant threshold.

static let increase: SensoryFeedback

Indicates that an important value increased above a significant threshold.

static let levelChange: SensoryFeedback

Indicates movement between discrete levels of pressure.

static let selection: SensoryFeedback

Indicates that a UI element’s values are changing.

