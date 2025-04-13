

- UIKit
- NSTextLayoutManager
-  textViewportLayoutController 

Instance Property

# textViewportLayoutController

Returns text viewport layout controller associated with the layout manager’s text container.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+tvOS 15.0+visionOS 1.0+

``` source
var textViewportLayoutController: NSTextViewportLayoutController { get }
```

## See Also

### Causing layout generation

func invalidateLayout(for: NSTextRange)

Invalidates the layout information for specified text range.

func textLayoutFragment(for: any NSTextLocation) -> NSTextLayoutFragment?

Returns the text layout fragment from the document at the specified location.

func textLayoutFragment(for: CGPoint) -> NSTextLayoutFragment?

Returns the text layout fragment at the position you specify in the text container.

func ensureLayout(for: CGRect)

Performs the layout for filling the bounds you specify inside the last text container.

func ensureLayout(for: NSTextRange)

Performs the layout for specified text range.

func enumerateTextLayoutFragments(from: (any NSTextLocation)?, options: NSTextLayoutFragment.EnumerationOptions, using: (NSTextLayoutFragment) -> Bool) -> (any NSTextLocation)?

Enumerates the text layout fragments starting at the specified location.

enum SegmentType

Values that describe the rendering of selection boundaries.

struct SegmentOptions

Values that describe where and how the framework extends segments of a selection.

