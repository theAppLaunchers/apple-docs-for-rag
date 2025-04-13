

- Core Animation
- CALayer
-  backgroundFilters 

Instance Property

# backgroundFilters

An array of Core Image filters to apply to the content immediately behind the layer. Animatable.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.1+macOS 10.5+tvOS 9.0+visionOS 1.0+

``` source
var backgroundFilters: [Any]? { get set }
```

## Discussion

Background filters affect the content behind the layer that shows through into the layer itself. Typically this content belongs to the superlayer that acts as the parent of the layer. These filters do not affect the content of the layer itself, including the layer’s background color and border.

The default value of this property is `nil`.

Changing the inputs of the CIFilter object directly after it is attached to the layer causes undefined behavior. In macOS, it is possible to modify filter parameters after attaching them to the layer but you must use the layer’s setValue(_:forKeyPath:) method to do so. In addition, you must assign a name to the filter so that you can identify it in the array. For example, to change the `inputRadius` parameter of the filter, you could use code similar to the following:

- Swift
- Objective-C

```
let layer = CALayer()

if let filter = CIFilter(name:"CIGaussianBlur") {
    filter.name = "myFilter"
    layer.backgroundFilters = [filter]
    layer.setValue(1,
                   forKeyPath: "backgroundFilters.myFilter.inputRadius")
}
```

```
CIFilter *filter = ...;
CALayer *layer = ...;

filter.name = @"myFilter";
layer.backgroundFilters = [NSArray arrayWithObject:filter];
[layer setValue:[NSNumber numberWithInt:1] forKeyPath:@"backgroundFilters.myFilter.inputRadius"];
```

You use the layer’s masksToBounds to control the extent of its background filter’s effect.

The following code shows how to create two overlapping text layers, `background` and `foreground`. A Gaussian blur filter is added to the foreground layer’s backgroundFilters array and its masksToBounds is set to true:

```
view.layer = CALayer()
view.layerUsesCoreImageFilters = true

let background = CATextLayer()
background.string = "background"
background.backgroundColor = NSColor.red.cgColor
background.alignmentMode = kCAAlignmentCenter
background.fontSize = 96
background.frame = CGRect(x: 10, y: 10, width: 640, height: 160)

let foreground = CATextLayer()
foreground.string = "foreground"
foreground.backgroundColor = NSColor.blue.cgColor
foreground.alignmentMode = kCAAlignmentCenter
foreground.fontSize = 48
foreground.opacity = 0.5
foreground.frame = CGRect(x: 20, y: 20, width: 600, height: 60)
foreground.masksToBounds = true

if let blurFilter = CIFilter(name: "CIGaussianBlur",
                             withInputParameters: [kCIInputRadiusKey: 2]) {
    foreground.backgroundFilters = [blurFilter]
}

view.layer?.addSublayer(background)
background.addSublayer(foreground)
```

The following figure shows the result: the background layer is only blurred where it is overlapped by the foreground layer.

However, if the foreground layer’s masksToBounds is set to false, the entire background layer is blurred as illustrated in the following figure.

### Special Considerations

This property is not supported on layers in iOS.

## See Also

### Layer Filters

var filters: [Any]?

An array of Core Image filters to apply to the contents of the layer and its sublayers. Animatable.

var compositingFilter: Any?

A CoreImage filter used to composite the layer and the content behind it. Animatable.

var minificationFilter: CALayerContentsFilter

The filter used when reducing the size of the content.

var minificationFilterBias: Float

The bias factor used by the minification filter to determine the levels of detail.

var magnificationFilter: CALayerContentsFilter

The filter used when increasing the size of the content.

