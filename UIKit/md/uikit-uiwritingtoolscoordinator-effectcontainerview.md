

- UIKit
- UIWritingToolsCoordinator
-  effectContainerView 

Instance Property

# effectContainerView

The view that Writing Tools uses to display visual effects during the text-rewriting process.

iOS 18.2+iPadOS 18.2+Mac Catalyst 18.2+visionOS 2.4+

``` source
@MainActor
weak var effectContainerView: UIView? { get set }
```

## Discussion

Writing Tools uses the view in this property to host the visual effects it creates when making interactive changes to your view’s content. These visual effects let people know the state of the text and provide feedback about what’s happening to it. Set this property to a subview that sits visually above, and covers, all of the text in your custom text view. If you don’t assign a value to this property, the coordinator uses the object in its view property to host any visual effects.

If you display your view’s text using multiple text containers, implement the writingToolsCoordinator(_:requestsSingleContainerSubrangesOf:in:completion:) method to request multiple previews.

## See Also

### Getting the host views for effects

var decorationContainerView: UIView?

The view that Writing Tools uses to display background decorations such as proofreading marks.

