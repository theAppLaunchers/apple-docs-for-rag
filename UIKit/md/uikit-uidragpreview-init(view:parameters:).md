

- UIKit
- UIDragPreview
-  init(view:parameters:) 

Initializer

# init(view:parameters:)

Initializes a new drag item preview with a view and with a set of appearance parameters.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.1+visionOS 1.0+

``` source
@MainActor
init(
    view: UIView,
    parameters: UIDragPreviewParameters
)
```

## Parameters 

`view`  

A UIView object representing the drag item.

`parameters`  

A UIDragPreviewParameters object containing appearance parameters for the drag item preview.

## Return Value

A drag preview that is based on the specified view and has specific appearance parameters.

## Discussion

Use this method to display a custom drag item preview based on the provided view and appearance parameters. The appearance parameters specify display options for the preview, such as a background color and a Bézier path of the visible area of the provided view. The appearance parameters affect only the display of the preview, and not the provided view. The drag item preview uses a snapshot of the view for the display, and it never changes or moves the view.

## See Also

### Initializing a drag item preview

convenience init(view: UIView)

Initializes a new drag item preview with a view, using the default appearance parameters.

convenience init(forURL: URL)

Initializes a new drag item preview with a URL.

convenience init(forURL: URL, title: String?)

Initializes a drag item preview with a URL and title.

