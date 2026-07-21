  
- AccessoryAccess  
-  AAUSBAccessory  
  
Class  
  
# AAUSBAccessory  
  
A class that represents a USB accessory.  
  
macOS 27.0  
  
``` source  
class AAUSBAccessory  
```  
  
## Discussion  
  
A USB accessory can either be obtained from the usbAccessoryDidConnect(_:) method, or instantiated from an XPC representation that describes an existing USB accessory.  
  
## Topics  
  
### Creating USB accessories  
  
init?(XPCRepresentation: xpc_object_t)  
  
Creates a USB accessory from an XPC representation.  
  
init?(xpcRepresentation: xpc_object_t)  
  
Creates a USB accessory from an XPC representation.  
  
init?(coder: NSCoder)  
  
Creates a new USB accessory with the provided coder.  
  
### Getting information about a USB accessory  
  
var configurationDescriptorData: Data?  
  
Returns the currently selected configuration descriptor data.  
  
var deviceDescriptorData: Data  
  
Returns the device descriptor data.  
  
var registryID: UInt64  
  
Returns the IORegistry ID for the USB accessory.  
  
### Managing a USB accessory  
  
func open(serviceQueue: dispatch_queue_t?, completionHandler: (IOUSBHostDevice, (any Error)?) -> Void)  
  
Opens a connection to the USB accessory for this process to access it exclusively.  
  
func close(completionHandler: ((any Error)?) -> Void)  
  
Closes all connections to the USB accessory for this process.  
  
### Connection and disconnection events  
  
enum Event  
  
Events that represent accessory connection and disconnection.  
  
Encoding a USB accessory for delivery to an XPC service  
  
func createXPCRepresentation() -> xpc_object_t  
  
Creates an encoded representation of the USB accessory.  
  
## Relationships  
  
### Inherits From  
  
NSObject  
  
### Conforms To  
  
- CVarArg  
- CustomDebugStringConvertible  
- CustomStringConvertible  
- Equatable  
- Hashable  
- NSCoding  
- NSObjectProtocol  
- NSSecureCoding  
- Sendable  
- SendableMetatype  
  
## See Also  
  
### Managing accessories  
  
class AAUSBAccessoryManager  
  
A class your app uses to manage USB accessories and the listener objects for those accessories.  
