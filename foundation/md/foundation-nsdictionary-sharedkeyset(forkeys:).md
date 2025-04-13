

- Foundation
- NSDictionary
-  sharedKeySet(forKeys:) 

Type Method

# sharedKeySet(forKeys:)

Creates a shared key set object for the specified keys.

iOS 6.0+iPadOS 6.0+Mac Catalyst 13.1+macOS 10.8+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
class func sharedKeySet(forKeys keys: [any NSCopying]) -> Any
```

## Parameters 

`keys`  

The array of keys. If the parameter is nil, an exception is thrown. If the array of keys is empty, an empty key set is returned.

## Return Value

A shared key set object.

## Discussion

The array of `keys` may contain duplicates which are quietly ignored. Duplicate hash values of the keys are quietly allowed, but may cause lower performance and increase memory usage.

Typically you would create a shared key set for a given set of keys once, before creating shared key dictionaries, and retain and save the result of this method for use with the NSMutableDictionary class method `dictionaryWithSharedKeySet:.`

