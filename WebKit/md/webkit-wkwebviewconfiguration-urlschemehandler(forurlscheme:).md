

- WebKit
- WKWebViewConfiguration
-  urlSchemeHandler(forURLScheme:) 

Instance Method

# urlSchemeHandler(forURLScheme:)

Returns the currently registered handler object for the specified URL scheme.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.1+macOS 10.13+visionOS 1.0+

``` source
@MainActor
func urlSchemeHandler(forURLScheme urlScheme: String) -> (any WKURLSchemeHandler)?
```

## Parameters 

`urlScheme`  

The scheme to look up. Scheme names are case sensitive, must start with an ASCII letter, and may contain only ASCII letters, numbers, the “`+`” character, the “`-`” character, and the “`.`” character. If this parameter contains an empty string or the scheme name includes invalid characters, this method returns `nil`.

## Return Value

The handler object for the specified scheme, or `nil` if the scheme has no handler.

## See Also

### Adding handlers for custom URL schemes

func setURLSchemeHandler((any WKURLSchemeHandler)?, forURLScheme: String)

Registers an object to load resources associated with the specified URL scheme.

