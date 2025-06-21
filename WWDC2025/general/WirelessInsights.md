Framework

# WirelessInsights

Receive notifications for anticipated changes in cellular data service conditions.

iOS 26.0+BetaiPadOS 26.0+Beta

## [Overview](/documentation/WirelessInsights#Overview)

The WirelessInsights framework notifies your app about network conditions that might affect its ability to use data. The framework collects metrics on the device about cellular conditions, such as whether the device is in service, current cellular congestion, and more. With this information, you can improve someone’s experience using your app.

When your app receives a notification about a potential degradation of cellular service, you can adapt to the problem in a number of ways:

*   Prefetch and buffer data prior to the event.
    
*   Reduce your bit rate.
    
*   Defer activity to a time when cellular conditions are better.
    
*   Build in additional retries.
    

The app receives an asynchronous sequence of [`ServicePrediction`](/documentation/wirelessinsights/serviceprediction) instances, which describe anticipated events in terms of their impact and expected timing. The prediction includes metrics indicating the level of confidence in each factor of the prediction.

Your app can take action appropriate to its use of cellular data; for example:

*   A streaming media app might react to a prediction of a lengthy, high-impact event by buffering media in advance of the event. Or, the app might proactively reduce its bit rate.
    
*   An app that performs one-time downloads of large files might defer a download until after an event passes.
    

Important

While the WirelessInsights framework exists in apps built with Mac Catalyst, it doesn’t have any functionality. Instead, iterating over the [`servicePredictions`](/documentation/wirelessinsights/servicepredictionprovider/servicepredictions) sequence throws a [`ServicePredictionError.unsupportedDevice`](/documentation/wirelessinsights/servicepredictionerror/unsupporteddevice) error. This behavior also occurs in iOS apps running in visionOS or in macOS on Apple silicon. On iPad, the framework may provide predictions on a cellular iPad device, but not on Wi-Fi-only devices. Anticipate this error in your app and handle it gracefully on unsupported devices.

## [Topics](/documentation/WirelessInsights#topics)

### [Essentials](/documentation/WirelessInsights#Essentials)

```swift
```swift
```swift
```swift
class ServicePredictionProvider
```
```

A class that provices cellular service predictions about upcoming events and anomalies.
```

[`Wireless Insights Service Predictions`](/documentation/BundleResources/Entitlements/com.apple.developer.wireless-insights.service-predictions)

A Boolean value that indicates whether the app can use the WirelessInsights framework to obtain wireless service predictions.
```

Beta Software

This documentation contains preliminary information about an API or technology in development. This information is subject to change, and software implemented according to this documentation should be tested with final operating system software.

[Learn more about using Apple's beta software](https://developer.apple.com/support/beta-software/)