

- SwiftUI
- Shader
-  compile(as:) 

Instance Method

# compile(as:)

Attempts to asynchronously compile a shader function, to minimize the chance of stalling when it is first used for rendering.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+

``` source
func compile(as type: Shader.UsageType) async throws
```

## Parameters 

`type`  

How the shader will eventually be used.

## Discussion

Before being available for rendering each shader must be compiled for the current GPU. By default this happens on first use, but that may cause that frame to be delayed waiting for the compiler, i.e. cause a visible “glitch” in animations.

Calling this method for each shader before it’s first used allows the necessary compilation to happen ahead of time, eliminating the delay on the first actual use (provided `compile()` completes before the first use of the shader).

For compilation to be successful the specified usage type must match how the shader is eventually used to render, and its current argument values must match the types of the arguments used when rendering (however array and data sizes may be empty).

For example, to compile a fill shader asynchronously when your app launches:

```
Task {
    let shader = ShaderLibrary.example(.color(.clear), .float(0))
    try! await shader.compile(as: .shapeStyle)
}
```

Here the MSL shader function `example` takes two uniform arguments: a color and a numeric value. The placeholder values are replaced with actual values when using the shader, in this case to fill a circle:

```
Circle().fill(
    ShaderLibrary.example(.color(.orange), .float(32)))
```

Throws

An error describing why compilation failed.

