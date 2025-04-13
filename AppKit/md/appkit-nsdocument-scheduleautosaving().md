

- AppKit
- NSDocument
-  scheduleAutosaving() 

Instance Method

# scheduleAutosaving()

Schedules periodic autosaving for the purpose of crash protection.

macOS 10.7+

``` source
@MainActor
func scheduleAutosaving()
```

## Discussion

The default implementation of this method checks to see if autosaving is turned on and, if so and if `[self hasUnautosavedChanges]` returns true, schedules an `NSTimer` to invoke autosave(withDelegate:didAutosave:contextInfo:) in the future. If `[self hasUnautosavedChanges]` returns false it unschedules any previously scheduled timer. It takes care not to cause autosave(withDelegate:didAutosave:contextInfo:) to be invoked before a previous invocation caused by it has finished. The exact timings it uses are complicated and subject to change in future releases of macOS. You can override this method to control when exactly periodic autosaving happens. It is invoked by updateChangeCount(_:) and updateChangeCount(withToken:for:).

## See Also

### Autosaving the Document

func checkAutosavingSafety() throws

Returns a Boolean value that indicates whether it is safe to autosave document changes.

var hasUnautosavedChanges: Bool

A Boolean value that indicates whether the document has changes that have not been autosaved.

func autosave(withDelegate: Any?, didAutosave: Selector?, contextInfo: UnsafeMutableRawPointer?)

Autosaves the document’s contents to an appropriate location in the file system.

func autosave(withImplicitCancellability: Bool, completionHandler: ((any Error)?) -> Void)

Autosaves the document’s contents to an appropriate file-system location, as needed.

var backupFileURL: URL?

The URL for the document’s backup file that was created during an autosave operation.

