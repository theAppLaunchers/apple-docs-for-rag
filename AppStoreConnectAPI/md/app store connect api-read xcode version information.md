

- App Store Connect API
-  Read Xcode Version Information 

Web Service Endpoint

# Read Xcode Version Information

Get information about a specific Xcode version that’s available to Xcode Cloud workflows.

App Store Connect API 1.5+

## URL

``` source
GET https://api.appstoreconnect.apple.com/v1/ciXcodeVersions/{id}
```

## Path Parameters

`id`

`string`

 (Required) 

The opaque resource ID that uniquely identifies the Xcode Versions resource.

## Query Parameters

`fields[ciXcodeVersions]`

`[string]`

Additional fields to include for the Xcode Versions resource returned by the response.

Possible Values: `version, name, testDestinations, macOsVersions`

`include`

`[string]`

The relationship data to include in the response.

Value: `macOsVersions`

`limit[macOsVersions]`

`integer`

The number of included Xcode Versions resources to return if the macOS versions relationship is included.

Maximum: `50`

`fields[ciMacOsVersions]`

`[string]`

Additional fields to include for the Xcode Versions resource returned by the response.

Possible Values: `version, name, xcodeVersions`

## Response Codes

` 200 ``OK`

CiXcodeVersionResponse

`OK`

The request completed successfully.

Content-Type: application/json

` 400 ``Bad Request`

ErrorResponse

`Bad Request`

An error occurred with your request.

Content-Type: application/json

` 401 ``Unauthorized`

ErrorResponse

`Unauthorized`

Content-Type: application/json

` 403 ``Forbidden`

ErrorResponse

`Forbidden`

Request not authorized.

Content-Type: application/json

` 404 ``Not Found`

ErrorResponse

`Not Found`

Resource not found.

Content-Type: application/json

## Discussion

The example request below accesses detailed information for a specific Xcode version available to Xcode Cloud workflows. Use the data provided in the response to display available Xcode versions and test destinations on a dashboard or to read additional information; for example, macOS version information.

### Example Request and Response

- Request
- Response

```
GET https://api.appstoreconnect.apple.com/v1/ciXcodeVersions/Xcode12E507:stable
```

```
{
    "data": {
        "type": "ciXcodeVersions",
        "id": "Xcode12E507:stable",
        "attributes": {
            "version": "Xcode12E507:stable",
            "name": "Xcode 12.5.1 (12E507)",
            "testDestinations": [
                {
                    "deviceTypeName": "iPhone 8",
                    "deviceTypeIdentifier": "com.apple.CoreSimulator.SimDeviceType.iPhone-8",
                    "availableRuntimes": [
                        {
                            "runtimeName": "iOS 13.0",
                            "runtimeIdentifier": "com.apple.CoreSimulator.SimRuntime.iOS-13-0"
                        }
                    ],
                    "kind": "SIMULATOR"
                },
                {
                    "deviceTypeName": "Mac",
                    "deviceTypeIdentifier": "mac",
                    "availableRuntimes": [
                        {
                            "runtimeName": "Same as Selected macOS Version",
                            "runtimeIdentifier": "builder"
                        },
                        {
                            "runtimeName": "Latest Beta or Release (Currently macOS Big Sur 11.5.2 (20G95))",
                            "runtimeIdentifier": "latest:all"
                        },
                        {
                            "runtimeName": "macOS Big Sur 11.5.2 (20G95)",
                            "runtimeIdentifier": "20G95"
                        }
                    ],
                    "kind": "MAC"
                },
                {
                    "deviceTypeName": "Mac (Mac Catalyst)",
                    "deviceTypeIdentifier": "mac_catalyst",
                    "availableRuntimes": [
                        {
                            "runtimeName": "Same as Selected macOS Version",
                            "runtimeIdentifier": "builder"
                        },
                        {
                            "runtimeName": "Latest Beta or Release (Currently macOS Big Sur 11.5.2 (20G95))",
                            "runtimeIdentifier": "latest:all"
                        },
                        {
                            "runtimeName": "macOS Big Sur 11.5.2 (20G95)",
                            "runtimeIdentifier": "20G95"
                        }
                    ],
                    "kind": "MAC"
                }
            ]
        },
        "relationships": {
            "macOsVersions": {
                "links": {
                    "self": "https://api.appstoreconnect.apple.com/v1/ciXcodeVersions/Xcode12E507:stable/relationships/macOsVersions",
                    "related": "https://api.appstoreconnect.apple.com/v1/ciXcodeVersions/Xcode12E507:stable/macOsVersions"
                }
            }
        },
        "links": {
            "self": "https://api.appstoreconnect.apple.com/v1/ciXcodeVersions/Xcode12E507:stable"
        }
    },
    "links": {
        "self": "https://api.appstoreconnect.apple.com/v1/ciXcodeVersions/Xcode12E507:stable"
    }
}
```

## See Also

### Getting Xcode Version Information

List All Xcode Versions Available in Xcode Cloud

List all Xcode versions that are available to Xcode Cloud workflows.

List Available macOS Versions for an Xcode Version

List all macOS versions available in Xcode Cloud that support a specific Xcode version.

