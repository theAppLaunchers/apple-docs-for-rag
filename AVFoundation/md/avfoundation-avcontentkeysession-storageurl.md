

- AVFoundation
- AVContentKeySession
-  storageURL 

Instance Property

# storageURL

A URL that points to a writable storage directory.

iOS 10.3+iPadOS 10.3+Mac Catalyst 13.1+macOS 10.12.4+tvOS 10.2+visionOS 1.0+watchOS 7.0+

``` source
var storageURL: URL? { get }
```

## Discussion

The writable directory stores expired session reports.

## See Also

### Inspecting the Session

var keySystem: AVContentKeySystem

The type of key system used to retrieve keys.

struct AVContentKeySystem

A key-delivery method for a content key session.

