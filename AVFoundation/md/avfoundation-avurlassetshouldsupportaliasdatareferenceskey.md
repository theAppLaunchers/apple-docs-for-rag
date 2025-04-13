

- AVFoundation
-  AVURLAssetShouldSupportAliasDataReferencesKey 

Global Variable

# AVURLAssetShouldSupportAliasDataReferencesKey

A Boolean value that indicates whether the system parses and resolves alias data references in the asset.

macOS 10.10+

``` source
let AVURLAssetShouldSupportAliasDataReferencesKey: String
```

## Discussion

Most QuickTime movie files contain all of the media data they require, but some contain references to media in other files. While AVFoundation and CoreMedia typically employ a URL reference for this purpose, older implementations commonly use a Macintosh alias instead, as the QuickTime File Format specification documents. Specify this option if your app must work with legacy QuickTime movie files that contain alias-based references to media data in other files.

If you provide a value for AVURLAssetReferenceRestrictionsKey, the system observes restrictions for resolved alias references like it does for URL references.

## See Also

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

let AVURLAssetURLRequestAttributionKey: String

A value that specifies the attribution of the URLs that this asset requests.

