

- Notary API
-  NewSubmissionRequest 

Object

# NewSubmissionRequest

Data that you provide when starting a submission to the notary service.

Notary API 2.0.0+

``` source
object NewSubmissionRequest
```

## Properties

`notifications`

`[`NewSubmissionRequest.Notifications`]`

An optional array of notifications that you want to receive when notarization finishes. Omit this key if you don’t need a notification.

`sha256`

`string`

 (Required) 

A cryptographic hash of the software that you want to notarize, computed using Secure Hashing Algorithm 2 (SHA-2) with a 256-bit digest. Supply the hash as a string of 64 hexadecimal digits. You must compute the hash from the exact version of the software that you plan to upload to Amazon S3.

Value: `/[A-Fa-f0-9]{64}/`

`submissionName`

`string`

 (Required) 

The name of the file that you plan to submit. The service includes this name in its responses when you ask for the status of a submission, get a list of previous submissions, or get a log file corresponding to a submission. The file name doesn’t have to be unique among all your submissions, but making it so might help you to distinguish among submissions in service responses.

## Attributes 

Possible types:

## Discussion

Use a structure of this type as the HTTP body when you post to the Submit Software endpoint.

## Topics

### Objects

object NewSubmissionRequest.Notifications

A notification that the notary service sends you when notarization finishes.

## See Also

### Software submission

Submit Software

Start the process of uploading a new version of your software to the notary service.

object NewSubmissionResponse

The notary service’s response to a software submission.

