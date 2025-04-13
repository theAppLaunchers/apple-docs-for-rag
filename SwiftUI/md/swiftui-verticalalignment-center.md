

- SwiftUI
- VerticalAlignment
-  center 

Type Property

# center

A guide that marks the vertical center of the view.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
static let center: VerticalAlignment
```

## Mentioned in 

Aligning views across stacks

## Discussion

Use this guide to align the centers of views:

The following code generates the image above using an HStack:

```
struct VerticalAlignmentCenter: View {
    var body: some View {
        HStack(alignment: .center, spacing: 0) {
            Color.red.frame(height: 1)
            Text("Center").font(.title).border(.gray)
            Color.red.frame(height: 1)
        }
    }
}
```

## See Also

### Getting guides

static let top: VerticalAlignment

A guide that marks the top edge of the view.

static let bottom: VerticalAlignment

A guide that marks the bottom edge of the view.

static let firstTextBaseline: VerticalAlignment

A guide that marks the top-most text baseline in a view.

static let lastTextBaseline: VerticalAlignment

A guide that marks the bottom-most text baseline in a view.

