Web Service

# Notary API

Submit your macOS software for notarization through a web interface.

Notary API 2.0.0+

## [Overview](/documentation/NotaryAPI#overview)

Notarization gives people confidence that your Developer ID-signed macOS software has been checked by Apple for malicious code. In addition to interacting with the notary service through Xcode or the `notarytool` command-line utility, you can bypass `notarytool` and interact directly with the service through its REST API. The Notary API is helpful for instances where you need to avoid a macOS dependency when uploading your app to the notary service, and provides endpoints that enable you to:

*   Prepare the notary service to receive a new version of your software, and get credentials that you use to upload your software to an Amazon S3 endpoint.
    
*   Check the status of a submission.
    
*   Retrieve a log file that provides details about a submission.
    
*   Get a list of your team’s previous submissions.
    

To learn how notarization works, see [Notarizing macOS software before distribution](/documentation/Security/notarizing-macos-software-before-distribution). For details about using the notary service REST API to upload your software, see [Submitting software for notarization over the web](/documentation/notaryapi/submitting-software-for-notarization-over-the-web).

## [Topics](/documentation/NotaryAPI#topics)

### [Essentials](/documentation/NotaryAPI#Essentials)

[

Submitting software for notarization over the web](/documentation/notaryapi/submitting-software-for-notarization-over-the-web)

Eliminate a dependency on macOS in your notarization workflow by interfacing directly with the notary service.

### [Software submission](/documentation/NotaryAPI#Software-submission)

[`Submit Software`](/documentation/notaryapi/submit-software)

Start the process of uploading a new version of your software to the notary service.

[`object NewSubmissionRequest`](/documentation/notaryapi/newsubmissionrequest)

Data that you provide when starting a submission to the notary service.

[`object NewSubmissionResponse`](/documentation/notaryapi/newsubmissionresponse)

The notary service’s response to a software submission.

### [Notarization results](/documentation/NotaryAPI#Notarization-results)

[`Get Submission Status`](/documentation/notaryapi/get-submission-status)

Fetch the status of a software notarization submission.

[`object SubmissionResponse`](/documentation/notaryapi/submissionresponse)

The notary service’s response to a request for the status of a submission.

[`Get Submission Log`](/documentation/notaryapi/get-submission-log)

Fetch details about a single completed notarization.

[`object SubmissionLogURLResponse`](/documentation/notaryapi/submissionlogurlresponse)

The notary service’s response to a request for the log information about a completed submission.

### [History](/documentation/NotaryAPI#History)

[`Get Previous Submissions`](/documentation/notaryapi/get-previous-submissions)

Fetch a list of your team’s previous notarization submissions.

[`object SubmissionListResponse`](/documentation/notaryapi/submissionlistresponse)

The notary service’s response to a request for information about your team’s previous submissions.

### [Errors](/documentation/NotaryAPI#Errors)

[`object ErrorResponse`](/documentation/notaryapi/errorresponse)

The notary service’s response when an error occurs.