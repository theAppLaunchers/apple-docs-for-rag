

- Exposure Notification
- Supporting Exposure Notifications Express
-  Setting Up an Exposure Notifications Express Test Verification Server 

Article

# Setting Up an Exposure Notifications Express Test Verification Server

Validate positive diagnoses for app-less exposure notifications.

## Overview

Exposure Notifications Express requires a Public Health Authority (PHA) to have a test verification server that verifies positive diagnoses received from a test center or other healthcare provider. A test verification server includes a mechanism to request a verification code for users with a positive COVID-19 test result. The test verification server also has APIs that allow Exposure Notifications Express to authenticate the user’s positive diagnosis before uploading exposure keys to the PHA’s key server

Google has created a reference implementation of a test verification server that you can use as a starting point or as a reference while implementing your own test verification server.

### Configure the Test Verification Server

Exposure Notifications Express works by reading configuration values for a PHA from Apple Business Registry (ABR). It uses these configuration values to locate a PHA’s servers and to adjust its calculations and behavior based on the values entered by that PHA. To set up a test verification server to work with Exposure Notifications Express, a PHA specifies the following values:

- **Test Verification Intro Message**: The `testVerificationIntroMessage` is a string that iOS presents to the user to explain the purpose of test verification and key upload.

- **Test Verification URL**: Exposure Notifications Express uses the `testVerificationURL` to exchange verification codes for long-term authentication tokens.

- **Test Verification Certificate URL**: Exposure Notifications Express uses the `testVerificationCertificateURL` to upload an HMAC and long-term authentication token and receive back a certificate and key metadata.

- **Test Verification API Key**: iOS needs the value in `testVerificationAPIKey` to communicate with your test verification server.

- **Verification Code Learn More URL**: Exposure Notifications Express presents the `verificationCodeLearnMoreURL` to the user when they have received a positive diagnosis. The link contains information on how to use the verification code and provides way to request help if the user experiences problems.

To see all of the configuration options available with Exposure Notifications Express, see Configuring Exposure Notifications.

### Generate Verification Codes on Request

PHAs use the test verification server to generate verification codes for positive test results. The verification code may be an 8-digit number that can be read over the phone or a deep link that can be texted or emailed to the user. A test verification server can use any one-time password algorithm to generate a verification code as long as the resulting code uniquely identifies one test result.

Note

For information on generating deep links that are compatible with Exposure Notifications Express, see Exposure Notifications Server Resource Identifier Scheme Documentation.

### Exchange Verification Codes for Tokens

Test verification servers must provide an endpoint to allow an iPhone to exchange a verification code for a long-term authentication token. PHAs register the URL for this endpoint with ABR as the Test Verification URL (`testVerificationURL`). This endpoint expects a JSON dictionary as the body of an HTTP POST request.

This endpoint supports one key in the request dictionary:

`code`  
String containing the authentication code. **Required**.

Requests must also include a custom HTTP header field called `X-API-Key`, with its value set to the test verification server’s secret API key. Test verification servers reject requests without this header or if the value in the header doesn’t match the API key registered with ABR.

The test verification server responds to these requests by returning a JSON dictionary in the body of the response. Here are the keys that the response dictionary uses:

`testtype`  
String representing the user’s test result. Possible values are “confirmed”, “likely”, or “negative”.

`symptomDate`  
String containing the date of symptom onset (`YYYY-MM-DD`).

`token`  
String containing the long-term authentication token.

`error`  
If the test verification server encounters an error while processing the request, this string contains a description of the problem.

`errorCode`  
If the test verification server encounters an error while processing the request, this string contains a code that describes the error.

### Respond to Verification Certificate Requests

Before uploading keys to the key server, Exposure Notifications Express contacts the verification server at the Test Verification Certificate URL (`testVerificationCertificateURL`) registered with ABR to get a certificate and metadata for the key batch.

The test verification server expects requests to this URL to contain a JSON dictionary in the body of an HTTP POST request. Here are the keys that dictionary supports:

`token`  
String containing the long-term authentication token previously received from the test verification server. **Required**.

`ekeyhmac`  
String containing a hash-based message authentication code Exposure Notifications Express calculated from the keys it will submit to the key server. For information on calculating HMAC, see the Public Health Authority Diagnosis Verification Protocol. **Required**.

Requests to this URL must also include a custom HTTP header field called `X-API-Key`, with its value set to the test verification server’s API key. Test verification servers reject requests without this header, or with the wrong value in the header.

The test validation server responds to requests by returning JSON in the body of the response. Here are the keys for that response dictionary:

`certificate`  
String containing the requested certificate if the test verification server was able to validate the request.

`error`  
If the test verification server encounters an error while processing the request, this string contains a description of the problem.

`errorCode`  
If the test verification server encounters an error while processing the request, this string contains a code describing the error.

## See Also

### Server Configuration

Configuring a Key Server for Exposure Notifications Express

Support exposure key upload and download for app-less exposure notifications.

