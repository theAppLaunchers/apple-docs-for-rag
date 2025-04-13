

- Foundation
- NSMeasurement
-  adding(\_:) 

Instance Method

# adding(\_:)

Returns a new measurement by adding the receiver to the specified measurement.

iOS 10.0+iPadOS 10.0+Mac Catalyst 13.1+macOS 10.12+tvOS 10.0+visionOS 1.0+watchOS 3.0+

``` source
func adding(_ measurement: Measurement) -> Measurement
```

## Parameters 

`measurement`  

The measurement to be added.

## Return Value

A new measurement with a value equal to the receiver’s value plus the value of the specified measurement converted into the unit of the receiver.

## Discussion

This method raises an invalidArgumentException if the receiver cannot be converted to unit.

You can use the canBeConverted(to:) method, passing the unit of the specified measurement, to determine whether a measurement can be converted to a particular unit before calling this method.

## See Also

### Operating on Measurements

func subtracting(Measurement&lt;Unit>) -> Measurement&lt;Unit>

Returns a new measurement by subtracting the specified measurement from the receiver.

