

- SwiftUI
- Animation
-  bouncy 

Type Property

# bouncy

A spring animation with a predefined duration and higher amount of bounce.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
static var bouncy: Animation { get }
```

## See Also

### Getting built-in spring animations

static func bouncy(duration: TimeInterval, extraBounce: Double) -> Animation

A spring animation with a predefined duration and higher amount of bounce that can be tuned.

static var smooth: Animation

A smooth spring animation with a predefined duration and no bounce.

static func smooth(duration: TimeInterval, extraBounce: Double) -> Animation

A smooth spring animation with a predefined duration and no bounce that can be tuned.

static var snappy: Animation

A spring animation with a predefined duration and small amount of bounce that feels more snappy.

static func snappy(duration: TimeInterval, extraBounce: Double) -> Animation

A spring animation with a predefined duration and small amount of bounce that feels more snappy and can be tuned.

