

- UIKit
- UIEventAttribution
-  reportEndpoint 

Instance Property

# reportEndpoint

The URL that receives attribution data.

iOS 14.5+iPadOS 14.5+Mac Catalyst 14.5+visionOS 1.0+

``` source
@MainActor
var reportEndpoint: URL? { get }
```

## Discussion

This read-only property contains the URL that recieves the event attribution data. Your app sets this value by reading it from its `Info.plist` using the NSAdvertisingAttributionReportEndpoint key.

Specify the desired value in your Xcode project’s `Info.plist` file. Your app uses the value you set in all PCM attribution requests. You can’t change the value at runtime.

This field corresponds to the `source_site` field of a web attribution.

## See Also

### Setting attribution details

var destinationURL: URL

The destination URL to attribute.

var purchaser: String

The entity that purchased the ad or content.

var sourceDescription: String

A string describing the source tapped to launch the external link.

var sourceIdentifier: UInt8

A number that identifies the source of the attribution.

