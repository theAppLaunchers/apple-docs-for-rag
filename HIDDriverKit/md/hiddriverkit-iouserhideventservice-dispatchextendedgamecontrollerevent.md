

- HIDDriverKit
- IOUserHIDEventService
-  dispatchExtendedGameControllerEvent 

Instance Method

# dispatchExtendedGameControllerEvent

DriverKit 22.0–23.0DeprecatedmacOS

``` source
kern_return_t dispatchExtendedGameControllerEvent(uint64_t timeStamp, IOFixed dpadUp, IOFixed dpadDown, IOFixed dpadLeft, IOFixed dpadRight, IOFixed faceX, IOFixed faceY, IOFixed faceA, IOFixed faceB, IOFixed shoulderL1, IOFixed shoulderR1, IOFixed shoulderL2, IOFixed shoulderR2, IOFixed joystickX, IOFixed joystickY, IOFixed joystickZ, IOFixed joystickRz, bool thumbstickButtonLeft, bool thumbstickButtonRight, IOFixed buttonL4, IOFixed buttonR4, IOFixed buttonL5, IOFixed buttonR5, IOOptionBits options);
```

