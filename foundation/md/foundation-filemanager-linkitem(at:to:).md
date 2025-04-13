

- Foundation
- FileManager
-  linkItem(at:to:) 

Instance Method

# linkItem(at:to:)

Creates a hard link between the items at the specified URLs.

iOS 4.0+iPadOS 4.0+Mac Catalyst 13.1+macOS 10.6+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func linkItem(
    at srcURL: URL,
    to dstURL: URL
) throws
```

## Parameters 

`srcURL`  

The file URL that identifies the source of the link. The URL in this parameter must not be a file reference URL; it must specify the actual path to the item. The value in this parameter must not be `nil`.

`dstURL`  

The file URL that specifies where you want to create the hard link. The URL in this parameter must not be a file reference URL; it must specify the actual path to the item. The value in this parameter must not be `nil`.

## Discussion

Use this method to create hard links between files in the current file system. If `srcURL` is a directory, this method creates a new directory at `dstURL` and then creates hard links for the items in that directory. If `srcURL` is (or contains) a symbolic link, the symbolic link is copied and not converted to a hard link at `dstURL`.

Prior to linking each item, the file manager asks its delegate if it should actually create the link. It does this by calling the fileManager(_:shouldLinkItemAt:to:) method; if that method is not implemented it calls the fileManager(_:shouldLinkItemAtPath:toPath:) method instead. If the delegate method returns true, or if the delegate does not implement the appropriate methods, the file manager creates the hard link. If there is an error linking one out of several items, the file manager may also call the delegate’s fileManager(_:shouldProceedAfterError:linkingItemAt:to:) or fileManager(_:shouldProceedAfterError:linkingItemAtPath:toPath:) method to determine how to proceed.

Handling Errors in Swift

In Swift, this method returns `Void` and is marked with the `throws` keyword to indicate that it throws an error in cases of failure.

You call this method in a `try` expression and handle any errors in the `catch` clauses of a `do` statement, as described in Error Handling in The Swift Programming Language and `About Imported Cocoa Error Parameters`.

## See Also

### Creating Symbolic and Hard Links

func createSymbolicLink(at: URL, withDestinationURL: URL) throws

Creates a symbolic link at the specified URL that points to an item at the given URL.

func createSymbolicLink(atPath: String, withDestinationPath: String) throws

Creates a symbolic link that points to the specified destination.

func linkItem(atPath: String, toPath: String) throws

Creates a hard link between the items at the specified paths.

func destinationOfSymbolicLink(atPath: String) throws -> String

Returns the path of the item pointed to by a symbolic link.

