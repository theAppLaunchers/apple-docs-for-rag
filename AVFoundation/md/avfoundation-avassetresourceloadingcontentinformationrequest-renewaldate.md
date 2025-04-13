

- AVFoundation
- AVAssetResourceLoadingContentInformationRequest
-  renewalDate 

Instance Property

# renewalDate

The date at which a new resource loading request will be issued for resources that expire, if the media system still requires it.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+macOS 10.10+tvOS 9.0+visionOS 1.0+

``` source
var renewalDate: Date? { get set }
```

## Discussion

If the asset resource is prone to expiry set the value of this property to the date at which a renewal should be triggered. You must do this before you finish loading an AVAssetResourceLoadingRequest object. This value must be set sufficiently early enough to allow an `AVAssetResourceRenewalRequest`, delivered to the delegate’s `resourceLoader:shouldWaitForRenewalOfRequestedResource:` method ß to finish before the actual expiry time, otherwise media playback may fail.

## See Also

### Configuring Content Information

var allowedContentTypes: [String]?

The types of data that are accepted as a valid response for the requested resource.

var contentType: String?

The UTI that specifies the type of data contained by the requested resource.

var contentLength: Int64

The length, in bytes, of the requested resource.

var isByteRangeAccessSupported: Bool

A Boolean value that indicates whether random access to arbitrary ranges of bytes of the resource is supported.

var isEntireLengthAvailableOnDemand: Bool

A Boolean value that indicates whether asset data loading can expect data immediately.

