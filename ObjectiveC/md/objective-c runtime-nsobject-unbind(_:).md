

- Objective-C Runtime
- NSObject
-  unbind(\_:) 

Instance Method

# unbind(\_:)

Removes a given binding between the receiver and a controller.

macOS

``` source
func unbind(_ binding: NSBindingName)
```

## Parameters 

`binding`  

The name of a binding.

## See Also

### Managing bindings

func valueClassForBinding(NSBindingName) -> AnyClass?

Returns the class of the value that will be returned for the specified binding.

func bind(NSBindingName, to: Any, withKeyPath: String, options: [NSBindingOption : Any]?)

Establishes a binding between a given property of the receiver and the property of a given object specified by a given key path.

func optionDescriptionsForBinding(NSBindingName) -> [NSAttributeDescription]

Returns an array describing the options for the specified binding.

func infoForBinding(NSBindingName) -> [NSBindingInfoKey : Any]?

Returns a dictionary describing the receiver’s `binding`.

struct NSBindingInfoKey

func NSIsControllerMarker(_ object: Any?) -> Bool

Tests whether a given object is special marker object used for indicating the state of a selection in relation to a key.

