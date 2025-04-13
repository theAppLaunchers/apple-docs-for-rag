

- PackageDescription
- SupportedPlatform
-  iOS(\_:) 

Type Method

# iOS(\_:)

Configures the minimum deployment target version for the iOS platform using a custom version string.

``` source
static func iOS(_ versionString: String) -> SupportedPlatform
```

## Parameters 

`versionString`  

The minimum deployment target as a string representation of two or three dot-separated integers, such as `8.0.1`.

## Return Value

A `SupportedPlatform` instance.

## Discussion

The version string must be a series of two or three dot-separated integers, such as `8.0` or `8.0.1`.

Since

First available in PackageDescription 5.0

## See Also

### Supporting iOS

static func iOS(SupportedPlatform.IOSVersion) -> SupportedPlatform

Configures the minimum deployment target version for the iOS platform.

static let iOS: Platform

The iOS platform.

struct IOSVersion

The supported iOS version.

