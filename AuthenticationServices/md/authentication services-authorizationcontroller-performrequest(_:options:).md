

- Authentication Services
- AuthorizationController
-  performRequest(\_:options:) 

Instance Method

# performRequest(\_:options:)

Performs the specified authorization request with explicit options.

AuthenticationServicesSwiftUIiOS 16.4+iPadOS 16.4+Mac Catalyst 16.4+macOS 13.3+visionOS 1.0+

``` source
@MainActor
func performRequest(
    _ request: ASAuthorizationRequest,
    options: ASAuthorizationController.RequestOptions
) async throws -> ASAuthorizationResult
```

## Parameters 

`request`  

The authorization request to perform.

`options`  

Additional options that customize the request’s behavior. For more information, see ASAuthorizationController.RequestOptions.

## Return Value

The request’s outcome. For more information, see ASAuthorizationResult.

## See Also

### Performing requests

func performRequest(ASAuthorizationRequest) async throws -> ASAuthorizationResult

Performs the specified authorization request.

func performRequests([ASAuthorizationRequest]) async throws -> ASAuthorizationResult

Performs an authorization request from the provided array.

func performRequests([ASAuthorizationRequest], options: ASAuthorizationController.RequestOptions) async throws -> ASAuthorizationResult

Performs an authorization request, with explicit options, from the provided array.

func performRequest(ASAuthorizationRequest, customMethods: [ASAuthorizationCustomMethod]) async throws -> ASAuthorizationResult

Performs the authorization request using a custom authorization method.

func performRequests([ASAuthorizationRequest], customMethods: [ASAuthorizationCustomMethod]) async throws -> ASAuthorizationResult

Performs an authorization request from the provided array using a custom authorization method.

