

- Objective-C Runtime
- NSObject
-  newScriptingObject(of:forValueForKey:withContentsValue:properties:) 

Instance Method

# newScriptingObject(of:forValueForKey:withContentsValue:properties:)

Creates and returns an instance of a scriptable class, setting its contents and properties, for insertion into the relationship identified by the key.

macOS 10.5+

``` source
func newScriptingObject(
    of objectClass: AnyClass,
    forValueForKey key: String,
    withContentsValue contentsValue: Any?,
    properties: [String : Any]
) -> Any?
```

## Parameters 

`objectClass`  

The class of the scriptable object to be created.

`key`  

A key that identifies the relationship into which the new class object will be inserted.

`contentsValue`  

Specifies the contents of the object to be created. This may be `nil`. (See also the Discussion section.)

`properties`  

The properties to be set in the new object. (See also the Discussion section.)

## Return Value

The new object. Returns `nil` if an error occurs.

## Discussion

You can override the `newScriptingObjectOfClass` method to take more control when your application is sent a `make` command. This method is invoked on the prospective container of the new object. The `contentsValue` and `properties` are derived from the `with contents` and `with properties` parameters of the `make` command. The returned objects or objects are then inserted into the container using key-value coding.

When this method is invoked by Cocoa, neither the contents value nor the properties will have yet been coerced using the `NSScriptKeyValueCoding` method coerceValue(_:forKey:). For sdef-declared scriptability, however, the types of the passed-in objects reliably match the relevant sdef declarations.

The default implementation of this method creates new scripting objects by sending `alloc` to a class and `init` to the resulting object. You override this method for situations where this is not sufficient, such as in Core Data applications, in which new objects must be initialized with `[NSManagedObject initWithEntity:insertIntoManagedObjectContext:]`.

## See Also

### Scripting

var classCode: FourCharCode

The receiver’s Apple event type code, as stored in the `NSScriptClassDescription` object for the object’s class.

var className: String

A string containing the name of the class.

func copyScriptingValue(Any, forKey: String, withProperties: [String : Any]) -> Any?

Creates and returns one or more scripting objects to be inserted into the specified relationship by copying the passed-in value and setting the properties in the copied object or objects.

var scriptingProperties: [String : Any]?

An `NSString`-keyed dictionary of the receiver’s scriptable properties.

func scriptingValue(for: NSScriptObjectSpecifier) -> Any?

Given an object specifier, returns the specified object or objects in the receiving container.

