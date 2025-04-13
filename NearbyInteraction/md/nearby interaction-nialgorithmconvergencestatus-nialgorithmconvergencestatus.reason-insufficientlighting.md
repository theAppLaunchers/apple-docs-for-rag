

- Nearby Interaction
- NIAlgorithmConvergenceStatus
- NIAlgorithmConvergenceStatus.Reason
-  insufficientLighting 

Type Property

# insufficientLighting

Indicates that the camera needs to view the physical environment under better lighting conditions.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+watchOS 9.0+

``` source
static let insufficientLighting: NIAlgorithmConvergenceStatus.Reason
```

## Discussion

Coach the user to resolve the issue, such as by presenting text that asks the user to turn on the lights.

This reason prevents a nearby object from providing a horizontalAngle and verticalDirectionEstimate.

## See Also

### Interpreting the convergence status reason

static let insufficientMovement: NIAlgorithmConvergenceStatus.Reason

Indicates that the device needs to move from its current position in the physical environment.

static let insufficientHorizontalSweep: NIAlgorithmConvergenceStatus.Reason

Indicates that the device needs more horizontal motion.

static let insufficientVerticalSweep: NIAlgorithmConvergenceStatus.Reason

Indicates that the device needs more vertical motion.

static let insufficientSignalStrength: NIAlgorithmConvergenceStatus.Reason

Indicates that the users might be too far apart.

