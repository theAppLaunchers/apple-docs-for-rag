

- System
- Errno
-  fileNameTooLong 

Type Property

# fileNameTooLong

The file name is too long.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 11.0+tvOS 14.0+visionOS 1.0+watchOS 7.0+

``` source
static var fileNameTooLong: Errno { get }
```

## Mentioned in 

Adopting Swift Error Constants

## Discussion

A component of a pathname exceeded 255 (`MAXNAMELEN`) characters, or an entire pathname exceeded 1023 (`MAXPATHLEN-1`) characters.

The corresponding C error is `ENAMETOOLONG`.

## See Also

### Path Errors

static var tooManyRemoteLevels: Errno

Too many levels of remote in path.

static var tooManySymbolicLinkLevels: Errno

Too many levels of symbolic links.

