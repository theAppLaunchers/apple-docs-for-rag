

- SceneKit
- SCNNode
-  filters 

Instance Property

# filters

An array of Core Image filters to be applied to the rendered contents of the node.

iOSiPadOSMac Catalyst 13.1+macOS 10.9+tvOSvisionOS

``` source
var filters: [CIFilter]? { get set }
```

## Discussion

An array of CIFilter objects.

When this array is nonempty, SceneKit renders the node (and its child node hierarchy) into an image buffer and then applies the filters before compositing the filters’ output into the rendered scene. The order of the array determines the order of the Core Image filter chain. For example, the following code applies a pixellate filter to the rendered node and then a blur filter to the output of the pixellate filter:

```
let gaussianBlurFilter = CIFilter(name: "CIGaussianBlur")
gaussianBlurFilter.name = "blur"
let pixellateFilter = CIFilter(name: CIPixellate")
node.filters = [ pixellateFilter, gaussianBlurFilter ]
```

```
CIFilter *gaussianBlurFilter = [CIFilter filterWithName:@"CIGaussianBlur"];
gaussianBlurFilter.name = @"blur";
CIFilter *pixellateFilter = [CIFilter filterWithName:@"CIPixellate"];
pixellateFilter.name = @"pixellate";
node.filters = @[ pixellateFilter, gaussianBlurFilter ];
```

After you attach filters to a node, you can modify filter parameters only by calling setValue(_:forKeyPath:) on the node the filter is attached to. (Directly modifying the parameters of a filter attached to a node results in undefined behavior.) To refer to a filter by key path, you must set the filter’s `name` property to a string that uniquely identifies that filter instance, as shown in the code above.

You can also animate filter parameters by their key paths, as in the code below that animates one of the filters from the previous example.

```
let animation = CABasicAnimation(keyPath: "filters.pixellate.inputScale") // user name set on filter instance above
animation.toValue = 50
animation.fromValue = 0
animation.autoreverses = true
animation.repeatCount = .infinity
animation.duration = 2.0
node.add(animation, forKey: nil)
```

```
CAAnimation *animation = [CABasicAnimation animationWithKeyPath:@"filters.pixellate.inputScale"]; // use name set on filter instance above
animation.toValue = @50;
animation.fromValue = @0;
animation.autoreverses = YES;
animation.repeatCount = FLT_MAX;
animation.duration = 2.0;
[node addAnimation:animation forKey:nil];
```

## See Also

### Customizing Node Rendering

var rendererDelegate: (any SCNNodeRendererDelegate)?

An object responsible for rendering custom contents for the node using Metal or OpenGL.

