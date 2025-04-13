

- Core Transferable
- ProxyRepresentation
-  suggestedFileName(\_:) 

Instance Method

# suggestedFileName(\_:)

Provides a filename to use if the receiver chooses to write the item to disk.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+watchOS 10.0+

``` source
func suggestedFileName(_ fileName: @escaping (Self.Item) -> String?) -> some TransferRepresentation
```

## Parameters 

`fileName`  

The optional closure that returns the suggested filename including the filename extension. If several suggested file names are specified on an item, only the last one will be used.

## Discussion

Any transfer representation can be written to disk.

```
struct Note: Transferable {
    var title: String
    var body: String
    static var transferRepresentation: some TransferRepresentation {
        ProxyRepresentation(exporting: \.body)
            .suggestedFileName { $0.title + ".txt" }
     }
 }
```

