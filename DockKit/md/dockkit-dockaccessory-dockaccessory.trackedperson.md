

- DockKit
- DockAccessory
-  DockAccessory.TrackedPerson 

Structure

# DockAccessory.TrackedPerson

The state of a tracked person in the active tracking session.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+

``` source
struct TrackedPerson
```

## Topics

### Operators

static func == (DockAccessory.TrackedPerson, DockAccessory.TrackedPerson) -> Bool

Returns a Boolean value indicating whether two values are equal.

### Instance Properties

var identifier: UUID

A unique identifier representing the tracked person. This identifier persists as long as the dock tracks the person. The value is random and doesn’t persist across sessions.

var lookingAtCameraConfidence: Double?

The confidence of the person looking directly at the camera. The range is from `0.0` to `1.0`, or `nil` if the framework hasn’t calculated the score.

var rect: CGRect

The bounding box rectangle of the tracked person’s face in the frame.

var saliencyRank: Int?

The saliency rank of the person the dock is tracking. A lower rank indicates higher importance of the person. This property is `nil` if the saliency ranking isn’t set or the person isn’t salient.

var speakingConfidence: Double?

The confidence score of the person speaking at the moment of tracking. The range is from `0.0` to `1.0`, or `nil` if the framework hasn’t calculated the score.

### Default Implementations

Equatable Implementations

## Relationships

### Conforms To

- Equatable
- Sendable

