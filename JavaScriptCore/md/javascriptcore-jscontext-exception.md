

- JavaScriptCore
- JSContext
-  exception 

Instance Property

# exception

A JavaScript exception to be thrown in evaluation of the script.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+macOS 10.9+tvOS 9.0+visionOS 1.0+

``` source
var exception: JSValue! { get set }
```

## Discussion

Before performing a callback from JavaScript to an Objective-C or Swift block or method, the context preserves the prior value of this property and then sets its value to `nil`. After the callback has completed, the context reads the new value of the exception property—if this value is not nil, the context treats the value as an exception to be thrown in JavaScript as a result of the callback. After reading the property (and possibly throwing a JavaScript exception), the context restores the prior value of this property.

By default, JavaScriptCore assigns any uncaught exception to this property, so you can check this property’s value to find uncaught exceptions arising from JavaScript function calls. To change the exception handling behavior, use the exceptionHandler property.

## See Also

### Working with JavaScript global state

var globalObject: JSValue!

The JavaScript global object associated with the context.

var exceptionHandler: ((JSContext?, JSValue?) -> Void)!

A block to be invoked should evaluating a script result in a JavaScript exception being thrown.

var virtualMachine: JSVirtualMachine!

The JavaScript virtual machine to which the context belongs.

var name: String!

A descriptive name for the context.

