

- Objective-C Runtime
- NSObject
-  keyPathsForValuesAffectingValue(forKey:) 

Type Method

# keyPathsForValuesAffectingValue(forKey:)

Returns a set of key paths for properties whose values affect the value of the specified key.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.1+macOS 10.5+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
class func keyPathsForValuesAffectingValue(forKey key: String) -> Set
```

## Parameters 

`key`  

The key whose value is affected by the key paths.

## Discussion

When an observer for the key is registered with an instance of the receiving class, key-value observing itself automatically observes all of the key paths for the same instance, and sends change notifications for the key to the observer when the value for any of those key paths changes.

The default implementation of this method searches the receiving class for a method whose name matches the pattern `+keyPathsForValuesAffecting`, and returns the result of invoking that method if it is found. Any such method must return an NSSet. If no such method is found, an NSSet that is computed from information provided by previous invocations of the now-deprecated setKeys:triggerChangeNotificationsForDependentKey: method is returned, for backward binary compatibility.

You can override this method when the getter method of one of your properties computes a value to return using the values of other properties, including those that are located by key paths. Your override should typically call `super` and return a set that includes any members in the set that result from doing that (so as not to interfere with overrides of this method in superclasses).

Note

You must not override this method when you add a computed property to an existing class using a category, overriding methods in categories is unsupported. In that case, implement a matching `+keyPathsForValuesAffecting` to take advantage of this mechanism.

## See Also

### Observing Customization

class func automaticallyNotifiesObservers(forKey: String) -> Bool

Returns a Boolean value that indicates whether the observed object supports automatic key-value observation for the given key.

var observationInfo: UnsafeMutableRawPointer?

Returns a pointer that identifies information about all of the observers that are registered with the observed object.

