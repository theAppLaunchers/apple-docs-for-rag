

- CarPlay
- CPRouteChoice
-  init(summaryVariants:additionalInformationVariants:selectionSummaryVariants:) 

Initializer

# init(summaryVariants:additionalInformationVariants:selectionSummaryVariants:)

Creates a route choice.

iOS 12.0+iPadOS 12.0+Mac Catalyst 13.1+

``` source
init(
    summaryVariants: [String],
    additionalInformationVariants: [String],
    selectionSummaryVariants: [String]
)
```

## Parameters 

`summaryVariants`  

An array of summary variants. The system displays the first variant that fits in the available screen space, so arrange the variants from most to least preferred display order. You should localize each variant for display to the user. You must provide at least one variant; for example, *Via I-280 South*.

`additionalInformationVariants`  

An array of variants providing additional information about the route choice. The system displays the first variant that fits in the available screen space, so arrange the variants from most to least preferred display order. You should localize each variant for display to the user. You must provide at least one variant; for example, *Fastest Route* or *Avoids Tolls*.

`selectionSummaryVariants`  

An array of selection summary variants. The system displays the first variant that fits in the available screen space, so arrange the variants from most to least preferred display order. You should localize each variant for display to the user. You must provide at least one variant.

## Return Value

A newly initialized route choice.

