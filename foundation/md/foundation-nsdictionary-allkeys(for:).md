

- Foundation
- NSDictionary
-  allKeys(for:) 

Instance Method

# allKeys(for:)

Returns a new array containing the keys corresponding to all occurrences of a given object in the dictionary.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.0+macOS 10.0+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func allKeys(for anObject: Any) -> [Any]
```

## Parameters 

`anObject`  

The value to look for in the dictionary.

## Return Value

A new array containing the keys corresponding to all occurrences of `anObject` in the dictionary. If no object matching `anObject` is found, returns an empty array.

## Discussion

Each object in the dictionary is sent an isEqual(_:) message to determine if it’s equal to `anObject`.

## See Also

### Accessing Keys and Values

var allKeys: [Any]

A new array containing the dictionary’s keys, or an empty array if the dictionary has no entries.

var allValues: [Any]

A new array containing the dictionary’s values, or an empty array if the dictionary has no entries.

func value(forKey: String) -> Any?

Returns the value associated with a given key.

func objects(forKeys: [Any], notFoundMarker: Any) -> [Any]

Returns as a static array the set of objects from the dictionary that corresponds to the specified keys.

func object(forKey: Any) -> Any?

Returns the value associated with a given key.

subscript(any NSCopying) -> Any?

Returns the value associated with a given key.

subscript(Any) -> Any?

Accesses the value associated with a given key.

