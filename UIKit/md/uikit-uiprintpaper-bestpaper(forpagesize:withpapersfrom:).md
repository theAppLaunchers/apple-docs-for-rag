

- UIKit
- UIPrintPaper
-  bestPaper(forPageSize:withPapersFrom:) 

Type Method

# bestPaper(forPageSize:withPapersFrom:)

The print-paper object that UIKit determines to be the best for a print job based on the specified page size and the paper size–imageable area combinations specific to the printer.

iOS 4.2+iPadOS 4.2+Mac Catalyst 13.1+visionOS 1.0+

``` source
@MainActor
class func bestPaper(
    forPageSize contentSize: CGSize,
    withPapersFrom paperList: [UIPrintPaper]
) -> UIPrintPaper
```

## Parameters 

`contentSize`  

The size of the printed page that your application requests, in points. You should think of this as the size of the physical sheet of paper to use in printing without consideration of the margin.

`paperList`  

An array of `UIPrintPaper` objects that represent combinations of supported paper size and printable areas. The array of objects usually comes directly from the second argument of the printInteractionController(_:choosePaper:) method of the UIPrintInteractionControllerDelegate protocol.

## Return Value

An instance of `UIPrintPaper` that represents the optimal printable area and paper size for the current print job. Returns `nil` if the instance could not be created.

## Discussion

The delegate of UIPrintInteractionController may call this method in its implementation of the printInteractionController(_:choosePaper:) method declared in the UIPrintInteractionControllerDelegate protocol.

