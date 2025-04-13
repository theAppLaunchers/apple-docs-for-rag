

- MetalKit
- MTKView
-  preferredFramesPerSecond 

Instance Property

# preferredFramesPerSecond

The rate at which the view redraws its contents.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+tvOS 9.0+visionOS 1.0+

``` source
@MainActor
var preferredFramesPerSecond: Int { get set }
```

## Discussion

When your application sets its preferred frame rate, the view chooses a frame rate as close to that as possible based on the capabilities of the screen the view is displayed on. To provide a consistent frame rate, the actual frame rate chosen is usually a factor of the maximum refresh rate of the screen. For example, if the maximum refresh rate of the screen is `60` frames per second, that’s also the highest frame rate the view sets as the actual frame rate. However, if you ask for a lower frame rate, the view might choose `30`, `20`, or `15` frames per second, or another factor, as the actual frame rate.

Your application should choose a frame rate that it can consistently maintain. The default value is `60` frames per second.

## See Also

### Configuring Drawing Behavior

var isPaused: Bool

A Boolean value that indicates whether the draw loop is paused.

var enableSetNeedsDisplay: Bool

A Boolean value that indicates whether the view responds to setNeedsDisplay().

func draw()

Redraws the view’s contents immediately.

var presentsWithTransaction: Bool

A Boolean value that determines whether the view presents its content using a Core Animation transaction.

