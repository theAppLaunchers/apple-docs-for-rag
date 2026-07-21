# DiskImageKit/DiskImage  
  
- DiskImageKit  
-  DiskImageKit.DiskImage  
  
Class  
  
# DiskImage  
  
The representation of an open disk image  
  
macOS 27.0+  
  
``` swift  
class DiskImage  
```  
  
## Overview  
  
To use a disk image as storage for virtual machine, use this object with the Virtualization API method init(diskImage:cachingMode:synchronizationMode:). In addition, it contains properties that describe the disk image and operations to manipulate it.  
  
An image can either be standalone or part of a stack. For more information on stacked disk image, see StackedImage.  
  
The following example demonstrates how to create a stacked disk image with 3 layers:  
  
``` swift  
// Open the base image.  
let baseImage = try DiskImage(opening: .open(url: baseImageURL))  
  
// Append a new cache layer,  
var stackedImage = try baseImage.appending(.asifLayer(url: cacheURL, type: .cache))  
  
// Append an existing overlay layer,  
let overlayImage = try DiskImage(opening: .open(url: overlayURL))  
stackedImage = try stackedImage.appending(overlayImage)  
  
// Append a new overlay layer.  
stackedImage = try stackedImage.appending(.asifLayer(url: overlayURL, type: .overlay))  
```  
  
The example demonstrates how to create a standalone, 512 GB (1 billion block) ASIF disk image:  
  
``` swift  
_ = try DiskImage(creating: .asif(url: imageURL, blockCount: 1000000000, blockSize: .bytes512))  
```  
  
## Topics  
  
### Protocols  
  
protocol CreationConfiguration  
  
A marker protocol for disk image creation configurations.  
  
protocol StackableLayer  
  
A marker protocol that stackable disk image layer configuration objects conform to.  
  
### Structures  
  
struct LayerType  
  
An enumeration that defines the type of a layer in a stacked disk image.  
  
### Initializers  
  
convenience init(creating: some DiskImage.CreationConfiguration) throws  
  
Creates a new, empty disk image.  
  
convenience init(opening: some OpenConfigurationProtocol) throws  
  
Opens an existing disk image using the specified image URL.  
  
### Instance Properties  
  
var blockCount: Int  
  
The number of blocks in the disk image.  
  
var blockSize: DiskImage.BlockSize  
  
The block size, either 512 bytes or 4 KB.  
  
var format: DiskImage.Format  
  
The format of the disk image.  
  
var layerType: DiskImage.LayerType?  
  
The layer type of the disk image.  
  
var layerUUID: UUID?  
  
A UUID of the image that the framework uses to validate its compatibility with the layer above it in the stack  
  
var openMode: OpenConfiguration.Mode  
  
The open mode of the disk image, read-only or read-write.  
  
var parentUUID: UUID?  
  
A UUID of the image that must be equal to the layer UUID of the layer beneath it in the stack.  
  
var size: Int  
  
The logical size of the disk image in bytes.  
  
let url: URL  
  
The URL of the disk image.  
  
### Instance Methods  
  
func appending(any DiskImage.CreationConfiguration & DiskImage.StackableLayer) throws -> any StackedImage  
  
Appends a new layer to this disk image, creating or extending a stack  
  
func appending(consuming DiskImage) throws -> any StackedImage  
  
Appends a layer to this disk image, creating or extending a stack.  
  
func truncate(blockCount: Int) throws  
  
Truncate or extend the disk image to a new size.  
  
### Enumerations  
  
enum BlockSize  
  
Values that represent the block size of a disk image.  
  
enum Format  
  
Values that describe the disk image formats DiskImageKit supports.  
  
## Relationships  
  
### Inherited By  
  
StackedImage  
  
## See Also  
  
### Essential Types  
  
protocol StackedImage  
  
The protocol for stacked disk images that contain multiple layers.  
  
protocol OpenConfigurationProtocol  
  
The protocol for disk image open configurations.  
  
struct OpenConfiguration  
  
A configuration to use for opening existing disk images.  
  
enum Mode  
  
Open modes for disk images.  
