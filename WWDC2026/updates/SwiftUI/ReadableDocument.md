- SwiftUI
- WritableDocument

Protocol

# ReadableDocument

A document type that supports reading from file.

iOS 27.0+ iPadOS 27.0+ Mac Catalyst 27.0+ macOS 27.0+ visionOS 27.0+

```swift
protocol ReadableDocument : AnyObject
```

## Overview

Conform to ReadableDocument to build a read-only document viewer, or combine with WritableDocument (via the Document protocol) for full read-write support.

A readable document is a reference type so that SwiftUI can maintain a stable identity across updates. Use @Observable to enable per-property change tracking:

```swift
@Observable
final class MarkdownViewer: ReadableDocument {
    static let readableContentTypes: [UTType] = [.markdown]


    var attributedText = AttributedString()


    func reader(configuration: sending ReadConfiguration) -> sending FileWrapperDocumentReader<String> {
        FileWrapperDocumentReader(configuration) { fileWrapper in
            guard let data =
                fileWrapper.regularFileContents else {
                throw CocoaError(.fileReadCorruptFile)
            }
            return String(decoding: data, as: UTF8.self)
        }
    }


    @MainActor
    func apply(snapshot: sending String, previous: sending String?) async throws {
        attributedText = try AttributedString(
            markdown: snapshot
        )
    }
}
```


Present a read-only document with DocumentGroup using the viewer initializer:

```swift
DocumentGroup { document in
    MarkdownView(document: document)
} makeReadableDocument: { configuration, context in
    MarkdownViewer()
}
```

Set CFBundleTypeRole to Viewer in your Info.plist for read-only document types.

## Topics

### Reading a document

static var readableContentTypes: [UTType]

The content types this document can open.

Required

typealias ReadConfiguration

The configuration for reading document contents.

associatedtype Reader : DocumentReader

A type that implements reading from disk.

Required

func reader(configuration: sending Self.ReadConfiguration) -> sending Self.Reader

Creates a reader to load this document from disk.

Required

func apply(snapshot: sending Self.Reader.Snapshot, previous: sending Self.Reader.Snapshot?) async throws

Applies a loaded snapshot to the document model.

Required

static var writableContentTypes: [UTType]

By default, a document that supports reading also supports writing the same content types.

## Relationships

### Inherited By

Document

## See Also

### Storing document data in a reference type instance

protocol Document

A document that supports both reading and writing.

protocol WritableDocument

A document type that supports writing to file.

class URLDocumentConfiguration

The configuration of an open document that stores its file URL, last modification date, and related metadata.

struct DocumentCreationContext

Context about how a document was created.

protocol DocumentBaseBox

A Box that allows setting its Document base not requiring the caller to know the exact types of the box and its base.