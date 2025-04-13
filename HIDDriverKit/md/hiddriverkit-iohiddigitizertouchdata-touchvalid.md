

- HIDDriverKit
- IOHIDDigitizerTouchData
-  touchValid 

Instance Property

# touchValid

A single-bit Boolean that indicates whether the touch contact was intended.

DriverKitmacOS

``` source
uint32_t touchValid;
```

## Discussion

The device should report `0` if the contact isn’t a valid touch.

## See Also

### Getting the Touch Data

identifier

A unique contact identifier.

x

An x-coordinate value in the range `0.0` to `1.0`.

y

A y-coordinate value in the range `0.0` to `1.0`.

inRange

A single-bit Boolean that indicates whether the finger is in range.

touch

A single-bit Boolean that indicates whether the finger is in contact with the surface of the digitizer.

touchChanged

A single-bit Boolean that indicates whether the touch variable changed since the last event was dispatched.

positionChanged

A single-bit Boolean that indicates whether the x or y position changed since the last event was dispatched.

rangeChanged

A single-bit Boolean that indicates whether the range variable changed since the last event was dispatched.

