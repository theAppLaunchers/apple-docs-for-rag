

- AppKit
- NSWritingToolsCoordinator
- NSWritingToolsCoordinator.Delegate
-  writingToolsCoordinator(\_:requestsUnderlinePathsFor:in:completion:) 

Instance Method

# writingToolsCoordinator(\_:requestsUnderlinePathsFor:in:completion:)

Asks the delegate to provide an underline shape for the specified text during a proofreading session.

macOS 15.2+

``` source
func writingToolsCoordinator(
    _ writingToolsCoordinator: NSWritingToolsCoordinator,
    requestsUnderlinePathsFor range: NSRange,
    in context: NSWritingToolsCoordinator.Context,
    completion: @escaping ([NSBezierPath]) -> Void
)
```

``` source
func writingToolsCoordinator(
    _ writingToolsCoordinator: NSWritingToolsCoordinator,
    underlinePathsFor range: NSRange,
    context: NSWritingToolsCoordinator.Context
) async -> [NSBezierPath]
```

**Required**

## Parameters 

`writingToolsCoordinator`  

The coordinator object requesting information from your custom view.

`range`  

The range of text to evaluate. This range is relative to the text in your context object, and it’s your responsibility to match that location to the correct location in your text storage. If you initialized the context object with the entire contents of your view’s text storage, you can use `range` as-is to access that text storage. However, if you initialized the context object with only a portion of your view’s text, add the starting location of your context object’s text to this value to get the correct range for that text storage.

`context`  

The context object with the target text. Use this object to find the text in your view’s text storage.

`completion`  

A handler to execute with the required information. The handler has no return value and takes an array of Bezier paths as a parameter. You must call this handler at some point during your method’s implementation.

## Discussion

When applying proofreading marks to your view’s content, the coordinator calls this method to retrieve a shape to draw under the specified text. You provide the shape using one or more Bezier paths, and the coordinator draws and animates that shape during the proofreading session.

After you determine the location of the specified range of text in your view’s text storage, find the rectangle around that text. If you’re using TextKit, you can call the enumerateTextSegments(in:type:options:using:) method of your view’s NSTextLayoutManager to get the rectangles for a range of text. Convert the coordinates of each rectangle to the coordinate space of the view in your coordinator’s decorationContainerView property. Use those rectangles to create the Bezier paths for your text. For example, you might create a path with a straight or wavy line at the bottom of the rectangle.

## See Also

### Displaying proofreading marks

func writingToolsCoordinator(NSWritingToolsCoordinator, requestsRangeInContextWithIdentifierFor: NSPoint, completion: (NSRange, UUID) -> Void)

Asks the delegate to provide the location of the character at the specified point in your view’s coordinate system.

Deprecated

func writingToolsCoordinator(NSWritingToolsCoordinator, requestsBoundingBezierPathsFor: NSRange, in: NSWritingToolsCoordinator.Context, completion: ([NSBezierPath]) -> Void)

Asks the delegate to provide the bounding paths for the specified text in your view.

**Required**

