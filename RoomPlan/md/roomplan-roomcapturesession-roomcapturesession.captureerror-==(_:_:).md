

- RoomPlan
- RoomCaptureSession
- RoomCaptureSession.CaptureError
-  ==(\_:\_:) 

Operator

# ==(\_:\_:)

Determines whether two errors are equal.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+visionOS 16.0–1.0Deprecated

``` source
static func == (a: RoomCaptureSession.CaptureError, b: RoomCaptureSession.CaptureError) -> Bool
```

## Parameters 

`lhs`  

The error argument on the left-hand side of the operator.

`rhs`  

The error argument on the right-hand side of the operator.

## Return Value

`true` if the errors are equal. Otherwise, returns `false`.

## See Also

### Comparing errors

static func != (Self, Self) -> Bool

Determines whether two errors aren’t equal.

var hashValue: Int

The hash value.

func hash(into: inout Hasher)

Hashes the essential components of this value by feeding them into the given hasher.

