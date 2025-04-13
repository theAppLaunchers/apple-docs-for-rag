

- HealthKit
- HKWorkoutSession
-  startMirroringToCompanionDevice(completion:) 

Instance Method

# startMirroringToCompanionDevice(completion:)

Starts mirroring the workout session to the companion iOS device.

watchOS 10.0+

``` source
func startMirroringToCompanionDevice(completion: @escaping (Bool, (any Error)?) -> Void)
```

``` source
func startMirroringToCompanionDevice() async throws
```

## Parameters 

`completion`  

A block that the system calls when the start request is complete. The system sets the following parameters:

`success`  
A Boolean value that indicates whether the system successfully started mirroring the session.

`error`  
If `success` is false, this contains an object that describes the error. Otherwise, it’s `nil`.

## Discussion

Call this method in your watchOS app to start a mirrored workout session on the companion iOS app. If your iOS app isn’t running, the system launches it in the background. The iOS companion app must assign a completion handler to its HealthKit Store’s workoutSessionMirroringStartHandler property to process the incoming session.

Important

This method fails if you call it on a workout session that ended.

```
let configuration = HKWorkoutConfiguration()
configuration.activityType = .running
configuration.locationType = .outdoor

let session: HKWorkoutSession
do {
    session = try HKWorkoutSession(healthStore: store,
                                   configuration: configuration)
} catch {
    // Handle failure here.
    fatalError("*** An error occurred: \(error.localizedDescription) ***")
}

let builder = session.associatedWorkoutBuilder()

let source = HKLiveWorkoutDataSource(healthStore: store,
                                     workoutConfiguration: configuration)

source.enableCollection(for: HKQuantityType(.stepCount), predicate: nil)
builder.dataSource = source

session.delegate = self
builder.delegate = self

self.session = session
self.builder = builder

let start = Date()

// Start the mirrored session on the companion iPhone.
do {
    try await session.startMirroringToCompanionDevice()
}
catch {
    fatalError("*** Unable to start the mirrored workout: \(error.localizedDescription) ***")
}

// Start the workout session.
session.startActivity(with: start)

do {
    try await builder.beginCollection(at: start)
} catch {
    fatalError("*** An error occurred while starting the workout: \(error.localizedDescription) ***")
}
```

## See Also

### Working with remote workout sessions

func stopMirroringToCompanionDevice(completion: (Bool, (any Error)?) -> Void)

Stops mirroring the workout session to the companion iOS device.

func sendToRemoteWorkoutSession(data: Data, completion: (Bool, (any Error)?) -> Void)

Sends the provided data to the remote workout session.

