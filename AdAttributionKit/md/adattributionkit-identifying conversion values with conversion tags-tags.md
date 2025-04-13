

- AdAttributionKit
-  Identifying conversion values with conversion tags 

Article

# Identifying conversion values with conversion tags

Use conversion tags to identify and update specific postbacks when you have overlapping conversion windows.

## Overview

AdAttributionKit supplies a conversion tag along with the reengagement URL it provides to your app when the system opens it as a result of a reengagement by someone. A conversion tag acts as a bookmark that you can supply as an argument to the update conversion value method to selectively update only the conversion corresponding to the specified conversion tag. You can use this capability, for example, to distinguish between measurements you apply to conversions that happen chronologically close to one another.

## Receive conversion tags during reengagement opens

When the system opens your app as the result of an AdAttributionKit reengagement, it supplies the conversion tag in the URL it passes to your app.

The system keys the value to the `AdAttributionKitReengagementOpen` key in the URL.

If this reengagement is of interest to you and you want to independently update it’s conversion value, persist the conversion tag along with some internal identifier to help you identify the conversion it belongs to.

Note

The internal identifier is for your own bookkeeping and has no role in the API.

## Selectively update conversion values with conversion tags

In iOS 18.4 and later, the PostbackUpdate structure can accept an optional `String` property named conversionTag during initialization.

During the flow to update the postback conversion value, initialize the PostbackUpdate structure with the requisite values and with the conversion tag of the conversion.

Call AdAttributionKit’s updateConversionValue(_:) method, passing in the PostbackUpdate instance initialized before.

If the framework finds a conversion with the specified conversion tag, it updates it with the values you specify in the PostbackUpdate instance.

Note

If you don’t specify a conversion tag, AdAttributionKit updates the most recent conversion. This is same behavior the framework implements prior to iOS 18.4.

## See Also

### Essentials

Understanding AdAttributionKit and SKAdNetwork interoperability

Learn how attribution APIs interact to deliver ad impressions.

Presenting ads in your app

Render different ad styles in your app.

Receiving ad attributions and postbacks

Understand timeframes and priorities for ad impressions that result in ad attributions, and how impressions qualify for postbacks.

