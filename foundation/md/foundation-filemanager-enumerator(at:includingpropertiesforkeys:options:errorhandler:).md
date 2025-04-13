

- Foundation
- FileManager
-  enumerator(at:includingPropertiesForKeys:options:errorHandler:) 

Instance Method

# enumerator(at:includingPropertiesForKeys:options:errorHandler:)

Returns a directory enumerator object that can be used to perform a deep enumeration of the directory at the specified URL.

iOS 8.0+iPadOS 8.0+Mac Catalyst 8.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
@nonobjc
func enumerator(
    at url: URL,
    includingPropertiesForKeys keys: [URLResourceKey]?,
    options mask: FileManager.DirectoryEnumerationOptions = [],
    errorHandler handler: ((URL, any Error) -> Bool)? = nil
) -> FileManager.DirectoryEnumerator?
```

## Parameters 

`url`  

The location of the directory for which you want an enumeration. This URL must not be a symbolic link that points to the desired directory. You can use the resolvingSymlinksInPath method to resolve any symlinks in the URL.

`keys`  

An array of keys that identify the properties that you want pre-fetched for each item in the enumeration. The values for these keys are cached in the corresponding NSURL objects. You may specify nil for this parameter. For a list of keys you can specify, see URLResourceKey.

`mask`  

Options for the enumeration. For a list of valid options, see FileManager.DirectoryEnumerationOptions.

`handler`  

An optional error handler block for the file manager to call when an error occurs. The handler block should return true if you want the enumeration to continue or false if you want the enumeration to stop. The block takes the following parameters:

| url | A `URL` that identifies the item for which the error occurred. |
|----|----|
| error | An NSError object that contains information about the error. |

If you specify `nil` for this parameter, the enumerator object continues to enumerate items as if you had specified a block that returned `true`.

## Return Value

An directory enumerator object that enumerates the contents of the directory at `url`. If `url` is a filename, the method returns an enumerator object that enumerates no files—the first call to nextObject() returns nil.

## Discussion

Because the enumeration is deep—that is, it lists the contents of all subdirectories—this enumerator object is useful for performing actions that involve large file-system subtrees. If the method is passed a directory on which another file system is mounted (a mount point), it traverses the mount point. This method does not resolve symbolic links or mount points encountered in the enumeration process, nor does it recurse through them if they point to a directory.

For example, if you pass a URL that points to `/Volumes/MyMountedFileSystem`, the returned enumerator will include the entire directory structure for the file system mounted at that location. If, on the other hand, you pass `/Volumes`, the returned enumerator will include `/Volumes/MyMountedFileSystem` as one of its results, but will not traverse into the file system mounted there.

The FileManager.DirectoryEnumerator class has methods for skipping descendants of the existing path and for returning the number of levels deep the current object is in the directory hierarchy being enumerated (where the directory passed to enumerator(at:includingPropertiesForKeys:options:errorHandler:) is considered to be level 0).

This code fragment enumerates a URL and its subdirectories, collecting the URLs of files (skips directories). It also demonstrates how to ignore the contents of specified directories, in this case directories named “`_extras`”.

```
let directoryURL = Bundle.main.bundleURL
let localFileManager = FileManager()

let resourceKeys = Set([.nameKey, .isDirectoryKey])
let directoryEnumerator = localFileManager.enumerator(at: directoryURL, includingPropertiesForKeys: Array(resourceKeys), options: .skipsHiddenFiles)!

var fileURLs: [URL] = []
for case let fileURL as URL in directoryEnumerator {
    guard let resourceValues = try? fileURL.resourceValues(forKeys: resourceKeys),
        let isDirectory = resourceValues.isDirectory,
        let name = resourceValues.name
        else {
            continue
    }

    if isDirectory {
        if name == "_extras" {
            directoryEnumerator.skipDescendants()
        }
    } else {
        fileURLs.append(fileURL)
    }
}

print(fileURLs)
```

## See Also

### Discovering Directory Contents

func contentsOfDirectory(at: URL, includingPropertiesForKeys: [URLResourceKey]?, options: FileManager.DirectoryEnumerationOptions) throws -> [URL]

Performs a shallow search of the specified directory and returns URLs for the contained items.

func contentsOfDirectory(atPath: String) throws -> [String]

Performs a shallow search of the specified directory and returns the paths of any contained items.

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

