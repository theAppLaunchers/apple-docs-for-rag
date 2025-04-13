

- PDFKit
- PDFAnnotation
-  popup 

Instance Property

# popup

Returns the pop-up annotation associated with an annotation.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.1+macOS 10.5+tvOS 11.0+visionOS 1.0+

``` source
var popup: PDFAnnotation? { get set }
```

## Return Value

The pop-up annotation associated with the annotation, or `NULL` if no pop-up exists.

## Discussion

Pop-up annotations are not used with links or widgets. The bounds and open state of the pop-up annotation indicate the placement and open state of the pop-up window.

## See Also

### Related Documentation

class PDFAnnotation

An annotation in a PDF document.

### Configuring Pop-Up Annotations

var isOpen: Bool

A Boolean value that indicates whether the pop-up annotation is in an opened state, displaying its text content, or in a closed state, displaying an icon.

