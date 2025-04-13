

- HIDDriverKit
- IOUserHIDEventService
-  dispatchExtendedGameControllerEventWithOptionalButtons 

Instance Method

# dispatchExtendedGameControllerEventWithOptionalButtons

DriverKit 23.0+macOS

``` source
kern_return_t dispatchExtendedGameControllerEventWithOptionalButtons(uint64_t timeStamp, IOFixed dpadUp, IOFixed dpadDown, IOFixed dpadLeft, IOFixed dpadRight, IOFixed faceX, IOFixed faceY, IOFixed faceA, IOFixed faceB, IOFixed shoulderL1, IOFixed shoulderR1, IOFixed shoulderL2, IOFixed shoulderR2, IOFixed joystickX, IOFixed joystickY, IOFixed joystickZ, IOFixed joystickRz, bool thumbstickButtonLeft, bool thumbstickButtonRight, IOFixed shoulderL4, IOFixed shoulderR4, IOFixed bottomM1, IOFixed bottomM2, IOFixed bottomM3, IOFixed bottomM4, IOOptionBits options);
```

