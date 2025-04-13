

- HealthKit
- HKContactsLensSpecification
-  init(sphere:cylinder:axis:addPower:baseCurve:diameter:) 

Initializer

# init(sphere:cylinder:axis:addPower:baseCurve:diameter:)

Creates a new contact lens specification, containing the prescription data for one eye.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+visionOS 1.0+watchOS 9.0+

``` source
init(
    sphere: HKQuantity,
    cylinder: HKQuantity?,
    axis: HKQuantity?,
    addPower: HKQuantity?,
    baseCurve: HKQuantity?,
    diameter: HKQuantity?
)
```

## Parameters 

`sphere`  

The correction for farsightedness, measured in diopter() units. The range is -10.5 to +6.5.

`cylinder`  

Part of the correction for astigmatism. This property measures the strength of the correction in diopter() units. The range is -3.0 to 3.0.

`axis`  

Part of the correction for astigmatism. This property measures the orientation of the correction in degreeAngle() units.

`addPower`  

The correction for nearsightedness, measured in diopter() units. The range is from 0.25 to 2.5. The right and left eyes should have the same value.

`baseCurve`  

Part of the contact’s fit, it measures the curve of the back side of the contact, measured in mm. The range is 7.8 to 9.2 mm.

`diameter`  

Part of the contact’s fit, it measures the diameter of the lens, measured in mm. The range is 9 to 15 mm.

