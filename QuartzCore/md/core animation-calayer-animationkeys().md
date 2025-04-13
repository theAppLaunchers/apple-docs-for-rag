

- Core Animation
- CALayer
-  animationKeys() 

Instance Method

# animationKeys()

Returns an array of strings that identify the animations currently attached to the layer.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.1+macOS 10.5+tvOS 9.0+visionOS 1.0+

``` source
func animationKeys() -> [String]?
```

## Return Value

An array of NSString objects identifying the current animations.

## Discussion

The order of the array matches the order in which animations will be applied to the layer.

## See Also

### Layer Animations

func add(CAAnimation, forKey: String?)

Add the specified animation object to the layer’s render tree.

func animation(forKey: String) -> CAAnimation?

Returns the animation object with the specified identifier.

func removeAllAnimations()

Remove all animations attached to the layer.

func removeAnimation(forKey: String)

Remove the animation object with the specified key.

