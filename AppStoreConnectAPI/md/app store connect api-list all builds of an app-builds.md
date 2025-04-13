

- App Store Connect API
-  List All Builds of an App 

Web Service Endpoint

# List All Builds of an App

Get a list of builds associated with a specific app.

App Store Connect API 1.0+

## URL

``` source
GET https://api.appstoreconnect.apple.com/v1/apps/{id}/builds
```

## Path Parameters

`id`

`string`

 (Required) 

An opaque resource ID that uniquely identifies the resource. Obtain the app resource ID from the List Apps response.

## Query Parameters

`fields[builds]`

`[string]`

Fields to return for included related types.

Possible Values: `version, uploadedDate, expirationDate, expired, minOsVersion, lsMinimumSystemVersion, computedMinMacOsVersion, iconAssetToken, processingState, buildAudienceType, usesNonExemptEncryption, preReleaseVersion, individualTesters, betaGroups, betaBuildLocalizations, appEncryptionDeclaration, betaAppReviewSubmission, app, buildBetaDetail, appStoreVersion, icons, buildBundles, perfPowerMetrics, diagnosticSignatures`

`limit`

`integer`

Number of resources to return.

Maximum: `200`

## Response Codes

` 200 ``OK`

BuildsWithoutIncludesResponse

`OK`

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

### Example Request and Response

- Request
- Response

```
https://api.appstoreconnect.apple.com/v1/apps/6446998023/builds
```

```
{
  "data": [
    {
      "type": "builds",
      "id": "b3149f9a-100d-4af7-a771-cef5507a0499",
      "attributes": {
        "version": "1",
        "uploadedDate": "2022-09-07T10:42:15-07:00",
        "expirationDate": "2022-12-06T10:42:15-08:00",
        "expired": false,
        "minOsVersion": "15.5",
        "lsMinimumSystemVersion": null,
        "computedMinMacOsVersion": "12.4",
        "iconAssetToken": {
          "templateUrl": "https://isq11.mzstatic.com/image/thumb/Purple123/v4/fb/4d/c2/fb4dc243-7048-8939-ac1c-0e1819c6e723/Icon-83.5@2x.png.png/{w}x{h}bb.{f}",
          "width": 167,
          "height": 167
        },
        "processingState": "VALID",
        "buildAudienceType": "APP_STORE_ELIGIBLE",
        "usesNonExemptEncryption": false
      },
      "relationships": {
        "preReleaseVersion": {
          "links": {
            "self": "https://api.appstoreconnect.apple.com/v1/builds/b3149f9a-100d-4af7-a771-cef5507a0499/relationships/preReleaseVersion",
            "related": "https://api.appstoreconnect.apple.com/v1/builds/b3149f9a-100d-4af7-a771-cef5507a0499/preReleaseVersion"
          }
        },
        "individualTesters": {
          "links": {
            "self": "https://api.appstoreconnect.apple.com/v1/builds/b3149f9a-100d-4af7-a771-cef5507a0499/relationships/individualTesters",
            "related": "https://api.appstoreconnect.apple.com/v1/builds/b3149f9a-100d-4af7-a771-cef5507a0499/individualTesters"
          }
        },
        "betaGroups": {
          "links": {
            "self": "https://api.appstoreconnect.apple.com/v1/builds/b3149f9a-100d-4af7-a771-cef5507a0499/relationships/betaGroups"
          }
        },
        "betaBuildLocalizations": {
          "links": {
            "self": "https://api.appstoreconnect.apple.com/v1/builds/b3149f9a-100d-4af7-a771-cef5507a0499/relationships/betaBuildLocalizations",
            "related": "https://api.appstoreconnect.apple.com/v1/builds/b3149f9a-100d-4af7-a771-cef5507a0499/betaBuildLocalizations"
          }
        },
        "appEncryptionDeclaration": {
          "links": {
            "self": "https://api.appstoreconnect.apple.com/v1/builds/b3149f9a-100d-4af7-a771-cef5507a0499/relationships/appEncryptionDeclaration",
            "related": "https://api.appstoreconnect.apple.com/v1/builds/b3149f9a-100d-4af7-a771-cef5507a0499/appEncryptionDeclaration"
          }
        },
        "betaAppReviewSubmission": {
          "links": {
            "self": "https://api.appstoreconnect.apple.com/v1/builds/b3149f9a-100d-4af7-a771-cef5507a0499/relationships/betaAppReviewSubmission",
            "related": "https://api.appstoreconnect.apple.com/v1/builds/b3149f9a-100d-4af7-a771-cef5507a0499/betaAppReviewSubmission"
          }
        },
        "app": {
          "links": {
            "self": "https://api.appstoreconnect.apple.com/v1/builds/b3149f9a-100d-4af7-a771-cef5507a0499/relationships/app",
            "related": "https://api.appstoreconnect.apple.com/v1/builds/b3149f9a-100d-4af7-a771-cef5507a0499/app"
          }
        },
        "buildBetaDetail": {
          "links": {
            "self": "https://api.appstoreconnect.apple.com/v1/builds/b3149f9a-100d-4af7-a771-cef5507a0499/relationships/buildBetaDetail",
            "related": "https://api.appstoreconnect.apple.com/v1/builds/b3149f9a-100d-4af7-a771-cef5507a0499/buildBetaDetail"
          }
        },
        "appStoreVersion": {
          "links": {
            "self": "https://api.appstoreconnect.apple.com/v1/builds/b3149f9a-100d-4af7-a771-cef5507a0499/relationships/appStoreVersion",
            "related": "https://api.appstoreconnect.apple.com/v1/builds/b3149f9a-100d-4af7-a771-cef5507a0499/appStoreVersion"
          }
        },
        "icons": {
          "links": {
            "self": "https://api.appstoreconnect.apple.com/v1/builds/b3149f9a-100d-4af7-a771-cef5507a0499/relationships/icons",
            "related": "https://api.appstoreconnect.apple.com/v1/builds/b3149f9a-100d-4af7-a771-cef5507a0499/icons"
          }
        },
        "perfPowerMetrics": {
          "links": {
            "related": "https://api.appstoreconnect.apple.com/v1/builds/b3149f9a-100d-4af7-a771-cef5507a0499/perfPowerMetrics"
          }
        },
        "diagnosticSignatures": {
          "links": {
            "self": "https://api.appstoreconnect.apple.com/v1/builds/b3149f9a-100d-4af7-a771-cef5507a0499/relationships/diagnosticSignatures",
            "related": "https://api.appstoreconnect.apple.com/v1/builds/b3149f9a-100d-4af7-a771-cef5507a0499/diagnosticSignatures"
          }
        }
      },
      "links": {
        "self": "https://api.appstoreconnect.apple.com/v1/builds/b3149f9a-100d-4af7-a771-cef5507a0499"
      }
    },
    {
      "type": "builds",
      "id": "e3d564dc-acff-468d-8cb5-0fc196c56dda",
      "attributes": {
        "version": "1",
        "uploadedDate": "2022-09-07T10:23:45-07:00",
        "expirationDate": "2022-12-06T10:23:45-08:00",
        "expired": false,
        "minOsVersion": "15.5",
        "lsMinimumSystemVersion": null,
        "computedMinMacOsVersion": "12.4",
        "iconAssetToken": {
          "templateUrl": "https://isq11.mzstatic.com/image/thumb/Purple123/v4/97/9b/62/979b62fb-df95-39cb-c2b9-45ee6aa0b707/Icon-83.5@2x.png.png/{w}x{h}bb.{f}",
          "width": 167,
          "height": 167
        },
        "processingState": "VALID",
        "buildAudienceType": "APP_STORE_ELIGIBLE",
        "usesNonExemptEncryption": false
      },
      "relationships": {
        "preReleaseVersion": {
          "links": {
            "self": "https://api.appstoreconnect.apple.com/v1/builds/e3d564dc-acff-468d-8cb5-0fc196c56dda/relationships/preReleaseVersion",
            "related": "https://api.appstoreconnect.apple.com/v1/builds/e3d564dc-acff-468d-8cb5-0fc196c56dda/preReleaseVersion"
          }
        },
        "individualTesters": {
          "links": {
            "self": "https://api.appstoreconnect.apple.com/v1/builds/e3d564dc-acff-468d-8cb5-0fc196c56dda/relationships/individualTesters",
            "related": "https://api.appstoreconnect.apple.com/v1/builds/e3d564dc-acff-468d-8cb5-0fc196c56dda/individualTesters"
          }
        },
        "betaGroups": {
          "links": {
            "self": "https://api.appstoreconnect.apple.com/v1/builds/e3d564dc-acff-468d-8cb5-0fc196c56dda/relationships/betaGroups"
          }
        },
        "betaBuildLocalizations": {
          "links": {
            "self": "https://api.appstoreconnect.apple.com/v1/builds/e3d564dc-acff-468d-8cb5-0fc196c56dda/relationships/betaBuildLocalizations",
            "related": "https://api.appstoreconnect.apple.com/v1/builds/e3d564dc-acff-468d-8cb5-0fc196c56dda/betaBuildLocalizations"
          }
        },
        "appEncryptionDeclaration": {
          "links": {
            "self": "https://api.appstoreconnect.apple.com/v1/builds/e3d564dc-acff-468d-8cb5-0fc196c56dda/relationships/appEncryptionDeclaration",
            "related": "https://api.appstoreconnect.apple.com/v1/builds/e3d564dc-acff-468d-8cb5-0fc196c56dda/appEncryptionDeclaration"
          }
        },
        "betaAppReviewSubmission": {
          "links": {
            "self": "https://api.appstoreconnect.apple.com/v1/builds/e3d564dc-acff-468d-8cb5-0fc196c56dda/relationships/betaAppReviewSubmission",
            "related": "https://api.appstoreconnect.apple.com/v1/builds/e3d564dc-acff-468d-8cb5-0fc196c56dda/betaAppReviewSubmission"
          }
        },
        "app": {
          "links": {
            "self": "https://api.appstoreconnect.apple.com/v1/builds/e3d564dc-acff-468d-8cb5-0fc196c56dda/relationships/app",
            "related": "https://api.appstoreconnect.apple.com/v1/builds/e3d564dc-acff-468d-8cb5-0fc196c56dda/app"
          }
        },
        "buildBetaDetail": {
          "links": {
            "self": "https://api.appstoreconnect.apple.com/v1/builds/e3d564dc-acff-468d-8cb5-0fc196c56dda/relationships/buildBetaDetail",
            "related": "https://api.appstoreconnect.apple.com/v1/builds/e3d564dc-acff-468d-8cb5-0fc196c56dda/buildBetaDetail"
          }
        },
        "appStoreVersion": {
          "links": {
            "self": "https://api.appstoreconnect.apple.com/v1/builds/e3d564dc-acff-468d-8cb5-0fc196c56dda/relationships/appStoreVersion",
            "related": "https://api.appstoreconnect.apple.com/v1/builds/e3d564dc-acff-468d-8cb5-0fc196c56dda/appStoreVersion"
          }
        },
        "icons": {
          "links": {
            "self": "https://api.appstoreconnect.apple.com/v1/builds/e3d564dc-acff-468d-8cb5-0fc196c56dda/relationships/icons",
            "related": "https://api.appstoreconnect.apple.com/v1/builds/e3d564dc-acff-468d-8cb5-0fc196c56dda/icons"
          }
        },
        "perfPowerMetrics": {
          "links": {
            "related": "https://api.appstoreconnect.apple.com/v1/builds/e3d564dc-acff-468d-8cb5-0fc196c56dda/perfPowerMetrics"
          }
        },
        "diagnosticSignatures": {
          "links": {
            "self": "https://api.appstoreconnect.apple.com/v1/builds/e3d564dc-acff-468d-8cb5-0fc196c56dda/relationships/diagnosticSignatures",
            "related": "https://api.appstoreconnect.apple.com/v1/builds/e3d564dc-acff-468d-8cb5-0fc196c56dda/diagnosticSignatures"
          }
        }
      },
      "links": {
        "self": "https://api.appstoreconnect.apple.com/v1/builds/e3d564dc-acff-468d-8cb5-0fc196c56dda"
      }
    },
    {
      "type": "builds",
      "id": "3f3a24e2-ae3b-4c39-8dd0-3fe46c69bb15",
      "attributes": {
        "version": "1",
        "uploadedDate": "2022-09-07T10:24:58-07:00",
        "expirationDate": "2022-12-06T10:24:58-08:00",
        "expired": false,
        "minOsVersion": "15.5",
        "lsMinimumSystemVersion": null,
        "computedMinMacOsVersion": "12.4",
        "iconAssetToken": {
          "templateUrl": "https://isq11.mzstatic.com/image/thumb/Purple113/v4/04/ac/0b/04ac0b6f-fa09-a354-80f3-ecf74ed38059/Icon-83.5@2x.png.png/{w}x{h}bb.{f}",
          "width": 167,
          "height": 167
        },
        "processingState": "VALID",
        "buildAudienceType": "APP_STORE_ELIGIBLE",
        "usesNonExemptEncryption": false
      },
      "relationships": {
        "preReleaseVersion": {
          "links": {
            "self": "https://api.appstoreconnect.apple.com/v1/builds/3f3a24e2-ae3b-4c39-8dd0-3fe46c69bb15/relationships/preReleaseVersion",
            "related": "https://api.appstoreconnect.apple.com/v1/builds/3f3a24e2-ae3b-4c39-8dd0-3fe46c69bb15/preReleaseVersion"
          }
        },
        "individualTesters": {
          "links": {
            "self": "https://api.appstoreconnect.apple.com/v1/builds/3f3a24e2-ae3b-4c39-8dd0-3fe46c69bb15/relationships/individualTesters",
            "related": "https://api.appstoreconnect.apple.com/v1/builds/3f3a24e2-ae3b-4c39-8dd0-3fe46c69bb15/individualTesters"
          }
        },
        "betaGroups": {
          "links": {
            "self": "https://api.appstoreconnect.apple.com/v1/builds/3f3a24e2-ae3b-4c39-8dd0-3fe46c69bb15/relationships/betaGroups"
          }
        },
        "betaBuildLocalizations": {
          "links": {
            "self": "https://api.appstoreconnect.apple.com/v1/builds/3f3a24e2-ae3b-4c39-8dd0-3fe46c69bb15/relationships/betaBuildLocalizations",
            "related": "https://api.appstoreconnect.apple.com/v1/builds/3f3a24e2-ae3b-4c39-8dd0-3fe46c69bb15/betaBuildLocalizations"
          }
        },
        "appEncryptionDeclaration": {
          "links": {
            "self": "https://api.appstoreconnect.apple.com/v1/builds/3f3a24e2-ae3b-4c39-8dd0-3fe46c69bb15/relationships/appEncryptionDeclaration",
            "related": "https://api.appstoreconnect.apple.com/v1/builds/3f3a24e2-ae3b-4c39-8dd0-3fe46c69bb15/appEncryptionDeclaration"
          }
        },
        "betaAppReviewSubmission": {
          "links": {
            "self": "https://api.appstoreconnect.apple.com/v1/builds/3f3a24e2-ae3b-4c39-8dd0-3fe46c69bb15/relationships/betaAppReviewSubmission",
            "related": "https://api.appstoreconnect.apple.com/v1/builds/3f3a24e2-ae3b-4c39-8dd0-3fe46c69bb15/betaAppReviewSubmission"
          }
        },
        "app": {
          "links": {
            "self": "https://api.appstoreconnect.apple.com/v1/builds/3f3a24e2-ae3b-4c39-8dd0-3fe46c69bb15/relationships/app",
            "related": "https://api.appstoreconnect.apple.com/v1/builds/3f3a24e2-ae3b-4c39-8dd0-3fe46c69bb15/app"
          }
        },
        "buildBetaDetail": {
          "links": {
            "self": "https://api.appstoreconnect.apple.com/v1/builds/3f3a24e2-ae3b-4c39-8dd0-3fe46c69bb15/relationships/buildBetaDetail",
            "related": "https://api.appstoreconnect.apple.com/v1/builds/3f3a24e2-ae3b-4c39-8dd0-3fe46c69bb15/buildBetaDetail"
          }
        },
        "appStoreVersion": {
          "links": {
            "self": "https://api.appstoreconnect.apple.com/v1/builds/3f3a24e2-ae3b-4c39-8dd0-3fe46c69bb15/relationships/appStoreVersion",
            "related": "https://api.appstoreconnect.apple.com/v1/builds/3f3a24e2-ae3b-4c39-8dd0-3fe46c69bb15/appStoreVersion"
          }
        },
        "icons": {
          "links": {
            "self": "https://api.appstoreconnect.apple.com/v1/builds/3f3a24e2-ae3b-4c39-8dd0-3fe46c69bb15/relationships/icons",
            "related": "https://api.appstoreconnect.apple.com/v1/builds/3f3a24e2-ae3b-4c39-8dd0-3fe46c69bb15/icons"
          }
        },
        "perfPowerMetrics": {
          "links": {
            "related": "https://api.appstoreconnect.apple.com/v1/builds/3f3a24e2-ae3b-4c39-8dd0-3fe46c69bb15/perfPowerMetrics"
          }
        },
        "diagnosticSignatures": {
          "links": {
            "self": "https://api.appstoreconnect.apple.com/v1/builds/3f3a24e2-ae3b-4c39-8dd0-3fe46c69bb15/relationships/diagnosticSignatures",
            "related": "https://api.appstoreconnect.apple.com/v1/builds/3f3a24e2-ae3b-4c39-8dd0-3fe46c69bb15/diagnosticSignatures"
          }
        }
      },
      "links": {
        "self": "https://api.appstoreconnect.apple.com/v1/builds/3f3a24e2-ae3b-4c39-8dd0-3fe46c69bb15"
      }
    }
  ],
  "links": {
    "self": "https://api.appstoreconnect.apple.com/v1/apps/6446998023/builds"
  },
  "meta": {
    "paging": {
      "total": 3,
      "limit": 50
    }
  }
}
```

## See Also

### Getting app build and prerelease version information

List All Prerelease Versions for an App

Get a list of prerelease versions associated with a specific app.

