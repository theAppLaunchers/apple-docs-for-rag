

- Foundation
- URL
-  stopAccessingSecurityScopedResource() 

Instance Method

# stopAccessingSecurityScopedResource()

Revokes the access granted to the url by a prior successful call to the complementary start function.

iOS 8.0+iPadOS 8.0+Mac Catalyst 8.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func stopAccessingSecurityScopedResource()
```

## Mentioned in 

Implementing Handoff in Your App

## Discussion

When you no longer need access to a file or directory pointed to by a security-scoped URL, such as one returned by resolving a security-scoped bookmark, call this method on the URL to relinquish access. You can also use its Core Foundation equivalent, the CFURLStopAccessingSecurityScopedResource(_:) function.

You must balance each call to startAccessingSecurityScopedResource() for a given security-scoped URL with a call to stopAccessingSecurityScopedResource(). When you make the last balanced call to stopAccessingSecurityScopedResource(), you immediately lose access to the resource in question.

Warning

If you fail to relinquish your access to file-system resources when you no longer need them, your app leaks kernel resources. If sufficient kernel resources leak, your app loses its ability to add file-system locations to its sandbox, such as with Powerbox or security-scoped bookmarks, until relaunched.

If you call this method on a URL whose referenced resource you don’t have access to, nothing happens.

Version note

Security-scoped bookmarks aren’t available in versions of macOS prior to OS X 10.7.3.

## See Also

### Working with security scoped resources

func startAccessingSecurityScopedResource() -> Bool

Given a url created by resolving a bookmark data created with security scope, make the resource referenced by the url accessible to the process.

