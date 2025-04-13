

- System
- FileDescriptor
- FileDescriptor.OpenOptions
-  symlink 

Type Property

# symlink

Indicates that opening the file opens symbolic links instead of following them.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 11.0+tvOS 14.0+visionOS 1.0+watchOS 7.0+

``` source
static var symlink: FileDescriptor.OpenOptions { get }
```

## Mentioned in 

Adopting Swift File Options

## Discussion

If you specify this option and the file path you pass to doc:FileDescriptor/open(\_:\_:options:permissions:retryOnInterrupt:)-2266j is a symbolic link, then the link itself is opened instead of what it links to.

The corresponding C constant is `O_SYMLINK`.

## See Also

### Specifying Options

static var append: FileDescriptor.OpenOptions

Indicates that each write operation appends to the file.

static var closeOnExec: FileDescriptor.OpenOptions

Indicates that executing a program closes the file.

static var create: FileDescriptor.OpenOptions

Indicates that opening the file creates the file if it doesn’t exist.

static var eventOnly: FileDescriptor.OpenOptions

Indicates that opening the file monitors a file for changes.

static var exclusiveCreate: FileDescriptor.OpenOptions

Indicates that opening the file creates the file, expecting that it doesn’t exist.

static var exclusiveLock: FileDescriptor.OpenOptions

Indicates that opening the file atomically obtains an exclusive lock.

static var noFollow: FileDescriptor.OpenOptions

Indicates that opening the file doesn’t follow symlinks.

static var nonBlocking: FileDescriptor.OpenOptions

Indicates that opening the file doesn’t wait for the file or device to become available.

static var sharedLock: FileDescriptor.OpenOptions

Indicates that opening the file atomically obtains a shared lock on the file.

static var truncate: FileDescriptor.OpenOptions

Indicates that opening the file truncates the file if it exists.

