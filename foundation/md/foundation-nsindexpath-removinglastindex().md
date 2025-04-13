

- Foundation
- NSIndexPath
-  removingLastIndex() 

Instance Method

# removingLastIndex()

Returns an index path with the nodes in the receiving index path, excluding the last one.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.0+macOS 10.0+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func removingLastIndex() -> IndexPath
```

## Return Value

A new index path with the receiving index path’s indexes, excluding the last one.

## Discussion

Returns an empty `NSIndexPath` instance if the receiving index path’s length is 1 or less.

### Special Considerations

In OS X v10.4 this method returns `nil` when the length of the receiving index path is 1 or less. On iOS and macOS 10.5 and later this method never returns `nil`.

## See Also

### Adding and Removing Nodes

func adding(Int) -> IndexPath

Returns an index path containing the nodes in the receiving index path plus another given index.

