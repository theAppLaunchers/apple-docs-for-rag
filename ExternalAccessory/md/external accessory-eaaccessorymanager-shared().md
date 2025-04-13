

- External Accessory
- EAAccessoryManager
-  shared() 

Type Method

# shared()

Returns the shared accessory manager object for the iOS-based device.

iOS 3.0+iPadOS 3.0+Mac Catalyst 13.1+macOS 10.13+tvOS 10.0+visionOS 1.0+

``` source
class func shared() -> EAAccessoryManager
```

## Return Value

The shared accessory manager object.

## Discussion

You should always use this method to obtain the accessory manager object and should not try to create instances directly.

