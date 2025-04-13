

- Authentication Services
- AuthorizationController
-  performAutoFillAssistedRequests(\_:) 

Instance Method

# performAutoFillAssistedRequests(\_:)

Performs an AutoFill-assisted authorization request from the provided array.

AuthenticationServicesSwiftUIiOS 16.4+iPadOS 16.4+visionOS 1.0+

``` source
@MainActor
func performAutoFillAssistedRequests(_ requests: [ASAuthorizationRequest]) async throws -> ASAuthorizationResult
```

## Parameters 

`requests`  

An array of supported authorization requests.

## Return Value

The request’s outcome. For more information, see ASAuthorizationResult.

## Discussion

To perform AutoFill-assisted authorization requests, add the appropriate textContentType(_:) to any sign-in related fields, such as those for usernames and passwords:

```
TextField("Username", text: $username)
    .textContentType(.username)
```

Then use task(priority:_:) or task(id:priority:_:) to perform the requests when the view appears:

```
.task {
    // Create the authorization requests.
    async let requests = makeAutoFillAuthorizationRequests()
    // Perform the request and await its result.
    let result = try await authorizationController
        .performAutoFillAssistedRequests(requests)
    switch result {
        // Process the request's result.
    }
}
```

## See Also

### Performing assisted requests

func performAutoFillAssistedRequest(ASAuthorizationRequest) async throws -> ASAuthorizationResult

Performs an AutoFill-assisted authorization request.

