

- SwiftUI
-  ProposedViewSize 

Structure

# ProposedViewSize

A proposal for the size of a view.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
@frozen
struct ProposedViewSize
```

## Overview

During layout in SwiftUI, views choose their own size, but they do that in response to a size proposal from their parent view. When you create a custom layout using the Layout protocol, your layout container participates in this process using `ProposedViewSize` instances. The layout protocol’s methods take a proposed size input that you can take into account when arranging views and calculating the size of the composite container. Similarly, your layout proposes a size to each of its own subviews when it measures and places them.

Layout containers typically measure their subviews by proposing several sizes and looking at the responses. The container can use this information to decide how to allocate space among its subviews. A layout might try the following special proposals:

- The zero proposal; the view responds with its minimum size.

- The infinity proposal; the view responds with its maximum size.

- The unspecified proposal; the view responds with its ideal size.

A layout might also try special cases for one dimension at a time. For example, an HStack might measure the flexibility of its subviews’ widths, while using a fixed value for the height.

## Topics

### Getting standard proposals

static let zero: ProposedViewSize

A size proposal that contains zero in both dimensions.

static let infinity: ProposedViewSize

A size proposal that contains infinity in both dimensions.

static let unspecified: ProposedViewSize

The proposed size with both dimensions left unspecified.

### Creating a custom size proposal

init(CGSize)

Creates a new proposed size from a specified size.

init(width: CGFloat?, height: CGFloat?)

Creates a new proposed size using the specified width and height.

### Getting the proposal’s dimensions

var height: CGFloat?

The proposed vertical size measured in points.

var width: CGFloat?

The proposed horizontal size measured in points.

### Modifying a proposal

func replacingUnspecifiedDimensions(by: CGSize) -> CGSize

Creates a new proposal that replaces unspecified dimensions in this proposal with the corresponding dimension of the specified size.

## Relationships

### Conforms To

- BitwiseCopyable
- Copyable
- Equatable
- Sendable

## See Also

### Configuring a custom layout

struct LayoutProperties

Layout-specific properties of a layout container.

struct ViewSpacing

A collection of the geometric spacing preferences of a view.

