

- Foundation
- NSFileVersion
-  remove() 

Instance Method

# remove()

Remove this version object and its associated file from the version store.

iOS 5.0+iPadOS 5.0+Mac Catalyst 13.1+macOS 10.7+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func remove() throws
```

## Discussion

This method removes this version object and its file from the version store, freeing up the associated storage space. You must not call this method for the current file version—that is, the version object returned by the currentVersionOfItem(at:) method.

You should always remove file versions as part of a coordinated write operation to a file. In other words, always call this method from a block passed to a file coordinator object to initiate a write operation. Doing so ensures that no other processes are operating on the file while you remove the version information.

If successful, subsequent requests for the versions of the file do not include this version object (or any object with the same information). You can use this method to free up disk space by removing versions that are no longer needed.

Handling Errors in Swift

In Swift, this method returns `Void` and is marked with the `throws` keyword to indicate that it throws an error in cases of failure.

You call this method in a `try` expression and handle any errors in the `catch` clauses of a `do` statement, as described in Error Handling in The Swift Programming Language and `About Imported Cocoa Error Parameters`.

## See Also

### Replacing and Deleting Versions

func replaceItem(at: URL, options: NSFileVersion.ReplacingOptions) throws -> URL

Replace the contents of the specified file with the contents of the current version’s file.

class func removeOtherVersionsOfItem(at: URL) throws

Removes all versions of a file, except the current one, from the version store.

