

- Core ML
- MLUpdateProgressEvent
-  init(rawValue:) 

Initializer

# init(rawValue:)

Creates a progress event for the given integer.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.1+macOS 10.15+tvOS 14.0+visionOS 1.0+watchOS 6.0+

``` source
init(rawValue: Int)
```

## Discussion

You do not use this initializer directly. Get update event types from the type properties, such as trainingBegin, miniBatchEnd, or epochEnd.

