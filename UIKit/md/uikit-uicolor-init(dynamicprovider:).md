

- UIKit
- UIColor
-  init(dynamicProvider:) 

Initializer

# init(dynamicProvider:)

Creates a color object that uses the specified block to generate its color data dynamically.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.1+tvOS 13.0+visionOS 1.0+

``` source
init(dynamicProvider: @escaping (UITraitCollection) -> UIColor)
```

## Parameters 

`dynamicProvider`  

A block that determines the appropriate color values based on the specified traits. This block returns a UIColor object and takes a single parameter:

traits  
The trait collection to use when generating the color information. Always use the traits in this collection, and not the traits of the current environment, when determining the color information.

## Return Value

A color object whose color information is provided by the specified block.

## Discussion

Use this method to create a color object whose component values change based on the currently active traits. The block you provide creates a new color object based on the traits in the provided trait collection.

