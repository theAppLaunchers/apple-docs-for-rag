

- Foundation
- Date
- Date.RelativeFormatStyle
- Date.RelativeFormatStyle.Presentation
-  named 

Type Property

# named

A style that uses named styles to describe relative dates, such as “yesterday”, “last week”, or “next week”.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

``` source
static var named: Date.RelativeFormatStyle.Presentation { get }
```

## Discussion

The format uses the numeric style if a name isn’t available.

## See Also

### Modifying Relative Date Style Presentations

static var numeric: Date.RelativeFormatStyle.Presentation

A style that uses a numeric style to describe relative dates, such as “1 day ago” or “in 3 weeks”.

