

- SwiftUI
- ViewAlignedScrollTargetBehavior
- ViewAlignedScrollTargetBehavior.LimitBehavior
-  alwaysByFew 

Type Property

# alwaysByFew

The always-by-few limit behavior.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+watchOS 11.0+

``` source
static var alwaysByFew: ViewAlignedScrollTargetBehavior.LimitBehavior { get }
```

## Discussion

Limit the number of views that can be scrolled by a single interaction to a small number of views, rather than a single view at a time. The number of views is determined automatically.

