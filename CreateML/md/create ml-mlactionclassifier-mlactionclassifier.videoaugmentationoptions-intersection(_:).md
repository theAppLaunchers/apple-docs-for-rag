

- Create ML
- MLActionClassifier
- MLActionClassifier.VideoAugmentationOptions
-  intersection(\_:) 

Instance Method

# intersection(\_:)

Returns a new option set with only the elements contained in both this set and the given set.

Create MLSwiftmacOS 10.14+

``` source
func intersection(_ other: Self) -> Self
```

## Parameters 

`other`  

An option set.

## Return Value

A new option set with only the elements contained in both this set and `other`.

## Discussion

This example uses the `intersection(_:)` method to limit the available shipping options to what can be used with a PO Box destination.

```
// Can only ship standard or priority to PO Boxes
let poboxShipping: ShippingOptions = [.standard, .priority]
let memberShipping: ShippingOptions =
        [.standard, .priority, .secondDay]

let availableOptions = memberShipping.intersection(poboxShipping)
print(availableOptions.contains(.priority))
// Prints "true"
print(availableOptions.contains(.secondDay))
// Prints "false"
```

## See Also

### Combining options

func union(Self) -> Self

Returns a new option set of the elements contained in this set, in the given set, or in both.

func formUnion(Self)

Inserts the elements of another set into this option set.

func formIntersection(Self)

Removes all elements of this option set that are not also present in the given set.

func symmetricDifference(Self) -> Self

Returns a new option set with the elements contained in this set or in the given set, but not in both.

func formSymmetricDifference(Self)

Replaces this set with a new set containing all elements contained in either this set or the given set, but not in both.

