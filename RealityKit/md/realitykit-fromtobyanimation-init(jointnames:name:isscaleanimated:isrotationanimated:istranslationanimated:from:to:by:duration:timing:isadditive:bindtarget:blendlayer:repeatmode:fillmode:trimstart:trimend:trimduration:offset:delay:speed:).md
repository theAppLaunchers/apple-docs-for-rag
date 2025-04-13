

- RealityKit
- FromToByAnimation
-  init(jointNames:name:isScaleAnimated:isRotationAnimated:isTranslationAnimated:from:to:by:duration:timing:isAdditive:bindTarget:blendLayer:repeatMode:fillMode:trimStart:trimEnd:trimDuration:offset:delay:speed:) 

Initializer

# init(jointNames:name:isScaleAnimated:isRotationAnimated:isTranslationAnimated:from:to:by:duration:timing:isAdditive:bindTarget:blendLayer:repeatMode:fillMode:trimStart:trimEnd:trimDuration:offset:delay:speed:)

Creates an animation that interpolates between two configurations of the given joints.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+visionOS

``` source
init(
    jointNames: [String],
    name: String = "",
    isScaleAnimated: Bool = true,
    isRotationAnimated: Bool = true,
    isTranslationAnimated: Bool = true,
    from: Value? = nil,
    to: Value? = nil,
    by: Value? = nil,
    duration: TimeInterval = 1.0,
    timing: AnimationTimingFunction = .linear,
    isAdditive: Bool = false,
    bindTarget: BindTarget? = nil,
    blendLayer: Int32 = 0,
    repeatMode: AnimationRepeatMode = .none,
    fillMode: AnimationFillMode = [],
    trimStart: TimeInterval? = nil,
    trimEnd: TimeInterval? = nil,
    trimDuration: TimeInterval? = nil,
    offset: TimeInterval = 0,
    delay: TimeInterval = 0,
    speed: Float = 1.0
)
```

Available when `Value` is `JointTransforms`.

## Parameters 

`jointNames`  

The names of the joints in the animated skeletal pose.

`name`  

A unique name for the animation.

`isScaleAnimated`  

A Boolean value that indicates whether that animation interpolates changes to the target’s size.

`isRotationAnimated`  

A Boolean value that indicates whether that animation interpolates rotational changes.

`isTranslationAnimated`  

A Boolean value that indicates whether that animation interpolates changes to the target object’s position.

`from`  

The state of the target object’s joints before the animation starts.

`to`  

The state of the target object’s joints after the animation finishes.

`by`  

An amount that increments the animated joints during the animation.

`duration`  

The total playback time.

`timing`  

An option that determines the animation’s pace over time.

`isAdditive`  

A Boolean value that indicates whether the animation blends additively with concurrent animations.

`bindTarget`  

A textual name that identifies the particular property that animates.

`blendLayer`  

The order in which the framework composites the animation into the view.

`repeatMode`  

An option that determines how the animation repeats.

`fillMode`  

The playback behavior outside of the normal duration.

`trimStart`  

The optional time, in seconds, at which the animation plays.

`trimEnd`  

The optional time, in seconds, at which the animation stops.

`trimDuration`  

An optional duration that overrides the calculated duration.

`offset`  

The time, in seconds, at which the animation begins within the duration.

`delay`  

An amount of time that elapses before the animation plays.

`speed`  

A factor that increases or decreases the animation’s rate of playback.

## See Also

### Creating an animation

init(name: String, from: Value?, to: Value?, by: Value?, duration: TimeInterval, timing: AnimationTimingFunction, isAdditive: Bool, bindTarget: BindTarget?, blendLayer: Int32, repeatMode: AnimationRepeatMode, fillMode: AnimationFillMode, trimStart: TimeInterval?, trimEnd: TimeInterval?, trimDuration: TimeInterval?, offset: TimeInterval, delay: TimeInterval, speed: Float)

Creates an animation that interpolates between two values for a property of the target entity.

