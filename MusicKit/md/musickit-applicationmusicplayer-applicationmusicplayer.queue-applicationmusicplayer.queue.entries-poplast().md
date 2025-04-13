

- MusicKit
- ApplicationMusicPlayer
- ApplicationMusicPlayer.Queue
- ApplicationMusicPlayer.Queue.Entries
-  popLast() 

Instance Method

# popLast()

Removes and returns the last element of the collection.

MusicKitSwiftiOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+

``` source
mutating func popLast() -> Self.Element?
```

Available when `Self` conforms to `BidirectionalCollection`.

## Return Value

The last element of the collection if the collection is not empty; otherwise, `nil`.

## Discussion

Calling this method may invalidate all saved indices of this collection. Do not rely on a previously stored index value after altering a collection with any operation that can change its length.

Complexity

O(1)

