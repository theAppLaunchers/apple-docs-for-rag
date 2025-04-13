

- AdServices
- AAAttributionError
- AAAttributionError.Code
-  AAAttributionError.Code.networkError 

Case

# AAAttributionError.Code.networkError

The server is unable to provide a token because the internet isn’t available.

iOS 14.3+iPadOS 14.3+Mac Catalyst 14.3+macOS 11.1+visionOS 1.0+

``` source
case networkError
```

## Discussion

To receive an attribution token, you must have unimpeded internet access. Make sure you’re not using a simulator when generating a token.

## See Also

### Determining the cause of an error

case internalError

The server is unable to provide a token because of an internal error.

case platformNotSupported

The server is unable to provide a token because of an unsupported operating system.

