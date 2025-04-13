

- ExtensionKit
- AppExtensionSceneBuilder
-  buildBlock(\_:\_:\_:) 

Type Method

# buildBlock(\_:\_:\_:)

Builds an extension scene by combining three scenes.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
@MainActor @preconcurrency
static func buildBlock(
    _ c0: C0,
    _ c1: C1,
    _ c2: C2
) -> some AppExtensionScene where C0 : AppExtensionScene, C1 : AppExtensionScene, C2 : AppExtensionScene
```

## Return Value

The composed scene.

## See Also

### Building Content

static func buildBlock&lt;Content>(Content) -> some AppExtensionScene

Passes through a single extension scene unmodified.

static func buildBlock&lt;C0, C1>(C0, C1) -> some AppExtensionScene

Builds an extension scene by combining two scenes.

static func buildBlock&lt;C0, C1, C2, C3>(C0, C1, C2, C3) -> some AppExtensionScene

Builds an extension scene by combining four scenes.

static func buildBlock&lt;C0, C1, C2, C3, C4>(C0, C1, C2, C3, C4) -> some AppExtensionScene

Builds an extension scene by combining five scenes.

static func buildBlock&lt;C0, C1, C2, C3, C4, C5>(C0, C1, C2, C3, C4, C5) -> some AppExtensionScene

Builds an extension scene by combining six scenes.

static func buildBlock&lt;C0, C1, C2, C3, C4, C5, C6>(C0, C1, C2, C3, C4, C5, C6) -> some AppExtensionScene

Builds an extension scene by combining seven scenes.

static func buildBlock&lt;C0, C1, C2, C3, C4, C5, C6, C7>(C0, C1, C2, C3, C4, C5, C6, C7) -> some AppExtensionScene

Builds an extension scene by combining eight scenes.

static func buildBlock&lt;C0, C1, C2, C3, C4, C5, C6, C7, C8>(C0, C1, C2, C3, C4, C5, C6, C7, C8) -> some AppExtensionScene

Builds an extension scene by combining nine scenes.

static func buildBlock&lt;C0, C1, C2, C3, C4, C5, C6, C7, C8, C9>(C0, C1, C2, C3, C4, C5, C6, C7, C8, C9) -> some AppExtensionScene

Builds an extension scene by combining ten scenes.

