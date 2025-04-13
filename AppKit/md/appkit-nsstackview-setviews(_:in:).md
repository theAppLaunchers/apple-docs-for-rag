

- AppKit
- NSStackView
-  setViews(\_:in:) 

Instance Method

# setViews(\_:in:)

Specifies an array of views for a specified gravity area in the stack view, replacing any previous views in that area.

macOS

``` source
@MainActor
func setViews(
    _ views: [NSView],
    in gravity: NSStackView.Gravity
)
```

## Parameters 

`views`  

The array of views you are specifying for the gravity area.

`gravity`  

The gravity area that you’re specifying the array of views for. Valid values are those in the NSStackView.Gravity enumeration, according to the stack view’s layout direction.

## Discussion

Calling this method updates the stack view’s layout, which can change the stack view size. As a result, views could detach or clip according to the clipping resistance of the stack view and the visibility priorities of its views.

A view in a detached state is not present in the stack view’s view hierarchy, but it still consumes memory. To respond to detachment and reattachment of views, implement an NSStackViewDelegate object and assign it to the delegate property.

## See Also

### Managing Views in Gravity Areas

func addView(NSView, in: NSStackView.Gravity)

Adds a view to the end of the stack view gravity area.

func insertView(NSView, at: Int, in: NSStackView.Gravity)

Adds a view to a stack view gravity area at a specified index position.

func removeView(NSView)

Removes a specified view from the stack view.

enum Gravity

The gravity areas available in a stack view.

