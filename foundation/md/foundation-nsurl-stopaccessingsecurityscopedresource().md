

- Foundation
- NSURL
-  stopAccessingSecurityScopedResource() 

Instance Method

# stopAccessingSecurityScopedResource()

In an app that adopts App Sandbox, revokes access to the resource pointed to by a security-scoped URL.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+macOS 10.7+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func stopAccessingSecurityScopedResource()
```

## Discussion

When you no longer need access to a file or directory pointed to by a security-scoped URL, such as one returned by resolving a security-scoped bookmark, call this method on the URL to relinquish access. You can also use its Core Foundation equivalent, the CFURLStopAccessingSecurityScopedResource(_:) function.

You must balance each call to startAccessingSecurityScopedResource() for a given security-scoped URL with a call to stopAccessingSecurityScopedResource(). When you make the last balanced call to stopAccessingSecurityScopedResource(), you immediately lose access to the resource in question.

Warning

If you fail to relinquish your access to file-system resources when you no longer need them, your app leaks kernel resources. If sufficient kernel resources leak, your app loses its ability to add file-system locations to its sandbox, such as with Powerbox or security-scoped bookmarks, until relaunched.

If you call this method on a URL whose referenced resource you don’t have access to, nothing happens.

Version note

Security-scoped bookmarks aren’t available in versions of macOS prior to OS X 10.7.3.

## See Also

### Working with Bookmark Data

class func bookmarkData(withContentsOf: URL) throws -> Data

Initializes and returns bookmark data derived from an alias file pointed to by a specified URL.

func bookmarkData(options: NSURL.BookmarkCreationOptions, includingResourceValuesForKeys: [URLResourceKey]?, relativeTo: URL?) throws -> Data

Returns a bookmark for the URL, created with specified options and resource values.

class func resourceValues(forKeys: [URLResourceKey], fromBookmarkData: Data) -> [URLResourceKey : Any]?

Returns the resource values for properties identified by a specified array of keys contained in specified bookmark data.

class func writeBookmarkData(Data, to: URL, options: NSURL.BookmarkFileCreationOptions) throws

Creates an alias file on disk at a specified location with specified bookmark data.

func startAccessingSecurityScopedResource() -> Bool

In an app that has adopted App Sandbox, makes the resource pointed to by a security-scoped URL available to the app.

typealias BookmarkFileCreationOptions

Options used when creating file bookmark data

struct BookmarkCreationOptions

Options used when creating bookmark data.

struct BookmarkResolutionOptions

Options used when resolving bookmark data.

