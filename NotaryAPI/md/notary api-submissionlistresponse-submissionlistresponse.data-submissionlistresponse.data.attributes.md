

- Notary API
- SubmissionListResponse
- SubmissionListResponse.Data
-  SubmissionListResponse.Data.Attributes 

Object

# SubmissionListResponse.Data.Attributes

Information about the status of a submission.

Notary API 2.0.0+

``` source
object SubmissionListResponse.Data.Attributes
```

## Properties

`createdDate`

`string`

The date that you started the submission process, given in ISO 8601 format, like `2022-06-08T01:38:09.498Z`.

`name`

`string`

The name that you specified in the `submissionName` field of the Submit Software call when you started the submission.

`status`

`string`

The status of the submission. The associated string contains one of the following: `Accepted`, `In Progress`, `Invalid`, or `Rejected`.

## Attributes 

Possible types:

