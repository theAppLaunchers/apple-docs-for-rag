

- SwiftUI
- ShaderLibrary
-  init(data:) 

Initializer

# init(data:)

Creates a new Metal shader library from `data`, which must be the contents of precompiled Metal library. Functions compiled from the returned library will only be cached as long as the returned library exists.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+

``` source
init(data: Data)
```

## See Also

### Creating a shader library

init(url: URL)

Creates a new Metal shader library from the contents of `url`, which must be the location of precompiled Metal library. Functions compiled from the returned library will only be cached as long as the returned library exists.

