

- SwiftUI
-  Alignment 

Structure

# Alignment

An alignment in both axes.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
@frozen
struct Alignment
```

## Mentioned in 

Building layouts with stack views

Aligning views within a stack

## Overview

An `Alignment` contains a HorizontalAlignment guide and a VerticalAlignment guide. Specify an alignment to direct the behavior of certain layout containers and modifiers, like when you place views in a ZStack, or layer a view in front of or behind another view using overlay(alignment:content:) or background(alignment:content:), respectively. During layout, SwiftUI brings the specified guides of the affected views together, aligning the views.

SwiftUI provides a set of built-in alignments that represent common combinations of the built-in horizontal and vertical alignment guides. The blue boxes in the following diagram demonstrate the alignment named by each box’s label, relative to the background view:

The following code generates the diagram above, where each blue box appears in an overlay that’s configured with a different alignment:

```
struct AlignmentGallery: View {
    var body: some View {
        BackgroundView()
            .overlay(alignment: .topLeading) { box(".topLeading") }
            .overlay(alignment: .top) { box(".top") }
            .overlay(alignment: .topTrailing) { box(".topTrailing") }
            .overlay(alignment: .leading) { box(".leading") }
            .overlay(alignment: .center) { box(".center") }
            .overlay(alignment: .trailing) { box(".trailing") }
            .overlay(alignment: .bottomLeading) { box(".bottomLeading") }
            .overlay(alignment: .bottom) { box(".bottom") }
            .overlay(alignment: .bottomTrailing) { box(".bottomTrailing") }
            .overlay(alignment: .leadingLastTextBaseline) { box(".leadingLastTextBaseline") }
            .overlay(alignment: .trailingFirstTextBaseline) { box(".trailingFirstTextBaseline") }
    }

    private func box(_ name: String) -> some View {
        Text(name)
            .font(.system(.caption, design: .monospaced))
            .padding(2)
            .foregroundColor(.white)
            .background(.blue.opacity(0.8), in: Rectangle())
    }
}

private struct BackgroundView: View {
    var body: some View {
        Grid(horizontalSpacing: 0, verticalSpacing: 0) {
            GridRow {
                Text("Some text in an upper quadrant")
                Color.gray.opacity(0.3)
            }
            GridRow {
                Color.gray.opacity(0.3)
                Text("More text in a lower quadrant")
            }
        }
        .aspectRatio(1, contentMode: .fit)
        .foregroundColor(.secondary)
        .border(.gray)
    }
}
```

To avoid crowding, the alignment diagram shows only two of the available text baseline alignments. The others align as their names imply. Notice that the first text baseline alignment aligns with the top-most line of text in the background view, while the last text baseline aligns with the bottom-most line. For more information about text baseline alignment, see VerticalAlignment.

In a left-to-right language like English, the leading and trailing alignments appear on the left and right edges, respectively. SwiftUI reverses these in right-to-left language environments. For more information, see HorizontalAlignment.

### Custom alignment

You can create custom alignments — which you typically do to make use of custom horizontal or vertical guides — by using the init(horizontal:vertical:) initializer. For example, you can combine a custom vertical guide called `firstThird` with the built-in horizontal center guide, and use it to configure a ZStack:

```
ZStack(alignment: Alignment(horizontal: .center, vertical: .firstThird)) {
    // ...
}
```

For more information about creating custom guides, including the code that creates the custom `firstThird` alignment in the example above, see AlignmentID.

## Topics

### Getting top guides

static let topLeading: Alignment

A guide that marks the top and leading edges of the view.

static let top: Alignment

A guide that marks the top edge of the view.

static let topTrailing: Alignment

A guide that marks the top and trailing edges of the view.

### Getting middle guides

static let leading: Alignment

A guide that marks the leading edge of the view.

static let center: Alignment

A guide that marks the center of the view.

static let trailing: Alignment

A guide that marks the trailing edge of the view.

### Getting bottom guides

static let bottomLeading: Alignment

A guide that marks the bottom and leading edges of the view.

static let bottom: Alignment

A guide that marks the bottom edge of the view.

static let bottomTrailing: Alignment

A guide that marks the bottom and trailing edges of the view.

### Getting text baseline guides

static var leadingFirstTextBaseline: Alignment

A guide that marks the leading edge and top-most text baseline in a view.

static var centerFirstTextBaseline: Alignment

A guide that marks the top-most text baseline in a view.

static var trailingFirstTextBaseline: Alignment

A guide that marks the trailing edge and top-most text baseline in a view.

static var leadingLastTextBaseline: Alignment

A guide that marks the leading edge and bottom-most text baseline in a view.

static var centerLastTextBaseline: Alignment

A guide that marks the bottom-most text baseline in a view.

static var trailingLastTextBaseline: Alignment

A guide that marks the trailing edge and bottom-most text baseline in a view.

### Creating a custom alignment

init(horizontal: HorizontalAlignment, vertical: VerticalAlignment)

Creates a custom alignment value with the specified horizontal and vertical alignment guides.

var horizontal: HorizontalAlignment

The alignment on the horizontal axis.

var vertical: VerticalAlignment

The alignment on the vertical axis.

## Relationships

### Conforms To

- BitwiseCopyable
- Copyable
- Equatable
- Sendable

## See Also

### Aligning views

Aligning views within a stack

Position views inside a stack using alignment guides.

Aligning views across stacks

Create a custom alignment and use it to align views across multiple stacks.

func alignmentGuide(_:computeValue:)

Sets the view’s horizontal alignment.

struct HorizontalAlignment

An alignment position along the horizontal axis.

struct VerticalAlignment

An alignment position along the vertical axis.

struct DepthAlignment

An alignment position along the depth axis.

protocol AlignmentID

A type that you use to create custom alignment guides.

struct ViewDimensions

A view’s size and alignment guides in its own coordinate space.

