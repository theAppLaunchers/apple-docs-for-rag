

- App Store Connect API
-  Start a Build 

Web Service Endpoint

# Start a Build

Start a new Xcode Cloud build for a workflow.

App Store Connect API 1.5+

## URL

``` source
POST https://api.appstoreconnect.apple.com/v1/ciBuildRuns
```

## HTTP Body

CiBuildRunCreateRequest

The request body you use to start a new Xcode Cloud build.

Content-Type: application/json

## Response Codes

` 201 ``Created`

CiBuildRunResponse

`Created`

The request completed successfully and a new Build Runs resource has been created.

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

` 409 ``Conflict`

ErrorResponse

`Conflict`

The provided resource data is not valid.

Content-Type: application/json

` 422 `

ErrorResponse

Content-Type: application/json

## Discussion

The example request below starts a new build for a specific workflow. Use the information provided in the response to display build information on a dashboard or to access additional information; for example, the actions Xcode Cloud performs during the build.

### Example Request and Response

- Request
- Response

```
{
    “data”: {
        “type”: “ciBuildRuns”,
        “attributes”: {},
        “relationships”: {
            “workflow”: {
                “data”: {
                    “type”: “ciWorkflows”,
                    “id”: “a3946af0-cc38-4e0b-acba-5575c8dad050”
                }
            }
        }
    }
}
```

```
{
    "data": {
        "type": "ciBuildRuns",
        "id": "574f26a1-193c-409e-98ab-33ed4105a2ff",
        "attributes": {
            "number": 1,
            "createdDate": "2021-08-17T19:04:31.876Z",
            "startedDate": null,
            "finishedDate": null,
            "sourceCommit": {
                "commitSha": "The commit hash of the source commit.",
                "message": "A commit message.",
                "author": {
                    "displayName": "An author",
                    "avatarUrl": "https://example.com/user/avatar/author.png"
                },
                "committer": {
                    "displayName": "A committer",
                    "avatarUrl": "https://example.com/user/avatar/author.png"
                },
                "webUrl": "https://example.cpm/commits/abc123"
            },
            "destinationCommit": null,
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
                    "self": "https://api.appstoreconnect.apple.com/v1/ciBuildRuns/574f26a1-193c-409e-98ab-33ed4105a2ff/relationships/builds",
                    "related": "https://api.appstoreconnect.apple.com/v1/ciBuildRuns/574f26a1-193c-409e-98ab-33ed4105a2ff/builds"
                }
            },
            "actions": {
                "links": {
                    "self": "https://api.appstoreconnect.apple.com/v1/ciBuildRuns/574f26a1-193c-409e-98ab-33ed4105a2ff/relationships/actions",
                    "related": "https://api.appstoreconnect.apple.com/v1/ciBuildRuns/574f26a1-193c-409e-98ab-33ed4105a2ff/actions"
                }
            }
        },
        "links": {
            "self": "https://api.appstoreconnect.apple.com/v1/ciBuildRuns/574f26a1-193c-409e-98ab-33ed4105a2ff"
        }
    },
    "links": {
        "self": "https://api.appstoreconnect.apple.com/v1/ciBuildRuns"
    }
}

```

