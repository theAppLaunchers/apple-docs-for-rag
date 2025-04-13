

- Core Transferable
- ProxyRepresentation
-  exportingCondition(\_:) 

Instance Method

# exportingCondition(\_:)

Prevents the system from exporting an item if it does not meet the supplied condition.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
func exportingCondition(_ condition: @escaping (Self.Item) -> Bool) -> _ConditionalTransferRepresentation
```

## Parameters 

`condition`  

A closure that determines whether the item is exportable. Don’t perform long-running work in this closure. It shouldn’t contain network requests, file operations, or other potentially time-consuming tasks as they can cause delays during operations with `Transferable` items.

## Discussion

Some instances of a model type may have state-dependent conditions that make them unsuitable for export. For example, an `Archive` structure that supports a comma-separated text representation only when it has compatible content:

```
struct Archive {
    var supportsCSV: Bool
    func csvData() -> Data
    init(csvData: Data)
}

extension Archive: Transferable {
    static var transferRepresentation: some TransferRepresentation {
        DataRepresentation(contentType: .commaSeparatedText) { archive in
            archive.csvData()
        } importing: { data in Archive(csvData: data) }
            .exportingCondition { archive in archive.supportsCSV }
    }
}
```

