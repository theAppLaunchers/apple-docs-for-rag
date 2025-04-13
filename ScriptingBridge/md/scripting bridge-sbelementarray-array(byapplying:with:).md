

- Scripting Bridge
- SBElementArray
-  array(byApplying:with:) 

Instance Method

# array(byApplying:with:)

Returns an array containing the results of sending the specified message to each object in the receiver.

Mac Catalyst 13.0+macOS 10.5+

``` source
func array(
    byApplying aSelector: Selector,
    with argument: Any
) -> [Any]
```

## Parameters 

`argument`  

The value for the parameter of the message identified by `selector`.

## Return Value

A new array containing the results of sending the `selector` message to each object in the receiver, starting with the first object and continuing through the element array to the last object.

## Discussion

The method identified by `selector` must take a single argument—whose value is provided in `argument`—and must return an object. It should not have the side effect of modifying the receiving array. The order of the items in the result array corresponds to the order of the items in the original array.

## See Also

### Filtering an Element Array

func array(byApplying: Selector) -> [Any]

Returns an array containing the results of sending the specified message to each object in the receiver.

