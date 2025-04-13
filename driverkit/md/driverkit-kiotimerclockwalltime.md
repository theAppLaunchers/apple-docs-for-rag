

- DriverKit
-  kIOTimerClockWallTime 

Enumeration Case

# kIOTimerClockWallTime

The system’s wall-clock time, expressed as the amount of time since the Epoch.

DriverKitiOSiPadOSmacOS

``` source
kIOTimerClockWallTime
```

## Discussion

This constant is the type of clock obtained by passing `CLOCK_UPTIME_RAW` to `clock_gettime_nsec_np(_:)`. It’s equivalent to a value from `mach_absolute_time()`, but in nanoseconds.

## See Also

### Timer Options

kIOTimerClockUptimeRaw

A clock type that increments monotonically, but does not increment when the system is asleep.

kIOTimerClockMonotonicRaw

A clock type that increments monotonically, and is unaffected by frequency or time adjustmets.

kIOTimerClockRealTime

The system’s real time, expressed as the amount of time since the Epoch.

kIOTimerClockMachAbsoluteTime

A clock type representing the numer of ticks since the last reboot.

kIOTimerClockMachContinuousTime

A clock type representing the number of ticks since the last reboot, including when the computer is asleep.

