

- Foundation
- NSURL
-  filePathURL 

Instance Property

# filePathURL

A file path URL that points to the same resource as the URL object. (read-only)

iOS 4.0+iPadOS 4.0+Mac Catalyst 13.1+macOS 10.6+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
var filePathURL: URL? { get }
```

## Discussion

If the receiver is a file reference URL, this property contains a copy of the URL converted to a file path URL. If the receiver’s URL is a file path URL, this property contains the original URL. If the original URL is not a file URL, or if the resource is not reachable or no longer exists, this property contains `nil`.

## See Also

### Modifying and Converting a File URL

func fileReferenceURL() -> URL?

Returns a new file reference URL that points to the same resource as the receiver.

func appendingPathComponent(String) -> URL?

Returns a new URL by appending a path component to the original URL.

func appendingPathComponent(String, isDirectory: Bool) -> URL?

Returns a new URL by appending a path component to the original URL, along with a trailing slash if the component is a directory.

func appendingPathComponent(String, conformingTo: UTType) -> URL

Returns a URL by appending the specified path component with the file extension for a uniform type identifier.

func appendingPathExtension(String) -> URL?

Returns a new URL by appending a path extension to the original URL.

func appendingPathExtension(for: UTType) -> URL

Returns a URL by appending the path extension for a uniform type identifier.

var deletingLastPathComponent: URL?

A URL you create by removing the last path component from the receiver. (read-only)

var deletingPathExtension: URL?

A URL you create by removing the path extension from the receiver, if any. (read-only)

var resolvingSymlinksInPath: URL?

A URL that points to the same resource as the receiver and includes no symbolic links. (read-only)

var standardizingPath: URL?

A URL that points to the same resource as the original URL using an absolute path. (read-only)

var hasDirectoryPath: Bool

A Boolean value that indicates whether the URL string’s path represents a directory.

