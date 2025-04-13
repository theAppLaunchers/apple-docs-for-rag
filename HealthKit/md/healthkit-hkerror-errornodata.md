

- HealthKit
- HKError
-  errorNoData 

Type Property

# errorNoData

Data is unavailable for the requested query and predicate.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 13.0+visionOS 1.0+watchOS 7.0+

``` source
static var errorNoData: HKError.Code { get }
```

## Discussion

This error indicates that no data exists that corresponds to a particular query, so the system can’t calculate the query’s result. HKStatisticsQuery queries return this error when HealthKit can’t return the data needed to calculate the statistics.

## See Also

### Accessing errors

enum Code

Error codes returned by HealthKit.

static var noError: HKError.Code

No error occurred.

static var errorHealthDataUnavailable: HKError.Code

The user accessed HealthKit on an unsupported device.

static var errorHealthDataRestricted: HKError.Code

A Mobile Device Management (MDM) profile restricts the use of HealthKit on this device.

static var errorInvalidArgument: HKError.Code

The app passed an invalid argument to the HealthKit API.

static var errorAuthorizationDenied: HKError.Code

The user hasn’t given the app permission to save data.

static var errorAuthorizationNotDetermined: HKError.Code

The app hasn’t yet asked the user for the authorization required to complete the task.

static var errorRequiredAuthorizationDenied: HKError.Code

The user hasn’t granted the application authorization to access all the required clinical record types.

static var errorDatabaseInaccessible: HKError.Code

The HealthKit data is unavailable because it’s protected and the device is locked.

static var errorUserCanceled: HKError.Code

The user canceled the operation.

static var errorAnotherWorkoutSessionStarted: HKError.Code

Another app started a workout session.

static var errorUserExitedWorkoutSession: HKError.Code

The user exited your application while a workout session was running.

