

- JavaScriptCore
-  JSExport 

Protocol

# JSExport

The protocol for exporting Objective-C objects to JavaScript.

iOS 16.0+iPadOS 16.0+Mac Catalyst 13.0+macOS 10.5+tvOS 9.0+visionOS 1.0+

``` source
protocol JSExport
```

## Overview

Implement this protocol to export your Objective-C classes and their instance methods, class methods, and properties to JavaScript code.

### Export Objective-C Objects to JavaScript

When you create a JavaScript value from an instance of an Objective-C class, and the JSValue class doesn’t specify a copying convention, JavaScriptCore creates a JavaScript wrapper object. For certain classes, JavaScriptCore automatically copies values to the appropriate JavaScript type; for example, NSString instances become JavaScript strings.

JavaScript supports inheritance using a chain of prototype objects. For each Objective-C class you export, JavaScriptCore creates a prototype within the enclosing JavaScript context (a JSContext object). For the NSObject class, the prototype object is the JavaScript context’s `Object` prototype. For all other Objective-C classes, JavaScriptCore creates a prototype object with an internal `[Prototype]` property that points to the prototype property it creates for the Objective-C class’s superclass. As such, the prototype chain for a JavaScript wrapper object reflects the wrapped Objective-C type’s inheritance hierarchy.

In addition to the prototype object, JavaScriptCore produces a JavaScript constructor object for each Objective-C class.

### Expose Objective-C Methods and Properties to JavaScript

By default, no methods or properties of the Objective-C class have exposure to JavaScript. Instead, you must choose methods and properties to export. For each protocol that a class conforms to, if the protocol incorporates the JSExport protocol, JavaScriptCore interprets that protocol as a list of methods and properties to export to JavaScript.

For each instance method you export, JavaScriptCore creates a corresponding JavaScript function as a property of the prototype object. For each Objective-C property you export, JavaScriptCore creates a JavaScript accessor property on the prototype. For each class method you export, JavaScriptCore creates a JavaScript function on the constructor object. The following code example illustrates adoption of the JSExport protocol:

```
@protocol MyPointExports 
@property double x;
@property double y;
- (NSString *)description;
- (instancetype)initWithX:(double)x y:(double)y;
+ (MyPoint *)makePointWithX:(double)x y:(double)y;
@end

@interface MyPoint : NSObject 
- (void)myPrivateMethod;  // This isn't in the MyPointExports protocol, so it isn't visible to JavaScript code.
@end

@implementation MyPoint
// ...
@end
```

The following code example illustrates the API that an exported class presents in JavaScript:

```
```

The attributes of an Objective-C `@property` declaration determine the attributes of the corresponding JavaScript property as follows:

- If the Objective-C property is `readonly`, the JavaScript property has the attributes `writable: false`, `enumerable: false`, `configurable: true`.

- If the Objective-C property is `readwrite`, the JavaScript property has the attributes `writable: true`, `enumerable: true`, `configurable: true`.

Wrapped Objective-C properties, parameters, and return values convert according to the copying convention that the JSValue class specifies for their types. See JSValue for the complete list of copying conventions.

Note

If a class declares conformance to the JSExport protocol, JavaScriptCore ignores its normal copying conventions for built-in types. For example, if you define a custom NSString subclass that conforms to the JSExport protocol and pass an instance of that class to the `valueWithObject:` method, the result is a JavaScript wrapper object for the custom class, not a JavaScript string primitive.

### Customize Export of Objective-C Selectors

When exporting a selector that takes one or more arguments, JavaScriptCore generates a corresponding function name using the following conversion:

- It removes all colons from the selector.

- It capitalizes any lowercase letter that follows a colon.

For example, under the default conversion, the Objective-C selector `doX:withY:` exports as the JavaScript function `doXWithY`.

Note

You can only apply the `JSExportAs` macro to a selector that takes one or more arguments.

To rename a selector that you export to JavaScript, use the `JSExportAs` macro. For example, to instead export the Objective-C selector `doX:withY:` as the JavaScript function `doX`, use the following declaration:

```
@protocol MyClassJavaScriptMethods 
JSExportAs(doX,
- (void)doX:(id)x withY:(id)y
);
@end
```

