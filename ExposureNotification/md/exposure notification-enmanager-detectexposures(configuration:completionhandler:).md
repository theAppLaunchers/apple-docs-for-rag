

- Exposure Notification
- ENManager
-  detectExposures(configuration:completionHandler:) 

Instance Method

# detectExposures(configuration:completionHandler:)

Detects exposures using the specified configuration to control the scoring algorithm.

iOS 12.5+iPadOS 12.5+Mac Catalyst 12.5+

``` source
func detectExposures(
    configuration: ENExposureConfiguration,
    completionHandler: @escaping ENDetectExposuresHandler
) -> Progress
```

## Parameters 

`configuration`  

The exposure configuration.

`completionHandler`  

The completion handler that the framework calls when the method completes.

## Return Value

The progress of the method.

## Discussion

Important

This method is available in iOS 12.5, and in iOS 13.5 and later.

This method allows recalculating a new score using different configuration parameters. If you’ve previously called detectExposures(configuration:diagnosisKeyURLs:completionHandler:), any keys you submitted in the previous 14 days are cached. Only use this method if your app specifies an `ENAPIVersion` of `2` in its `Info.plist` file, because older versions did not cache keys.

Important

On iOS 13.6 and later, you’re limited to using this method a maximum of 15 times per 24-hour period. If you’re on iOS 13.7 and later and specify `2` as the `ENAPIVersion` in your app’s `Info.plist` file, you’re limited to using this method a maximum of 6 times per 24-hour period.

On iOS 13.5, you can only submit 15 uncached key files per 24-hour period, regardless of the number of API calls you make.

## See Also

### Obtaining Exposure Information

func detectExposures(configuration: ENExposureConfiguration, diagnosisKeyURLs: [URL], completionHandler: ENDetectExposuresHandler) -> Progress

Detects exposures using the configuration that you specify for controlling the scoring algorithm.

func getExposureWindows(summary: ENExposureDetectionSummary, completionHandler: ENGetExposureWindowsHandler) -> Progress

Obtains information from the provided summary about the user’s exposure within a window of time.

typealias ENGetExposureWindowsHandler

The handler the system invokes when the acquisition of windows completes.

func getUserTraveled(completionHandler: ENGetUserTraveledHandler)

Obtains information about the user’s travel within an exposure period.

typealias ENGetUserTraveledHandler

The handler the system invokes when acquistiion of the user’s travel status completes.

func getExposureInfo(summary: ENExposureDetectionSummary, userExplanation: String, completionHandler: ENGetExposureInfoHandler) -> Progress

Returns information about each exposure.

Deprecated

