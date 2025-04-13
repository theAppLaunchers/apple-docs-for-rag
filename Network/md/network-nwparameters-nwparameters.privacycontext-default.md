

- Network
- NWParameters
- NWParameters.PrivacyContext
-  default 

Type Property

# default

The privacy context that applies to all connections that do not use a custom context.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 11.0+tvOS 14.0+visionOS 1.0+watchOS 7.0+

``` source
static let `default`: NWParameters.PrivacyContext
```

## Discussion

You cannot disable logging on the default privacy context.

Flushing the cache on the default privacy context will not affect other privacy contexts.

Changing name resolution settings will only affect privacy contexts that did not already explicitly configure resolution requirements.

## See Also

### Configuring Custom Privacy Settings

init(description: String)

Initializes a privacy context with a description string.

func disableLogging()

Disables system logging of connection activity.

func flushCache()

Flushes all cached data, such as TLS session state, created by connections associated with the privacy context.

