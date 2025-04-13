

- IOKit
- IOKit Data Types
-  IODataQueueMemory 

Type Alias

# IODataQueueMemory

A struct mapping to the header region of a data queue.

iOS 16.0+iPadOS 16.0+Mac Catalyst 13.0+macOS 10.0+visionOS 1.0+

``` source
typealias IODataQueueMemory = _IODataQueueMemory
```

## Discussion

This struct is variable sized. The struct represents the data queue header information plus a pointer to the actual data queue itself. The size of the struct is the combined size of the header fields (3 \* sizeof(UInt32)) plus the actual size of the queue region. This size is stored in the queueSize field.

