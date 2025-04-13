

- SceneKit
- SCNParticlePropertyController
-  inputProperty 

Instance Property

# inputProperty

A particle property that provides input values for this property controller’s animation.

iOSiPadOSMac Catalyst 13.1+macOS 10.10+tvOSvisionOSwatchOS

``` source
var inputProperty: SCNParticleSystem.ParticleProperty? { get set }
```

## Discussion

This property applies only when the controller’s inputMode value is SCNParticleInputMode.overOtherProperty.

Use this option to animate one property in response to changes in one of each particle’s other properties. For example, the following code animates particles’ size as a function of their velocity, causing particles to become larger when they move faster:

```
CABasicAnimation *animation = [CABasicAnimation animation];
animation.fromValue = @0.1;
animation.toValue = @10.0;

SCNParticlePropertyController *sizeController =
    [SCNParticlePropertyController controllerWithAnimation:animation];
sizeController.inputMode = SCNParticleInputModeOverOtherProperty;
sizeController.inputProperty = SCNParticlePropertyVelocity;
sizeController.inputScale = 0.1;

particleSystem.propertyControllers = @{ SCNParticlePropertySize : sizeController };
```

To refine the relationship between a range of property values and a range of input values for the controller’s animation, use the inputBias and inputScale properties.

If you specify a vector property (such as acceleration) as the input property, SceneKit uses that vector’s length for the input value.

## See Also

### Managing the Controller’s Animation

var animation: CAAnimation

The Core Animation object defining the behavior of the property animation.

var inputMode: SCNParticleInputMode

The mode that determines input values for the property controller’s animation.

var inputBias: CGFloat

An offset to add to the input value of the controller’s animation.

var inputScale: CGFloat

A factor for multiplying the input value of the controller’s animation.

var inputOrigin: SCNNode?

A node whose distance to each particle provides input values for the controller’s animation.

