

- Foundation
- NSFileVersion
-  addOfItem(at:withContentsOf:options:) 

Type Method

# addOfItem(at:withContentsOf:options:)

Creates a version of the file at the specified location.

macOS 10.7+

``` source
class func addOfItem(
    at url: URL,
    withContentsOf contentsURL: URL,
    options: NSFileVersion.AddingOptions = []
) throws -> NSFileVersion
```

## Parameters 

`url`  

The location at which to store the new file version.

`contentsURL`  

The URL that specifies the file to use for the version contents.

`options`  

Specify 0 for this parameter if you want to create a copy of the file at the location specified by the `url` parameter. Alternatively, specify one of the constants described in NSFileVersion.AddingOptions.

## Return Value

The file version object representing the new version or `nil` if an error occurred.

## Discussion

You can use this method to save a version of your file to the location specified by the `url` parameter. The contents of the file are taken from the `contentsURL` parameter, whose value may be the same as the `url` parameter.

You should always add file versions as part of a coordinated write operation to a file. In other words, always call this method from a block passed to a file coordinator object to initiate a write operation. Doing so ensures that no other processes are operating on the file while you save the version to its new location.

Handling Errors in Swift

In Swift, this method returns a nonoptional result and is marked with the `throws` keyword to indicate that it throws an error in cases of failure.

You call this method in a `try` expression and handle any errors in the `catch` clauses of a `do` statement, as described in Error Handling in The Swift Programming Language and `About Imported Cocoa Error Parameters`.

