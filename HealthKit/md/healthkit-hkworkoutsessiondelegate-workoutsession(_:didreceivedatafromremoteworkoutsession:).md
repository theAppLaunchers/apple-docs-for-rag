

- HealthKit
- HKWorkoutSessionDelegate
-  workoutSession(\_:didReceiveDataFromRemoteWorkoutSession:) 

Instance Method

# workoutSession(\_:didReceiveDataFromRemoteWorkoutSession:)

Passes data from the remote workout session to the session delegate.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 10.10+visionOS 1.0+watchOS 10.0+

``` source
optional func workoutSession(
    _ workoutSession: HKWorkoutSession,
    didReceiveDataFromRemoteWorkoutSession data: [Data]
)
```

## Parameters 

`workoutSession`  

The workout session that received the data.

`data`  

An array of data objects sent from the remote session. The array contains the data objects in the order the system received them.

## Discussion

Implement this method to decode and use the data sent from the remote workout session. Your app can send data from either the HKWorkoutSessionType.mirrored or HKWorkoutSessionType.primary workout session.

```
nonisolated func workoutSession(_ workoutSession: HKWorkoutSession, didReceiveDataFromRemoteWorkoutSession data: [Data]) {
    for archivedData in data {
        do {
            let decoder = try NSKeyedUnarchiver(forReadingFrom: archivedData)
            if let healthData = decoder.decodeObject() as? HealthData {
                Task {
                    await set(data: healthData)
                }
            }
        }
        catch {
            // Handle the error here.
            fatalError("*** An error occurred when trying to decode the incoming data: \(archivedData) ***")
        }
    }
}
```

In iOS, your app can go into the background and become suspended. When suspended, HealthKit gathers the data coming from the remote session. When the app resumes, HealthKit sends an array containing all the  data objects it has accumulated to this delegate method. The data objects in the array appear in the order that the local system received them. During the workout session, HealthKit wakes the iOS app periodically to deliver any cached data objects, but there might be several minutes between delegate calls.

On watchOS, the workout session keeps the app running even if it’s in the background; however, the system can temporarily suspend the app — for example, if the app uses an excessive amount of CPU in the background. See Running workout sessions. While suspended, HealthKit caches the incoming data objects and delivers an array of data objects when the app resumes, just like in the iOS app.

## See Also

### Working with mirrored sessions

func workoutSession(HKWorkoutSession, didDisconnectFromRemoteDeviceWithError: (any Error)?)

Tells the delegate that the mirrored workout session disconnected from the primary session.

