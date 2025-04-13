

- Core Animation
- CALayer
-  compositingFilter 

Instance Property

# compositingFilter

A CoreImage filter used to composite the layer and the content behind it. Animatable.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.1+macOS 10.5+tvOS 9.0+visionOS 1.0+

``` source
var compositingFilter: Any? { get set }
```

## Discussion

The default value of this property is `nil`, which causes the layer to use source-over compositing. Although you can use any Core Image filter as a layer’s compositing filter, for best results, use those in the CICategoryCompositeOperation category.

In macOS, it is possible to modify the filter’s parameters after attaching it to the layer but you must use the layer’s setValue(_:forKeyPath:) method to do so. For example, to change the `inputRadius` parameter of the filter, you could use code similar to the following:

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

layer.compositingFilter = filter;
[layer setValue:[NSNumber numberWithInt:1] forKeyPath:@"compositingFilter.inputRadius"];
```

Changing the inputs of the CIFilter object directly after it is attached to the layer causes undefined behavior.

The following code shows how to create two overlapping text layers, background and foreground. Addition compositing is used to composite the foreground over the background.

```
view.layer = CALayer()
view.layerUsesCoreImageFilters = true

let background = CATextLayer()
background.string = "background"
background.foregroundColor = NSColor.gray.cgColor
background.backgroundColor = NSColor.darkGray.cgColor
background.alignmentMode = kCAAlignmentCenter
background.fontSize = 96
background.frame = CGRect(x: 10, y: 10, width: 640, height: 160)

let foreground = CATextLayer()
foreground.string = "foreground"
foreground.foregroundColor = NSColor.lightGray.cgColor
foreground.backgroundColor = NSColor.darkGray.cgColor
foreground.alignmentMode = kCAAlignmentCenter
foreground.fontSize = 48
foreground.opacity = 0.5
foreground.frame = CGRect(x: 20, y: 20, width: 600, height: 60)
foreground.masksToBounds = false

if let compositingFilter = CIFilter(name: "CIAdditionCompositing") {
    foreground.compositingFilter = compositingFilter
}

view.layer?.addSublayer(background)
background.addSublayer(foreground)
```

The following figure shows the result: the identical background colors of the two layers are added together so that a brighter gray is produced where the layers overlap.

The following figure shows the default result when the foreground layer’s compositing filter is `nil` or CISourceOverCompositing.

### Special Considerations

This property is not supported on layers in iOS.

## See Also

### Layer Filters

var filters: [Any]?

An array of Core Image filters to apply to the contents of the layer and its sublayers. Animatable.

var backgroundFilters: [Any]?

An array of Core Image filters to apply to the content immediately behind the layer. Animatable.

var minificationFilter: CALayerContentsFilter

The filter used when reducing the size of the content.

var minificationFilterBias: Float

The bias factor used by the minification filter to determine the levels of detail.

var magnificationFilter: CALayerContentsFilter

The filter used when increasing the size of the content.

