

- App Store Connect API
-  Read the Xcode Cloud Build Information for a Build Action 

Web Service Endpoint

# Read the Xcode Cloud Build Information for a Build Action

Get Xcode Cloud build information for a given build action.

App Store Connect API 1.5+

## URL

``` source
GET https://api.appstoreconnect.apple.com/v1/ciBuildActions/{id}/buildRun
```

## Path Parameters

`id`

`string`

 (Required) 

The opaque resource ID that uniquely identifies the Build Actions resource.

## Query Parameters

`fields[builds]`

`[string]`

Additional fields to include for each Build Runs resource returned by the response.

Possible Values: `version, uploadedDate, expirationDate, expired, minOsVersion, lsMinimumSystemVersion, computedMinMacOsVersion, iconAssetToken, processingState, buildAudienceType, usesNonExemptEncryption, preReleaseVersion, individualTesters, betaGroups, betaBuildLocalizations, appEncryptionDeclaration, betaAppReviewSubmission, app, buildBetaDetail, appStoreVersion, icons, buildBundles, perfPowerMetrics, diagnosticSignatures`

`fields[ciBuildRuns]`

`[string]`

Additional fields to include for each Build Runs resource returned by the response.

Possible Values: `number, createdDate, startedDate, finishedDate, sourceCommit, destinationCommit, isPullRequestBuild, issueCounts, executionProgress, completionStatus, startReason, cancelReason, builds, workflow, product, sourceBranchOrTag, destinationBranch, actions, pullRequest`

`include`

`[string]`

The relationship data to include in the response.

Possible Values: `builds, workflow, product, sourceBranchOrTag, destinationBranch, pullRequest`

`limit[builds]`

`integer`

The number of included Build Runs resources to return if the builds relationship is included.

Maximum: `50`

`fields[scmGitReferences]`

`[string]`

Possible Values: `name, canonicalName, isDeleted, kind, repository`

`fields[ciWorkflows]`

`[string]`

Possible Values: `name, description, branchStartCondition, tagStartCondition, pullRequestStartCondition, scheduledStartCondition, manualBranchStartCondition, manualTagStartCondition, manualPullRequestStartCondition, actions, isEnabled, isLockedForEditing, clean, containerFilePath, lastModifiedDate, product, repository, xcodeVersion, macOsVersion, buildRuns`

`fields[scmPullRequests]`

`[string]`

Possible Values: `title, number, webUrl, sourceRepositoryOwner, sourceRepositoryName, sourceBranchName, destinationRepositoryOwner, destinationRepositoryName, destinationBranchName, isClosed, isCrossRepository, repository`

`fields[ciProducts]`

`[string]`

Possible Values: `name, createdDate, productType, app, bundleId, workflows, primaryRepositories, additionalRepositories, buildRuns`

## Response Codes

` 200 ``OK`

CiBuildRunResponse

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

The example request below retrieves detailed information for a specific action Xcode Cloud performed. Use the data provided in the response to display detailed build information on a dashboard or to access related information.

### Example Request and Response

- Request
- Response

```
GET https://api.appstoreconnect.apple.com/v1/ciBuildActions/6034552c-6cc0-4ac3-ad18-c3d24970882d/buildRun
```

```
{
    "data": {
        "type": "ciBuildRuns",
        "id": "56c512e6-111e-4067-8e88-640c28ce91a7",
        "attributes": {
            "number": 1,
            "createdDate": "2021-08-17T17:48:11.806Z",
            "startedDate": null,
            "finishedDate": null,
            "sourceCommit": {
                "commitSha": "SHA",
                "message": "Summary Message.\n\nSome more details about the commit.",
                "author": {
                    "displayName": "Source Author",
                    "avatarUrl": ""
                },
                "committer": {
                    "displayName": "Source Committer",
                    "avatarUrl": ""
                },
                "webUrl": "https://example.com/commit/abc123"
            },
            "destinationCommit": {
                "commitSha": "A commit hash.",
                "message": "BASE MESSAGE",
                "author": {
                    "displayName": "Base Author",
                    "avatarUrl": "https://example.com/user/avatar/author.png"
                },
                "committer": {
                    "displayName": "Base Committer",
                    "avatarUrl": "https://example.com/user/avatar/author.png"
                },
                "webUrl": "https://example.com/commit/xyz987"
            },
            "isPullRequestBuild": false,
            "issueCounts": null,
            "executionProgress": "PENDING",
            "completionStatus": null,
            "startReason": "MANUAL",
            "cancelReason": null
        },
        "relationships": {
            "builds": {
                "links": {
                    "self": "https://api.appstoreconnect.apple.com/v1/ciBuildRuns/56c512e6-111e-4067-8e88-640c28ce91a7/relationships/builds",
                    "related": "https://api.appstoreconnect.apple.com/v1/ciBuildRuns/56c512e6-111e-4067-8e88-640c28ce91a7/builds"
                }
            },
            "actions": {
                "links": {
                    "self": "https://api.appstoreconnect.apple.com/v1/ciBuildRuns/56c512e6-111e-4067-8e88-640c28ce91a7/relationships/actions",
                    "related": "https://api.appstoreconnect.apple.com/v1/ciBuildRuns/56c512e6-111e-4067-8e88-640c28ce91a7/actions"
                }
            }
        },
        "links": {
            "self": "https://api.appstoreconnect.apple.com/v1/ciBuildRuns/56c512e6-111e-4067-8e88-640c28ce91a7"
        }
    },
    "links": {
        "self": "https://api.appstoreconnect.apple.com/v1/ciBuildRuns/56c512e6-111e-4067-8e88-640c28ce91a7"
    }
}
```

## See Also

### Getting Build Actions

Read Build Action Information

Get information about a specific action Xcode Cloud performed as part of a build.

List All Artifacts for a Build Action

List all artifacts Xcode Cloud created when it performed an action.

List All Issues for a Build Action

List all issues that occurred for a specific action that Xcode Cloud performed as part of a build.

List All Test Results for an Xcode Cloud Test Action

List all test results for a specific test action Xcode Cloud performed as part of a build.

