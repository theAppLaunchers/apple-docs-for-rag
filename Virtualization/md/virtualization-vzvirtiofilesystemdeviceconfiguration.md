

- Virtualization
-  VZVirtioFileSystemDeviceConfiguration 

Class

# VZVirtioFileSystemDeviceConfiguration

An object that represents the configuration of a Virtio file system device.

macOS 12.0+

``` source
class VZVirtioFileSystemDeviceConfiguration
```

## Overview

Use `VZVirtioFileSystemDeviceConfiguration` to create a Virtio file system device which allows the host to expose directories to a guest using a tag label.

The example below shows the creation of a `VZVirtioFileSystemDeviceConfiguration` that shares a single directory that the user can manually mount after creating a mount point in the guest VM:

- Swift
- Objective-C

```
// Define a URL to a specific file path, in this case the 
// "Projects" directory in the user's home directory.
let projectsURL = URL(fileURLWithPath: NSHomeDirectory() + "Projects")

static func createSingleDirectoryShareDeviceConfiguration() -> VZVirtioFileSystemDeviceConfiguration {
    let sharedDirectory = VZSharedDirectory(url: projectsURL, readOnly: false)
    let singleDirectoryShare = VZSingleDirectoryShare(directory: sharedDirectory)

    // Create the VZVirtioFileSystemDeviceConfiguration and assign it a unique tag. 
    let sharingConfiguration = VZVirtioFileSystemDeviceConfiguration(tag: "Projects")
    sharingConfiguration.share = singleDirectoryShare

    return sharingConfiguration
}
```

```
    // Define a URL to a specific file path, in this case the
    // "Projects" directory in the user's home directory.
    NSString *projectsPath = [NSHomeDirectory() stringByAppendingPathComponent:@"Projects"];
    NSURL *projectsURL = [NSURL fileURLWithPath:projectsPath];

    VZSharedDirectory *sharedDirectory = [[VZSharedDirectory alloc] initWithURL:projectsURL readOnly:NO];
    VZSingleDirectoryShare *singleDirectoryShare = [[VZSingleDirectoryShare alloc] initWithDirectory:sharedDirectory];

    // Create the VZVirtioFileSystemDeviceConfiguration and assign it a unique tag.
    VZVirtioFileSystemDeviceConfiguration *sharingConfiguration = [[VZVirtioFileSystemDeviceConfiguration alloc] initWithTag:@"Projects"];
    sharingConfiguration.share = singleDirectoryShare;
```

A `VZVirtioFileSystemDeviceConfiguration` can also share multiple directories. The example below demonstrates sharing the `~/Invoices` and `~/Projects` directories from the user’s home directory to the guest VM:

- Swift
- Objective-C

```
// Define URLs at specific file paths, in this case the 
// "Projects" and "Invoices" directories in the user's home directory.
let projectsURL = URL(fileURLWithPath: NSHomeDirectory() + "Projects")
let invoicesURL = URL(fileURLWithPath: NSHomeDirectory() + "Invoices")

static func createMultipleDirectoryShareDeviceConfiguration() -> VZVirtioFileSystemDeviceConfiguration {
    let sharedProjectsDirectory = VZSharedDirectory(url: projectsURL, readOnly: false)

    // It's also possible to share directories that are read-only: 
    let sharedInvoicesDirectory = VZSharedDirectory(url: invoicesURL, readOnly: true)

    // Associate each shared directory with a name, which is how the framework lists them under the mount point.
    let directoriesToShare = ["My Projects": sharedProjectsDirectory, "Invoices": sharedInvoicesDirectory]
    let multipleDirectoryShare = VZMultipleDirectoryShare(directories: directoriesToShare)

    // Create the VZVirtioFileSystemDeviceConfiguration and assign it a unique tag. 
    let sharingConfiguration = VZVirtioFileSystemDeviceConfiguration(tag: "myfiles")
    sharingConfiguration.share = multipleDirectoryShare

    return sharingConfiguration
}
```

```
    // Define URLs at specific file paths, in this case the    
    // "Projects" and "Invoices" directories in the user's home directory.
    NSString *projectsPath = [NSHomeDirectory() stringByAppendingPathComponent:@"Projects"];
    NSString *invoicesPath = [NSHomeDirectory() stringByAppendingPathComponent:@"Invoices"];
    NSURL *projectsURL = [NSURL fileURLWithPath:projectsPath];
    NSURL *invoicesURL = [NSURL fileURLWithPath:invoicesPath];

    VZSharedDirectory *sharedProjectsDirectory = [[VZSharedDirectory alloc] initWithURL:projectsURL readOnly:NO];

    // It's also possible to share directories that are read-only:
    VZSharedDirectory *sharedInvoicesDirectory = [[VZSharedDirectory alloc] initWithURL:invoicesURL readOnly:YES];

    // Associate each shared directory with a name, which is how the framework lists them under the mount point.
    VZMultipleDirectoryShare *multipleDirectoryShare = [[VZMultipleDirectoryShare alloc] initWithDirectories:@{
        @"My Projects": sharedProjectsDirectory,
        @"Invoices": sharedInvoicesDirectory,
    }];

    // Create the VZVirtioFileSystemDeviceConfiguration and assign it a unique tag.
    VZVirtioFileSystemDeviceConfiguration *sharingConfiguration = [[VZVirtioFileSystemDeviceConfiguration alloc] initWithTag:@"myfiles"];
    sharingConfiguration.share = multipleDirectoryShare;
```

### Mounting shared directories

Important

The commands required to mount shared directories in a guest VM aren’t commands that your app can execute or that you can script from inside your application to a VM; the user must perform them either interactively or as part of a script while logged in to the guest. You must communicate these requirements to the user of your app.

Mounting a shared directory requires the user to execute a command in a terminal window, the specific mount command depends on the guest VM’s operating system:

- In macOS guests, use `mount_virtiofs tag directory`.

- In Linux guests, use `mount -t virtiofs tag directory`.

The `tag` argument is the file system device configuration label — `Projects` in the single directory case and `myfiles` in the multiple directory case in these examples — and `directory` is the mount point in the guest file system to which the framework attaches the shared directories.

### Automounting shared directories in macOS VMs

In macOS 13 and later, it’s possible to specify a file system device that macOS 13 or later guest VMs automount using the macOSGuestAutomountTag property. The example below demonstrates sharing a single macOS directory, to a macOS guest:

```
// Define a URL to a specific file path, in this case the 
// "Projects" directory in the user's home directory.
let projectsURL = URL(fileURLWithPath: NSHomeDirectory() + "Projects")

static func createAutomountSingleDirectoryShareDeviceConfiguration() -> VZVirtioFileSystemDeviceConfiguration {
    let sharedDirectory = VZSharedDirectory(url: projectsURL, readOnly: false)
    let singleDirectoryShare = VZSingleDirectoryShare(directory: sharedDirectory)

    // Assign the automount tag to this share. macOS shares automounted directories automatically under /Volumes in the guest.  
    let sharingConfiguration = VZVirtioFileSystemDeviceConfiguration(tag: VZVirtioFileSystemDeviceConfiguration.macOSGuestAutomountTag)
    sharingConfiguration.share = singleDirectoryShare

    return sharingConfiguration
}
```

The macOS guest automounts the user’s `~/Projects` directory from the host and shares it under `/Volumes/My Shared Files/` in the macOS guest.

It’s also possible to automount multiple directories in macOS guests. The example below demonstrates sharing the `~/Invoices` and `~/Projects` directories from the user’s home directory to the macOS guest VM:

```
// Define URLs at specific file paths, in this case the 
// "Projects" and "Invoices" directories in the user's home directory.
let projectsURL = URL(fileURLWithPath: NSHomeDirectory() + "Projects")
let invoicesURL = URL(fileURLWithPath: NSHomeDirectory() + "Invoices")

static func createAutomountMultipleDirectoryShareDeviceConfiguration() -> VZVirtioFileSystemDeviceConfiguration {
    // Share the contents of ~/Projects, which is writeable.
    let sharedProjectsDirectory = VZSharedDirectory(url: projectsURL, readOnly: false)

    // Share the contents of ~/Invoices, but make it read only.
    let sharedInvoicesDirectory = VZSharedDirectory(url: invoicesURL, readOnly: true) 

    // Associate each shared directory with a name, which is how the framework lists them under the mount point in the guest.
    let directoriesToShare = ["My Projects": sharedProjectsDirectory, "Invoices": sharedInvoicesDirectory]
    let multipleDirectoryShare = VZMultipleDirectoryShare(directories: directoriesToShare)

    // Assign the automount tag to this share. macOS will automatically mount each shared directory at /Volumes/My Shared Files.
    let sharingConfiguration = VZVirtioFileSystemDeviceConfiguration(tag: VZVirtioFileSystemDeviceConfiguration.macOSGuestAutomountTag)
    sharingConfiguration.share = multipleDirectoryShare

    return sharingConfiguration
}
```

In the guest, the framework lists each shared directory by its specified name under `/Volumes/My Shared Files`. Here, the shared directories in the macOS guest are `/Volumes/My Shared Files/My Projects` and `/Volumes/My Shared Files/Invoices`.

## Topics

### Creating a file system device configuration

init(tag: String)

Creates a configuration for a VIRTIO file system device.

### Getting file system information

var share: VZDirectoryShare?

A value that defines how the host exposes resources to the guest virtual machine.

var tag: String

A label that identifies this device in the guest VM.

class var macOSGuestAutomountTag: String

A value that indicates that the guest needs to automount this file system device in the guest VM.

### Tag validation

class func validateTag(String) throws

Checks to see whether a Virtio tag is valid.

## Relationships

### Inherits From

- VZDirectorySharingDeviceConfiguration

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSCopying
- NSObjectProtocol

## See Also

### Related Documentation

class VZMultipleDirectoryShare

An object that describes a directory share for multiple directories.

class VZSingleDirectoryShare

An object that defines the directory share for a single directory.

### Configurations

class VZDirectorySharingDeviceConfiguration

The base class for a directory sharing device configuration.

class VZLinuxRosettaDirectoryShare

The Linux directory share for Rosetta.

