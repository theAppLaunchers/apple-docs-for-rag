

- RealityKit
- ResolvedModel3D
-  accessibilityValue(\_:) 

Instance Method

# accessibilityValue(\_:)

Adds a textual description of the value that the view contains.

RealityKitSwiftUIiOS 14.0+iPadOS 14.0+macOS 11.0+tvOS 14.0+visionOSwatchOS 7.0+

``` source
nonisolated
func accessibilityValue(_ value: S) -> ModifiedContent where S : StringProtocol
```

## Discussion

Use this method to describe the value represented by a view, but only if that’s different than the view’s label. For example, for a slider that you label as “Volume” using accessibilityLabel(), you can provide the current volume setting, like “60%”, using accessibilityValue().

