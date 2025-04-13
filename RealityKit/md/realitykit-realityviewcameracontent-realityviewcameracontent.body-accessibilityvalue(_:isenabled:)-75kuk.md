

- RealityKit
- RealityViewCameraContent
- RealityViewCameraContent.Body
-  accessibilityValue(\_:isEnabled:) 

Instance Method

# accessibilityValue(\_:isEnabled:)

Adds a textual description of the value that the view contains.

RealityKitSwiftUIiOS 18.0+iPadOS 18.0+Mac CatalystmacOS 15.0+tvOS 18.0+visionOS 2.0+watchOS 11.0+

``` source
nonisolated
func accessibilityValue(
    _ valueKey: LocalizedStringKey,
    isEnabled: Bool
) -> ModifiedContent
```

## Parameters 

`valueKey`  

The accessibility value to apply.

`isEnabled`  

If true the accessibility value is applied; otherwise the accessibility value is unchanged.

## Discussion

Use this method to describe the value represented by a view, but only if that’s different than the view’s label. For example, for a slider that you label as “Volume” using accessibilityLabel(), you can provide the current volume setting, like “60%”, using accessibilityValue().

