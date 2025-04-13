

- UIKit
- UIEvent
-  predictedTouches(for:) 

Instance Method

# predictedTouches(for:)

Returns an array of touches that are predicted to occur for the specified touch.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+tvOS 9.0+visionOS 1.0+

``` source
@MainActor
func predictedTouches(for touch: UITouch) -> [UITouch]?
```

## Parameters 

`touch`  

A main touch object that was reported with the event. The touch object you specify is used to determine which sequence of additional touches is returned.

## Return Value

An array of UITouch objects representing the set of touches that the system predicts will occur next. The order of the objects in the array matches the order in which the touches are expected to be delivered to your app. This array does not include the original touch you specified in the *touch* parameter. The return value is `nil` if the object in the *touch* parameter is not associated with the current event.

## Discussion

Use this method to minimize the apparent latency between the user’s touch input and the rendering of your onscreen content. Processing touch input from the user and translating that information into drawing commands takes time, and turning those drawing commands into rendered content takes additional time. If the user’s finger or Apple Pencil is moving fast enough, these delays can result in a noticeable gap between the current touch location and the rendered content. To minimize the perceived lag, use the predicted touches of this method as additional, temporary input to your content.

The touches returned by this method represent the system’s estimation of where the user’s touch input will be, based on the user’s past input. Append these touches only temporarily to the structures you use for drawing or updating your content, and discard them as soon as you receive a new event with fresh touches. When used in conjunction with coalesced touches and efficient drawing code, you can create the perception that the user’s input is being handled immediately, with little or no lag. That perception improves the user experience of drawing apps or of any app that let users manipulate objects directly onscreen.

## See Also

### Getting the touches for an event

var allTouches: Set&lt;UITouch>?

All touches associated with the event.

func touches(for: UIView) -> Set&lt;UITouch>?

Returns the touch objects from the event that belong to the specified given view.

func touches(for: UIWindow) -> Set&lt;UITouch>?

Returns the touch objects from the event that belong to the specified window.

func coalescedTouches(for: UITouch) -> [UITouch]?

Returns all of the touches associated with the specified main touch.

