

- HealthKit
- HKHealthStore
-  enableBackgroundDelivery(for:frequency:withCompletion:) 

Instance Method

# enableBackgroundDelivery(for:frequency:withCompletion:)

Enables the delivery of updates to an app running in the background.

iOSiPadOSMac Catalyst 13.0+macOS 13.0+visionOSwatchOS 8.0+

``` source
func enableBackgroundDelivery(
    for type: HKObjectType,
    frequency: HKUpdateFrequency,
    withCompletion completion: @escaping (Bool, (any Error)?) -> Void
)
```

``` source
func enableBackgroundDelivery(
    for type: HKObjectType,
    frequency: HKUpdateFrequency
) async throws
```

## Parameters 

`type`  

The type of data to observe. This object can be any concrete subclass of the HKObjectType class (such as HKCharacteristicType , HKQuantityType, HKCategoryType, HKWorkoutType, or HKCorrelationType).

`frequency`  

The maximum frequency of the updates. The system wakes your app from the background at most once per time period specified. For a complete list of valid frequencies, see HKUpdateFrequency.

`completion`  

A block that this method calls as soon as it enables background delivery. It passes the following parameters:

`success`  
A Boolean value. This parameter contains true if the system successfully enabled background delivery; otherwise, false.

`error`  
An error object. If an error occurred, this object contains information about the error; otherwise, it is `nil`.

## Mentioned in 

Executing Observer Queries

## Discussion

Call this method to register your app for background updates.

Important

For iOS 15 and watchOS 8 and later, you must enable the HealthKit Background Delivery by adding the com.apple.developer.healthkit.background-delivery entitlement to your app. If your app doesn’t have this entitlement, the enableBackgroundDelivery(for:frequency:withCompletion:) method fails with an HKError.Code.errorAuthorizationDenied error.

HealthKit wakes your app whenever a process saves or deletes samples of the specified type. The system wakes your app at most once per time period defined by the specified frequency. Some sample types have a maximum frequency of HKUpdateFrequency.hourly. The system enforces this frequency transparently.

For example, on iOS, stepCount samples have an hourly maximum frequency.

In watchOS, most data types have an hourly maximum frequency; however, the following data types can receive updates at HKUpdateFrequency.immediate:

- highHeartRateEvent

- lowHeartRateEvent

- irregularHeartRhythmEvent

- environmentalAudioExposureEvent

- headphoneAudioExposureEvent

- lowCardioFitnessEvent

- numberOfTimesFallen

- vo2Max

- handwashingEvent

- toothbrushingEvent

Also, in watchOS, the background updates share a budget with WKApplicationRefreshBackgroundTask tasks. Your app can receive four updates (or background app refresh tasks) an hour, as long as it has a complication on the active watch face.

Important

Background server queries aren’t supported on the Simulator. Be sure to test your background queries on a device.

### Receive Background Updates

As soon as your app launches, HealthKit calls the update handler for any observer queries that match the newly saved data. If you plan on supporting background delivery, set up all your observer queries in your app delegate’s application(_:didFinishLaunchingWithOptions:) method. By setting up the queries in application(_:didFinishLaunchingWithOptions:), you ensure that you’ve instantiated your queries, and they’re ready to use before HealthKit delivers the updates.

After your observer queries have finished processing the new data, you must call the update’s completion handler. This lets HealthKit know that your app successfully received the background delivery. If you don’t call the update’s completion handler, HealthKit continues to attempt to launch your app using a backoff algorithm to increase the delay between attempts. If your app fails to respond three times, HealthKit assumes your app can’t receive data and stops sending background updates.

For more information on the background delivery completion handler, see HKObserverQueryCompletionHandler.

## See Also

### Related Documentation

class HKObserverQuery

A long-running query that monitors the HealthKit store and updates your app when the HealthKit store saves or deletes a matching sample.

### Managing background delivery

com.apple.developer.healthkit.background-delivery

A Boolean value that indicates whether observer queries receive updates while running in the background.

enum HKUpdateFrequency

Constants that determine how often the system launches your app in response to changes to HealthKit data.

func disableBackgroundDelivery(for: HKObjectType, withCompletion: (Bool, (any Error)?) -> Void)

Disables background deliveries of update notifications for the specified data type.

func disableAllBackgroundDelivery(completion: (Bool, (any Error)?) -> Void)

Disables all background deliveries of update notifications.

