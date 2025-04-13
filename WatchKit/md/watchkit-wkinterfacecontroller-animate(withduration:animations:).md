

- WatchKit
- WKInterfaceController
-  animate(withDuration:animations:) 

Instance Method

# animate(withDuration:animations:)

Animates changes to one or more interface objects over the specified duration.

watchOS 2.0+

``` source
@MainActor
func animate(
    withDuration duration: TimeInterval,
    animations: @escaping () -> Void
)
```

## Parameters 

`duration`  

The total duration of the animations, measured in seconds. If you specify a negative value or 0, the changes are made without animating them.

`animations`  

A block containing the changes to make to objects in the interface. Use this block to change any animatable properties of your interface objects. The block takes no parameters and has no return value. This parameter must not be `nil`.

## Discussion

Use this method to animate changes to the following attributes of your interface objects:

- alpha (opacity)

- width and height

- horizontal and vertical alignment

- background or tint color

- group content insets

Changes to visible items are animated over the specified duration. If you call this method in an interface controller that is managing a glance or custom notification interface, the changes you make are applied without animations. You cannot animate changes to the content of an object.

