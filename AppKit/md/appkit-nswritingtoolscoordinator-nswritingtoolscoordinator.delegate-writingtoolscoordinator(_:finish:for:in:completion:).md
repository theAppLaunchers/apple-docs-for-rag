

- AppKit
- NSWritingToolsCoordinator
- NSWritingToolsCoordinator.Delegate
-  writingToolsCoordinator(\_:finish:for:in:completion:) 

Instance Method

# writingToolsCoordinator(\_:finish:for:in:completion:)

Asks the delegate to clean up any state related to the specified Writing Tools animation.

macOS 15.2+

``` source
func writingToolsCoordinator(
    _ writingToolsCoordinator: NSWritingToolsCoordinator,
    finish textAnimation: NSWritingToolsCoordinator.TextAnimation,
    for range: NSRange,
    in context: NSWritingToolsCoordinator.Context,
    completion: @escaping () -> Void
)
```

``` source
func writingToolsCoordinator(
    _ writingToolsCoordinator: NSWritingToolsCoordinator,
    finish textAnimation: NSWritingToolsCoordinator.TextAnimation,
    for range: NSRange,
    in context: NSWritingToolsCoordinator.Context
) async
```

**Required**

## Parameters 

`writingToolsCoordinator`  

The coordinator object notifying you that animations are about to begin.

`textAnimation`  

The type of animation Writing Tools finished.

`range`  

The range of text that finished animating. This range is relative to the text in your context object, and it’s your responsibility to match that location to the correct location in your text storage. If you initialized the context object with the entire contents of your view’s text storage, you can use `range` as-is to access that text storage. However, if you initialized the context object with only a portion of your view’s text, add the starting location of your context object’s text to this value to get the correct range for that text storage.

`context`  

The context object that contains the original text.

`completion`  

A completion handler to execute when you are done. The handler has no return value and takes no parameters. You must call this handler at some point during your implementation.

## Mentioned in 

Adding Writing Tools support to a custom AppKit view

## Discussion

Use this method to clean up any data structures you created to support the specified type of Writing Tools animation. You can also use this method to restore the visibility of any text you hid previously. When you finish your cleanup work, call the completion handler to notify Writing Tools.

Writing Tools calls this method only after previous calls to the `writingToolsCoordinator(_:prepareFor:range:context:completion:)` and `writingToolsCoordinator(_:previewFor:range:context:completion:)` methods for the same animation type. However, Writing Tools can interleave calls to this method with calls to prepare an animation of a different type. In your implementation of this method, make sure the actions you take don’t interfere with other in-flight animations.

## See Also

### Animating inline text changes

func writingToolsCoordinator(NSWritingToolsCoordinator, requestsPreviewFor: NSWritingToolsCoordinator.TextAnimation, of: NSRange, in: NSWritingToolsCoordinator.Context, completion: ([NSTextPreview]?) -> Void)

Asks the delegate for a preview image and layout information for the specified text.

**Required**

func writingToolsCoordinator(NSWritingToolsCoordinator, requestsPreviewFor: NSRect, in: NSWritingToolsCoordinator.Context, completion: (NSTextPreview?) -> Void)

Asks the delegate for a preview image and layout information for the specified text.

**Required**

func writingToolsCoordinator(NSWritingToolsCoordinator, prepareFor: NSWritingToolsCoordinator.TextAnimation, for: NSRange, in: NSWritingToolsCoordinator.Context, completion: () -> Void)

Prepare for animations for the content that Writing Tools is evaluating.

**Required**

