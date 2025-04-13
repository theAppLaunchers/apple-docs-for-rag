

- AppKit
- NSWritingToolsCoordinator
-  effectContainerView 

Instance Property

# effectContainerView

The view that Writing Tools uses to display visual effects during the text-rewriting process.

macOS 15.2+

``` source
@MainActor
weak var effectContainerView: NSView? { get set }
```

## Discussion

Writing Tools uses the view in this property to host the visual effects it creates when making interactive changes to your view’s content. These visual effects let people know the state of the text and provide feedback about what’s happening to it. Set this property to a subview that sits visually above, and covers, all of the text in your custom text view. If you don’t assign a value to this property, the coordinator places its own effect view in front of the subviews in your custom view. The default value of this property is `nil`.

If you display your view’s text using multiple text containers, implement the `NSWritingToolsCoordinator/Delegate/writingToolsCoordinator(_:singleContainerSubrangesOf:in:)` method to request multiple previews.

## See Also

### Getting the host views for effects

var decorationContainerView: NSView?

The view that Writing Tools uses to display background decorations such as proofreading marks.

