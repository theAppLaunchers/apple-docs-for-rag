

- Foundation
-  CFBridgingRetain(\_:) 

Function

# CFBridgingRetain(\_:)

Casts an Objective-C pointer to a Core Foundation pointer and also transfers ownership to the caller.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.0+macOS 10.0+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func CFBridgingRetain(_ X: Any?) -> CFTypeRef?
```

## Discussion

You use this function to cast an Objective-C object as Core Foundation-style object and take ownership of the object so that you can manage its lifetime. You are responsible for subsequently releasing the object, as illustrated in this example:

```
NSString *string = ;
CFStringRef cfString = (CFStringRef)CFBridgingRetain(string);
// Use the CF string.
CFRelease(cfString);
```

