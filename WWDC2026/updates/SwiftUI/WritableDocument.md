- SwiftUI
- WritableDocument

Protocol

# WritableDocument

A document type that supports writing to file.

iOS 27.0+ iPadOS 27.0+ Mac Catalyst 27.0+ macOS 27.0+ visionOS 27.0+

```swift
protocol WritableDocument : AnyObject
```

## Overview

Conform to WritableDocument to add save and export capabilities. Most documents also conform to ReadableDocument — use the Document protocol as a shorthand for both.

The document saving has three steps:

- SwiftUI calls snapshot(contentType:) on the main actor.
- SwiftUI calls writer(configuration:) to get a writer.
- The writer’s DocumentWriter/write(content:to:previous:progress:) runs in the background with coordinated file access.

Important

Without registered undo actions, SwiftUI won’t trigger autosave. Register undo actions with the undo manager from the View environment for every user-facing change.

Example using FileWrapperDocumentWriter:

```swift
@Observable
final class NoteDocument: WritableDocument {
    static let writableContentTypes: [UTType] = [.markdown]


    var text = ""


    func writer(configuration: sending WriteConfiguration) -> sending FileWrapperDocumentWriter<String> {
        FileWrapperDocumentWriter(configuration) { snapshot, _ in
            FileWrapper(
                regularFileWithContents: Data(snapshot.utf8)
            )
        }
    }


    @MainActor
    func snapshot(contentType: UTType) async throws -> sending String { text }
}
```

Register undo actions in the view using the environment’s UndoManager. This ensures SwiftUI detects unsaved changes and triggers autosave:

```swift
struct NoteEditorView: View {
    @Bindable var document: NoteDocument
    @Environment(\.undoManager) private var undoManager


    var body: some View {
        TextEditor(text: $document.text)
            .onChange(of: document.text) { oldValue, _ in
                undoManager?.registerUndo(
                    withTarget: document
                ) { document in
                    document.text = oldValue
                }
            }
    }
}
```

## Topics

### Writing a document

static var writableContentTypes: [UTType]

The content types this document can save or export to.

Required

typealias WriteConfiguration

The configuration for writing document contents.

associatedtype Writer : DocumentWriter

A type that implements writing to disk.

Required

func writer(configuration: sending Self.WriteConfiguration) -> sending Self.Writer

Creates a writer to save this document to disk.

Required

func snapshot(contentType: UTType) async throws -> sending Self.Writer.Snapshot

Captures the document’s current state for saving.

Required

## Relationships

### Inherited By

Document

## See Also

### Storing document data in a reference type instance

protocol Document

A document that supports both reading and writing.

protocol ReadableDocument

A document type that supports reading from file.

class URLDocumentConfiguration

The configuration of an open document that stores its file URL, last modification date, and related metadata.

struct DocumentCreationContext

Context about how a document was created.

protocol DocumentBaseBox

A Box that allows setting its Document base not requiring the caller to know the exact types of the box and its base.