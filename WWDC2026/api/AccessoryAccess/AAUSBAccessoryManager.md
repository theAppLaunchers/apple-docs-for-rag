  
- AccessoryAccess  
- AAUSBAccessoryManager  
  
Class  
  
# AAUSBAccessoryManager  
  
A class your app uses to manage USB accessories and the listener objects for those accessories.  
  
macOS 27.0+  
  
``` swift  
class AAUSBAccessoryManager  
```  
  
## Discussion  
  
Don’t instantiate an AAUSBAccessoryManager directly, instead obtain the manager through the class property shared.  
  
Use the AAUSBAccessoryManager to manage accessories and register interest in events from USB accessories through AAUSBAccessoryListener objects. When a USB accessory connects to the system, the USB accessory manager notifies the listener and provides it an AAUSBAccessory object that represents this accessory. Your app can open this AAUSBAccessory object exclusively, and use it for performing USB transfers to the connected accessory.  
  
A USB accessory listener receives notifications when a USB accessories connect to or disconnect from the system. These listeners can register or unregister with the USB accessory manager object. The accessory manager notifies your app about the USB accessories as long an accessory’s listener remains registered with the manager. The framework delivers all the notifications to the listener on the internal serial queue of the accessory manager.  
  
The AAUSBAccessoryManager presents UI on behalf of your application, which means you can only use it from an application that implements a UI, that is, one that appears in the Dock.  
  
## Topics  
  
Accessing the shared manager  
  
class var shared: AAUSBAccessoryManager  
  
Returns the shared USB accessory manager object for this process.  
  
Registering and unregistering listeners  
  
func registerListener(any AAUSBAccessoryListener, matchingCriteria: [AAUSBAccessoryMatchingCriteria], completionHandler: ([AAUSBAccessory], (any Error)?) -> Void)  
  
Registers a USB accessory listener.  
  
func unregisterListener(any AAUSBAccessoryListener, completionHandler: () -> Void)  
  
Unregister a previously registered listener.  
  
Finding events that apply to an accessory  
  
func events(matching: [AAUSBAccessoryMatchingCriteria]) async throws -> some AsyncSequence<AAUSBAccessory.Event, Never>  
  
Returns an asynchronous list of events that match the provided criteria.  
  
## Relationships  
  
### Inherits From  
  
NSObject  
  
### Conforms To  
  
CVarArg  
CustomDebugStringConvertible  
CustomStringConvertible  
Equatable  
Hashable  
NSObjectProtocol  
Sendable  
SendableMetatype  
  
## See Also  
  
### Managing accessories  
  
class AAUSBAccessory  
  
A class that represents a USB accessory.  
