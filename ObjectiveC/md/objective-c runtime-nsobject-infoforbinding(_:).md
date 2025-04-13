

- Objective-C Runtime
- NSObject
-  infoForBinding(\_:) 

Instance Method

# infoForBinding(\_:)

Returns a dictionary describing the receiver’s `binding`.

macOS

``` source
func infoForBinding(_ binding: NSBindingName) -> [NSBindingInfoKey : Any]?
```

## Parameters 

`binding`  

The name of a binding.

## Return Value

A dictionary with information about `binding`, or `nil` if the binding is not bound. The dictionary contains three key/value pairs: `NSObservedObjectKey`: object bound, `NSObservedKeyPathKey`: key path bound, `NSOptionsKey`: dictionary with the options and their values for the bindings.

## Discussion

This method is mostly for use by subclasses which want to analyze the existing bindings of an object.

## See Also

### Managing bindings

func valueClassForBinding(NSBindingName) -> AnyClass?

Returns the class of the value that will be returned for the specified binding.

func bind(NSBindingName, to: Any, withKeyPath: String, options: [NSBindingOption : Any]?)

Establishes a binding between a given property of the receiver and the property of a given object specified by a given key path.

func optionDescriptionsForBinding(NSBindingName) -> [NSAttributeDescription]

Returns an array describing the options for the specified binding.

struct NSBindingInfoKey

func unbind(NSBindingName)

Removes a given binding between the receiver and a controller.

func NSIsControllerMarker(_ object: Any?) -> Bool

Tests whether a given object is special marker object used for indicating the state of a selection in relation to a key.

