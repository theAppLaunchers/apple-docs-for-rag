

- Accelerate
- BNNS
- BNNS.AdamWOptimizer
-  init(learningRate:beta1:beta2:timeStep:epsilon:gradientScale:weightDecay:gradientClipping:usesAMSGrad:) Deprecated

Initializer

# init(learningRate:beta1:beta2:timeStep:epsilon:gradientScale:weightDecay:gradientClipping:usesAMSGrad:)

Returns a new AdamW optimizer object with gradient clipped by value or clipped by norm.

iOS 15.0+iPadOS 15.0+Mac CatalystmacOS 12.0+tvOS 15.0+visionOSwatchOS 8.0+

``` source
init(
    learningRate: Float = 0.001,
    beta1: Float = 0.9,
    beta2: Float = 0.999,
    timeStep: Float = 1,
    epsilon: Float = 1e-8,
    gradientScale: Float,
    weightDecay: Float = 1e-2,
    gradientClipping: BNNS.GradientClipping,
    usesAMSGrad: Bool = false
)
```

Deprecated

Use the BNNSGraph API instead.

## Parameters 

`learningRate`  

A value that specifies the learning rate.

`beta1`  

A value that specifies the first-moment constant, in the range `0` to `1`.

`beta2`  

A value that specifies the second-moment constant, in the range `0` to `1`.

`timeStep`  

A value that’s at least `1` and represents the optimizer’s current time.

`epsilon`  

The epsilon value you use to improve numerical stability.

`gradientScale`  

A value that specifies the gradient scaling factor.

`weightDecay`  

The weight decay coefficient.

`gradientClipping`  

The gradient clipping function and bounds.

`usesAMSGrad`  

A Boolean value that specifies whether the optimizer should use the AMSGrad variant.

