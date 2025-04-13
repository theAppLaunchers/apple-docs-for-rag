

- Core Audio Types
- AudioChannelLayout
- AudioChannelLayout.UnsafeMutablePointer
-  count 

Instance Property

# count

The number of `AudioChannelDescription`s

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
var count: Int { get nonmutating set }
```

## Discussion

Warning: Setting a new value will not change the allocated size and may result in invalid access past the allocation.

