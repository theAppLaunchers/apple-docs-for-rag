

- Foundation
- FileManager
-  contentsOfDirectory(at:includingPropertiesForKeys:options:) 

Instance Method

# contentsOfDirectory(at:includingPropertiesForKeys:options:)

Performs a shallow search of the specified directory and returns URLs for the contained items.

iOS 4.0+iPadOS 4.0+Mac Catalyst 13.1+macOS 10.6+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func contentsOfDirectory(
    at url: URL,
    includingPropertiesForKeys keys: [URLResourceKey]?,
    options mask: FileManager.DirectoryEnumerationOptions = []
) throws -> [URL]
```

## Parameters 

`url`  

The URL for the directory whose contents you want to enumerate.

`keys`  

An array of keys that identify the file properties that you want pre-fetched for each item in the directory. For each returned URL, the specified properties are fetched and cached in the NSURL object. For a list of keys you can specify, see Common File System Resource Keys.

If you want directory contents to have no pre-fetched file properties, pass an empty array to this parameter. If you want directory contents to have default set of pre-fetched file properties, pass `nil` to this parameter.

`mask`  

Options for the enumeration. Because this method performs only shallow enumerations, options that prevent descending into subdirectories or packages are not allowed; the only supported option is skipsHiddenFiles.

## Return Value

An array of NSURL objects, each of which identifies a file, directory, or symbolic link contained in `url`. If the directory contains no entries, this method returns an empty array. When using Objective-C, if an error occurs, this method returns `nil` and assigns an appropriate error object to the `error` parameter.

## Discussion

This method performs a shallow search of the directory and therefore does not traverse symbolic links or return the contents of any subdirectories. This method also does not return URLs for the current directory (”`.`”), parent directory (”`..`”), or resource forks (files that begin with “`._`”) but it does return other hidden files. If you need to perform a deep enumeration, use the enumeratorAtURL:includingPropertiesForKeys:options:errorHandler: method instead.

The order of the files in the returned array is undefined.

Handling Errors in Swift

In Swift, this method returns a nonoptional result and is marked with the `throws` keyword to indicate that it throws an error in cases of failure.

You call this method in a `try` expression and handle any errors in the `catch` clauses of a `do` statement, as described in Error Handling in The Swift Programming Language and `About Imported Cocoa Error Parameters`.

## See Also

### Discovering Directory Contents

func contentsOfDirectory(atPath: String) throws -> [String]

Performs a shallow search of the specified directory and returns the paths of any contained items.

func enumerator(at: URL, includingPropertiesForKeys: [URLResourceKey]?, options: FileManager.DirectoryEnumerationOptions, errorHandler: ((URL, any Error) -> Bool)?) -> FileManager.DirectoryEnumerator?

Returns a directory enumerator object that can be used to perform a deep enumeration of the directory at the specified URL.

func enumerator(atPath: String) -> FileManager.DirectoryEnumerator?

Returns a directory enumerator object that can be used to perform a deep enumeration of the directory at the specified path.

class DirectoryEnumerator

An object that enumerates the contents of a directory.

func mountedVolumeURLs(includingResourceValuesForKeys: [URLResourceKey]?, options: FileManager.VolumeEnumerationOptions) -> [URL]?

Returns an array of URLs that identify the mounted volumes available on the device.

struct VolumeEnumerationOptions

Options for enumerating mounted volumes with the mountedVolumeURLs(includingResourceValuesForKeys:options:) method.

func subpathsOfDirectory(atPath: String) throws -> [String]

Performs a deep enumeration of the specified directory and returns the paths of all of the contained subdirectories.

func subpaths(atPath: String) -> [String]?

Returns an array of strings identifying the paths for all items in the specified directory.

