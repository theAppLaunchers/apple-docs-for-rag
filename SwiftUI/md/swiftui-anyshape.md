

- SwiftUI
-  AnyShape 

Structure

# AnyShape

A type-erased shape value.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
@frozen
struct AnyShape
```

## Overview

You can use this type to dynamically switch between shape types:

```
struct MyClippedView: View {
    var isCircular: Bool

    var body: some View {
        OtherView().clipShape(isCircular ?
            AnyShape(Circle()) : AnyShape(Capsule()))
    }
}
```

## Topics

### Creating a shape

init&lt;S>(S)

Create an any shape instance from a shape.

## Relationships

### Conforms To

- Animatable
- Sendable
- Shape
- View

## See Also

### Defining shape behavior

protocol ShapeView

A view that provides a shape that you can use for drawing operations.

protocol Shape

A 2D shape that you can use when drawing a view.

enum ShapeRole

Ways of styling a shape.

struct StrokeStyle

The characteristics of a stroke that traces a path.

struct StrokeShapeView

A shape provider that strokes its shape.

struct StrokeBorderShapeView

A shape provider that strokes the border of its shape.

struct FillStyle

A style for rasterizing vector shapes.

struct FillShapeView

A shape provider that fills its shape.

