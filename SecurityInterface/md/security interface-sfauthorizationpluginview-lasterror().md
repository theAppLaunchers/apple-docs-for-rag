

- Security Interface
- SFAuthorizationPluginView
-  lastError() 

Instance Method

# lastError()

Returns the last error that occurred during evaluation.

macOS 10.5+

``` source
func lastError() -> (any Error)!
```

## Discussion

Your authorization plug-in should override this method and return the last error that occurred during evaluation or `nil` if no error occurred.

A downstream plug-in can set a context value using the `kAuthorizationContextFlagSticky` flag to make it available to the `SFAuthorizationPluginView` class in case of an error.

## See Also

### Getting Instance Information

func callbacks() -> UnsafePointer&lt;AuthorizationCallbacks>!

Returns the authorization callbacks structure with which this instance was initialized.

func engineRef() -> AuthorizationEngineRef!

Returns the authorization engine handle with which this instance was initialized.

