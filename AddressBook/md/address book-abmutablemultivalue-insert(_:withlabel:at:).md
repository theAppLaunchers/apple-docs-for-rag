

- Address Book
- ABMutableMultiValue
-  insert(\_:withLabel:at:) 

Instance Method

# insert(\_:withLabel:at:)

Inserts a value and its label at the given index in a multivalue list.

macOS

``` source
func insert(
    _ value: Any!,
    withLabel label: String!,
    at index: Int
) -> String!
```

## Parameters 

`value`  

The value to add.

`label`  

The label to associate with the value.

`index`  

The index where the value will be inserted.

## Return Value

The identifier of the inserted value and label if they are added successfully; otherwise, `nil`.

## Discussion

If either the value or the label is `nil` or if the index is out of bounds, this method raises an exception

This method performs no type checking and will let you add a value whose type does not match the types of the other values in the list. However, if you try to use a multivalue list whose values are not all of the same type, other methods, such as the `ABRecord` setValue(_:forProperty:) method, will return false or `kABErrorInProperty`.

## See Also

### Adding a value

func add(Any!, withLabel: String!) -> String!

Adds a value and its label to a multivalue list.

