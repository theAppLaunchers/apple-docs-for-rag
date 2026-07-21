AccessoryAccess  
  
- AccessoryAccess  
-  Accessory Access  
#   
Framework  
  
# Accessory Access  
  
Manage access to connected USB accessories.  
  
macOS 27.0+  
  
## Topics  
  
### Managing accessories  
  
class AAUSBAccessoryManager  
  
A class your app uses to manage USB accessories and the listener objects for those accessories.  
  
class AAUSBAccessory  
  
A class that represents a USB accessory.  
  
### Identifying specific USB accessories  
  
class AAUSBAccessoryMatchingCriteria  
  
A class that represents the accessory matching criteria for a USB accessory.  
  
### Responding to changes in accessory status  
  
protocol AAUSBAccessoryListener  
  
A class that conforms to the framework’s USB accessory listener protocol can listen to the accessory events.  
  
### Errors  
  
struct AAError  
  
Values that describe errors the AccessoryAccess framework returns.  
  
let AAErrorDomain: String  
  
The string that represents the framework’s error domain.  
