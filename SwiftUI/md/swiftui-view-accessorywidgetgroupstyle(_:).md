

- SwiftUI
- View
-  accessoryWidgetGroupStyle(\_:) 

Instance Method

# accessoryWidgetGroupStyle(\_:)

The view modifier that can be applied to `AccessoryWidgetGroup` to specify the shape the three content views will be masked with. The value of `style` is set to `.automatic`, which is `.circular` by default.

watchOS 11.0+

``` source
@MainActor @preconcurrency
func accessoryWidgetGroupStyle(_ style: AccessoryWidgetGroupStyle = .automatic) -> some View
```

## Parameters 

`style`  

The shape with which the content views are masked. The available shapes are circle and rounded square.

