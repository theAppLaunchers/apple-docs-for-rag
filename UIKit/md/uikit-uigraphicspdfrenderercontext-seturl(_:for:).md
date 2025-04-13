

- UIKit
- UIGraphicsPDFRendererContext
-  setURL(\_:for:) 

Instance Method

# setURL(\_:for:)

Creates a link to an external resource defined by a URL

iOS 10.0+iPadOS 10.0+Mac Catalyst 13.1+tvOS 10.0+visionOS 1.0+

``` source
func setURL(
    _ url: URL,
    for rect: CGRect
)
```

## Parameters 

`url`  

The external URL that the user is directed to on clicking the link.

`rect`  

The region of the current page that becomes the active link area, specified in points in the PDF coordinate space.

## Discussion

Use this method to create links to external resources in the current page of a PDF. The URL is interpreted by the PDF viewer.

Note

Specify the `rect` value in the PDF coordinate space, not the Core Graphics context coordinate space. This means that the origin is in the bottom-left rather than the top-left, and the y-axis increases in an upwards direction. Use the userSpaceToDeviceSpaceTransform property on CGContext to map between the two.

To create internal links within the current PDF document, use addDestination(withName:at:) and setDestinationWithName(_:for:).

## See Also

### Managing destinations

func addDestination(withName: String, at: CGPoint)

Creates a named destination point in the current PDF page.

func setDestinationWithName(String, for: CGRect)

Creates a link rectangle in the current page that jumps the PDF viewer to the named destination when clicked.

