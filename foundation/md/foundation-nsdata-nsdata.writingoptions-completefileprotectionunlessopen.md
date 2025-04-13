

- Foundation
- NSData
- NSData.WritingOptions
-  completeFileProtectionUnlessOpen 

Type Property

# completeFileProtectionUnlessOpen

An option to allow the file to be accessible while the device is unlocked or the file is already open.

iOS 5.0+iPadOS 5.0+Mac Catalyst 13.1+macOS 11.0+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
static var completeFileProtectionUnlessOpen: NSData.WritingOptions { get }
```

## Discussion

In this case, your app cannot open the file to read it or write to it when the device is locked, but your app can create new files with this class. If one of these files is open when the device is locked, your app can read and write to the opened file.

## See Also

### Constants

static var atomic: NSData.WritingOptions

An option to write data to an auxiliary file first and then replace the original file with the auxiliary file when the write completes.

static var withoutOverwriting: NSData.WritingOptions

An option that attempts to write data to a file and fails with an error if the destination file already exists.

static var noFileProtection: NSData.WritingOptions

An option to not encrypt the file when writing it out.

static var completeFileProtection: NSData.WritingOptions

An option to make the file accessible only while the device is unlocked.

static var completeFileProtectionUntilFirstUserAuthentication: NSData.WritingOptions

An option to allow the file to be accessible after a user first unlocks the device.

static var fileProtectionMask: NSData.WritingOptions

An option the system uses when determining the file protection options that the system assigns to the data.

static var atomic: NSData.WritingOptions

An option to write data to an auxiliary file first and then replace the original file with the auxiliary file when the write completes.

static var withoutOverwriting: NSData.WritingOptions

An option that attempts to write data to a file and fails with an error if the destination file already exists.

static var noFileProtection: NSData.WritingOptions

An option to not encrypt the file when writing it out.

static var completeFileProtection: NSData.WritingOptions

An option to make the file accessible only while the device is unlocked.

static var completeFileProtectionUntilFirstUserAuthentication: NSData.WritingOptions

An option to allow the file to be accessible after a user first unlocks the device.

static var fileProtectionMask: NSData.WritingOptions

An option the system uses when determining the file protection options that the system assigns to the data.

