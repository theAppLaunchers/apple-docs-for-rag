

- CloudKit
-  CKFetchWebAuthTokenOperation 

Class

# CKFetchWebAuthTokenOperation

An operation that creates an authentication token for use with CloudKit web services.

iOS 9.2+iPadOS 9.2+Mac Catalyst 13.1+macOS 10.11+tvOS 9.1+visionOS 1.0+watchOS 3.0+

``` source
class CKFetchWebAuthTokenOperation
```

## Mentioned in 

Changing Access Controls on User Data

## Overview

CloudKit web services provides an HTTP interface to fetch, create, update, and delete records, zones, and subscriptions. Each request you send requires an API token, which you configure in CloudKit Dashboard. You must create an API token for each container in each environment.

If you want to send a request to an endpoint that requires an authenticated user, use this operation to fetch an authentication token. Append the authentication token, along with the API token, to the endpoint’s URL. That request then acts on behalf of the current user. Authentication tokens are short-lived and expire after a single use.

For an example of using a web authentication token with a CloudKit web service, see Changing Access Controls on User Data.

This operation executes the handlers you provide on an internal queue it manages. Your handlers must be capable of executing on a background queue. Tasks that need access to the main queue must redirect as appropriate.

The operation calls fetchWebAuthTokenCompletionBlock after it executes to provide the fetched token. Use the completion handler to perform housekeeping tasks for the operation. It should also manage any failures, whether due to an error or an explicit cancellation.

Note

Because this class inherits from Operation, you can also set the completionBlock property. The operation calls both completion handlers if they’re both set.

CloudKit operations have a default QoS of QualityOfService.default. Operations with this service level are discretionary. The system schedules their execution at an optimal time according to battery level and network conditions, among other factors. Use the qualityOfService property to set a more appropriate QoS for the operation.

The following example shows how to create the operation, configure its callbacks, and execute it in the user’s private database:

```
func fetchWebAuthToken(for apiToken: String, 
    completion: @escaping (Result) -> Void) {

    // Create the operation using the API token
    // that the caller provides to the method.
    let operation = CKFetchWebAuthTokenOperation(apiToken: apiToken)

    // If the operation fails, return the error to the caller.
    // Otherwise, return the fetched authentication token.
    operation.fetchWebAuthTokenCompletionBlock = { webToken, error in
        if let error = error {
            completion(.failure(error))
        } else {
            completion(.success(webToken!))
        }
    }

    // Set an appropriate QoS and add the operation to the
    // private database's queue to execute it.
    operation.qualityOfService = .utility
    CKContainer.default().privateCloudDatabase.add(operation)
}
```

## Topics

### Creating a Fetch Token Operation

convenience init(apiToken: String)

Creates a fetch operation for the specified API token.

init()

Creates an empty fetch operation.

### Managing the Operation’s Configuration

var apiToken: String?

The API token that allows access to an app’s container.

var fetchWebAuthTokenCompletionBlock: ((String?, (any Error)?) -> Void)?

The block to execute when the operation finishes.

Deprecated

### Instance Properties

var fetchWebAuthTokenResultBlock: ((Result&lt;String, any Error>) -> Void)?

## Relationships

### Inherits From

- CKDatabaseOperation

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSObjectProtocol
- Sendable

## See Also

### Privacy

Encrypting User Data

Deploy industry-standard security technologies using CloudKit encryption.

Providing User Access to CloudKit Data

Provide users access to the data your app stores on their behalf.

Changing Access Controls on User Data

Restrict access to or remove restrictions from a user’s data at their request.

Responding to Requests to Delete Data

Provide options for users to delete their CloudKit data from your app.

Identifying an App’s Containers

Use Xcode’s Project navigator to find the identifiers of active CloudKit containers.

