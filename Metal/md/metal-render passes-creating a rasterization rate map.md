

- Metal
- Render Passes
-  Creating a Rasterization Rate Map 

Article

# Creating a Rasterization Rate Map

Define the rasterization rates for each part of your render target.

## Overview

A rasterization rate map specifies the size of the final render target in logical viewport coordinates and rasterization rates within that area. You partition the render target into different horizontal and vertical zones and provide rasterization rates for each of these zones. From this configuration data, the rate map calculates the sizes for your intermediate texture targets and provides mapping functions between logical viewport coordinates and physical pixel coordinates.

To create a rate map, you create and configure a rate map descriptor for it and ask the device object to create it. You then keep the rate map around for as long as you need it for your render targets.

For example, if you’re rendering for display to the screen, set the screenSize property of the rate map descriptor to the drawableSize property of the destination CAMetalLayer object.

- Swift
- Objective-C

```
let descriptor = MTLRasterizationRateMapDescriptor()
descriptor.label = "My rate map"

let layerWidth = Int(metalLayer.drawableSize.width)
let layerHeight = Int(metalLayer.drawableSize.height)
descriptor.screenSize = MTLSizeMake(layerWidth, layerHeight, 0)
```

```
MTLRasterizationRateMapDescriptor *descriptor = [[MTLRasterizationRateMapDescriptor alloc] init];
descriptor.label = @"My rate map";
descriptor.screenSize = destinationMetalLayer.drawableSize;
```

### Create a Layer Rate Descriptor

To specify rasterization rates, create a layer rate descriptor with the rates you want to apply to each layer in the render target. If you aren’t using layered rendering, create a single layer rate descriptor. Otherwise, you can provide different rasterization rates for each layer. (For more information about layered rendering, see Rendering to Multiple Texture Slices in a Draw Command).

Decide how many horizontal and vertical zones you need for each layer. The number of zones should be factors of the width and height of the screen size you specified, and you should choose as many zones as you need for your specific use case. If you need to provide a more precise grid, use more zones.

To specify the grid layout, create a MTLSize object to hold the number of zones, and then create the layer descriptor:

- Swift
- Objective-C

```
let zoneCounts = MTLSizeMake(8, 4, 1)
let layerDescriptor = MTLRasterizationRateLayerDescriptor(sampleCount: zoneCounts)
```

```
MTLSize zoneCounts = MTLSizeMake(8, 4, 1);
MTLRasterizationRateLayerDescriptor *layerDescriptor = [[MTLRasterizationRateLayerDescriptor alloc] initWithSampleCount:zoneCounts];
```

### Specify the Rates for Each Zone

After creating the layer descriptor, specify rates for the rows and columns of the rate map. You determine the horizontal rate for a cell by specifying the rate for its column, and its vertical rate by specifying the rate for its row.

The rate is a floating-point number from `0.0` to `1.0`, where `1.0` means that the hardware should rasterize that zone at the full rate. The following example specifies a full rate for each zone, the default Metal behavior:

- Swift
- Objective-C

```
for row in 0..

```
for (int row = 0; row 

If you specify a value lower than `1.0`, the GPU rasterizes fewer pixels for that zone. For example, the following example code samples the edge zones at half the normal rate:

- Swift
- Objective-C

```
layerDescriptor.horizontal[0] = 0.5
layerDescriptor.horizontal[7] = 0.5
layerDescriptor.vertical[0] = 0.5
layerDescriptor.vertical[3] = 0.5
```

```
layerDescriptor.horizontalSampleStorage[0] = 0.5;
layerDescriptor.horizontalSampleStorage[7] = 0.5;
layerDescriptor.verticalSampleStorage[0] = 0.5;
layerDescriptor.verticalSampleStorage[3] = 0.5;
```

Metal guarantees that the actual rasterization rates are at least as high as the rates you specified. However, when you create the rate map, the device object may split it into more detailed cells or choose higher rates for specific cells if the GPU requires it.

### Add the Layer Descriptor to the Rate Map Descriptor

After you configure the layer descriptor, attach it to the rate map descriptor. When you’ve added all of the layer descriptors, create the rate map:

- Swift
- Objective-C

```
descriptor.setLayer(layerDescriptor, at: 0)
let rateMap = device.makeRasterizationRateMap(descriptor: descriptor)
```

```
[descriptor setLayer:layerDescriptor atIndex:0];
id rateMap = [_device newRasterizationRateMapWithDescriptor: descriptor];
```

## See Also

### Rasterization Settings

Rendering at Different Rasterization Rates

Configure a rasterization rate map to vary rasterization rates depending on the amount of detail needed.

Rendering with a Rasterization Rate Map

Create offscreen textures to hold intermediate rasterized data.

Scaling Variable Rasterization Rate Content

Use the rate map data to scale the content to fill your destination texture.

class MTLRasterizationRateMapDescriptor

An object that you use to configure new rasterization rate maps.

protocol MTLRasterizationRateMap

A compiled read-only object that determines how to apply variable rasterization rates when rendering.

typealias MTLCoordinate2D

A coordinate in the viewport.

func MTLCoordinate2DMake(Float, Float) -> MTLCoordinate2D

Returns a new 2D point with the specified coordinates.

