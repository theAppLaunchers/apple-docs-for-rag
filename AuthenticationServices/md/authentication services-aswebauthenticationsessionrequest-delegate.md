

- Authentication Services
- ASWebAuthenticationSessionRequest
-  delegate 

Instance Property

# delegate

A delegate that the session request instance informs about authentication completion.

macOS 10.15+

``` source
weak var delegate: (any ASWebAuthenticationSessionRequestDelegate)? { get set }
```

## See Also

### Indicating Completion

protocol ASWebAuthenticationSessionRequestDelegate

An interface through which the session request can inform its delegate, which is typically a browser, about the outcome of the authentication attempt.

