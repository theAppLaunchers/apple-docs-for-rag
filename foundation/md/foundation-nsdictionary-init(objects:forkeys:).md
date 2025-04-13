

- Foundation
- NSDictionary
-  init(objects:forKeys:) 

Initializer

# init(objects:forKeys:)

Initializes a newly allocated dictionary with key-value pairs constructed from the provided arrays of keys and objects.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.0+macOS 10.0+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
convenience init(
    objects: [Any],
    forKeys keys: [any NSCopying]
)
```

## Parameters 

`objects`  

An array containing the values for the new dictionary.

`keys`  

An array containing the keys for the new dictionary. Each key is copied (using copy(with:); keys must conform to the `NSCopying` protocol), and the copy is added to the new dictionary.

## Discussion

This method steps through the `objects` and `keys` arrays, creating entries in the new dictionary as it goes. An `NSInvalidArgumentException` is raised if the objects and keys arrays do not have the same number of elements.

## See Also

### Creating a Dictionary from Objects and Keys

init(objects: UnsafePointer&lt;AnyObject>?, forKeys: UnsafePointer&lt;any NSCopying>?, count: Int)

Initializes a newly allocated dictionary with the specified number of key-value pairs constructed from the provided C arrays of keys and objects.

convenience init(object: Any, forKey: any NSCopying)

Creates a dictionary containing a given key and value.

