

- AVFoundation
- Media assets
- AVURLAsset
-  Initialization Options 

API Collection

# Initialization Options

Specify options to configure the initialization of a media asset.

## Topics

### Options

let AVURLAssetAllowsCellularAccessKey: String

A Boolean value that indicates whether the system can make network requests on behalf of the asset when connected to a cellular network.

let AVURLAssetAllowsConstrainedNetworkAccessKey: String

A Boolean value that indicates whether the system allows network requests on behalf of this asset to use the constrained interface.

let AVURLAssetAllowsExpensiveNetworkAccessKey: String

A Boolean value that indicates whether the system allows network requests on behalf of this asset to use the expensive interface.

let AVURLAssetHTTPCookiesKey: String

The HTTP cookies that a URL asset may send with HTTP requests.

let AVURLAssetHTTPUserAgentKey: String

A key that specifies the user agent of requests that an asset makes.

let AVURLAssetOverrideMIMETypeKey: String

A key that specifies the MIME type to use to identify the format of a media resource.

let AVURLAssetPreferPreciseDurationAndTimingKey: String

A Boolean value that indicates whether the asset should provide accurate duration and precise random access by time.

let AVURLAssetPrimarySessionIdentifierKey: String

Specifies a UUID to set as the session identifier for HTTP requests that the asset makes.

let AVURLAssetReferenceRestrictionsKey: String

A value that represents the restrictions used by the asset when resolving references to external media data.

let AVURLAssetShouldSupportAliasDataReferencesKey: String

A Boolean value that indicates whether the system parses and resolves alias data references in the asset.

let AVURLAssetURLRequestAttributionKey: String

A value that specifies the attribution of the URLs that this asset requests.

## See Also

### Creating an Asset

convenience init(url: URL)

Creates an asset that models the media at the specified URL.

init(url: URL, options: [String : Any]?)

Creates an asset that models the media resource at the specified URL.

