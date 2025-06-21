Framework

# PaperKit

Add drawings, shapes, and a consistent markup experience to your app.

## [Overview](/documentation/PaperKit#overview)

PaperKit builds on top of [PencilKit](/documentation/PencilKit) and [PDFKit](/documentation/PDFKit) to provide a consistent way to add drawing and shapes in your app.

## [Topics](/documentation/PaperKit#topics)

### [View controllers](/documentation/PaperKit#View-controllers)

```swift
```swift
```swift
```swift
class PaperMarkupViewController
```
```

A view controller for interactively creating, and showing markup.

Beta
```
```swift
```swift
```swift
class MarkupEditViewController
```
```

A view controller that manages the interface for inserting content into a canvas.

Beta
```
```swift
```swift
```swift
class MarkupToolbarViewController
```
```
Beta
```
```

### [Configuration](/documentation/PaperKit#Configuration)

```swift
```swift
```swift
```swift
struct FeatureSet
```
```

The features supported by PaperKit UI / data models.

Beta
```
```swift
```swift
```swift
struct ShapeConfiguration
```
```

A configuration that specifies the appearance of a shape.

Beta
```
```swift
```swift
```swift
struct RenderingOptions
```
```

The rendering options for drawing paper data models.

Beta
```
```

### [Data model](/documentation/PaperKit#Data-model)

```swift
```swift
```swift
```swift
struct PaperMarkup
```
```

The data model object for storing markup data created from a `PaperViewController`.

Beta
```
```

### [Error handling](/documentation/PaperKit#Error-handling)

```swift
```swift
```swift
```swift
enum MarkupError
```
```

The error thrown for encoding / decoding data models.

Beta
```
```