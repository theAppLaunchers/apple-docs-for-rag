

- BrowserEngineKit
- RenderingProcess
-  invalidate() 

Instance Method

# invalidate()

Stops the extension process.

iOS 17.4+iPadOS 17.4+macOS 14.3+

``` source
func invalidate()
```

## Overview

In both iOS 18 and iPadOS 18 and later, the operating system terminates the rendering extension process for your browser app. In earlier versions of iOS, the system marks the extension process as no longer in use, and might terminate it at a later time to free its resources. The operating system doesn’t call the interruption handler that you passed to the object’s initializer.

After you call `invalidate()`, other method calls on the object throw errors.

## See Also

### Creating and invalidating extension processes

init(bundleIdentifier: String?, onInterruption: () -> Void) async throws

Launches a rendering extension process asynchronously.

