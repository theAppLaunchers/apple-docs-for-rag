

- Objective-C Runtime
- NSObjectProtocol
-  perform(\_:) 

Instance Method

# perform(\_:)

Sends a specified message to the receiver and returns the result of the message.

iOS 1.0+iPadOS 1.0+Mac Catalyst 1.0+macOS 10.0+tvOS 1.0+visionOS 1.0+watchOS 1.0+

``` source
func perform(_ aSelector: Selector!) -> Unmanaged!
```

**Required**

## Parameters 

`aSelector`  

A selector identifying the message to send. The message should take no arguments. If `aSelector` is `NULL`, an invalidArgumentException is raised.

## Return Value

An object that is the result of the message.

## Discussion

Calling the perform(_:) method is equivalent to sending the `aSelector` message directly to the receiver. For example, the following both do the same thing if `anObject` is an instance of `MyObject`:

- Swift
- Objective-C

```
let aClone = anObject.copy()
let aClone = anObject.perform(#selector(MyObject.copy)).takeRetainedValue()
```

```
id aClone = [anObject copy];
id aClone = [anObject performSelector:@selector(copy)];
id aClone = [anObject performSelector:sel_getUid("copy")];
```

The perform(_:) method allows you to send messages that aren’t determined until run-time. This means that you can pass a variable selector as the argument:

- Swift
- Objective-C

```
let aSelector = findTheAppropriateSelectorForTheCurrentSituation()
let returnedObject = anObject.perform(aSelector).takeUnretainedValue()
```

```
SEL aSelector = findTheAppropriateSelectorForTheCurrentSituation();
id returnedObject = [anObject performSelector:aSelector];
```

Use caution when doing this. This method returns an implicitly unwrapped optional unmanaged pointer to an `AnyObject` instance (Unmanaged`AnyObject`>!`). It’s up to you to decide how to bring the instance into Swift’s memory management scheme. Different messages require different memory management strategies for their returned objects, and it might not be obvious which to use.

Usually, a caller isn’t responsible for the memory of a returned instance, in which case you use takeUnretainedValue(), as shown above. However, for any of the creation methods, such as copy(), the caller is responsible, and you use takeRetainedValue() instead. See Memory Management Policy in Advanced Memory Management Programming Guide for a description of ownership expectations.

Due to this uncertainty, the compiler generates a warning if you supply a variable selector while using ARC to manage memory. Because it can’t determine ownership of the returned object at compile-time, ARC makes the assumption that the caller does *not* need to take ownership, but this may not be true. The compiler warning alerts you to the potential for a memory leak.

To avoid the warning, if you know that `aSelector` has no return value, you might be able to use performSelector(onMainThread:with:waitUntilDone:) or one of the related methods available in NSObject.

For a more general solution, use NSInvocation to construct a message that you can invoke with an arbitrary argument list and return value.

Alternatively, consider restructuring your code to use blocks as a means of passing chunks of functionality through an API. See Blocks Programming Topics for details.

Important

Because of the inherent lack of type safety, this API isn’t recommended for use in Swift unless your code specifically relies on the dynamic method resolution provided by the Objective-C run-time.

For more information about using selectors in Swift and alternatives to the perform(_:) function, read Using Objective-C Runtime Features in Swift.

## See Also

### Sending Messages

func perform(Selector!, with: Any!) -> Unmanaged&lt;AnyObject>!

Sends a message to the receiver with an object as the argument.

**Required**

func perform(Selector!, with: Any!, with: Any!) -> Unmanaged&lt;AnyObject>!

Sends a message to the receiver with two objects as arguments.

**Required**

