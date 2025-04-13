

- WebKit
- WKContentWorld
-  page 

Type Property

# page

The content world for the current webpage’s content.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 11.0+visionOS 1.0+

``` source
@MainActor
class var page: WKContentWorld { get }
```

## Discussion

This property contains the content world for scripts that the current webpage executes. Be careful when manipulating variables in this content world. If you modify a variable with the same name as one the webpage uses, you may unintentionally disrupt the normal operation of that page.

