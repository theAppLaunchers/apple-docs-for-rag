

- AppKit
- NSDocument
-  performActivity(withSynchronousWaiting:using:) 

Instance Method

# performActivity(withSynchronousWaiting:using:)

Waits for any work scheduled by previous invocations of this method to complete, then invokes the passed-in block.

macOS 10.7+

``` source
@MainActor
func performActivity(
    withSynchronousWaiting waitSynchronously: Bool,
    using block: @escaping (@escaping () -> Void) -> Void
)
```

## Parameters 

`waitSynchronously`  

If true, the method does not return until previous activities are complete and the passed-in block has been invoked. If false, the method might return before passed-in block is invoked. It might instead be invoked later, on the main thread, after previous activities are complete.

`block`  

A block that performs work that might result in the presentation of a modal dialog.

## Discussion

The block is passed another block, the activity completion handler, which must be invoked when the activity is complete.

This method’s primary use is to wait for asynchronous saving. With asynchronous saving it is possible for the user to instigate a user interface action that might present modal dialog, a sheet for example, when asynchronous saving is about to fail and present an error alert sheet of its own, which would not work. This method solves that problem. If your `NSDocument` subclass supports asynchronous saving you should invoke this method around the performance of any work that might cause the presentation of a modal dialog, regardless of whether that work is performed synchronously or asynchronously. Here is a list of `NSDocument` methods whose default implementations invoke this method because they might present sheets, either to ask the user what to do as they begin their work or because they may fail and present errors to user:

- revertToSaved(_:)

- save(withDelegate:didSave:contextInfo:)

- runModalSavePanel(for:delegate:didSave:contextInfo:)

- save(to:ofType:for:delegate:didSave:contextInfo:)

- canClose(withDelegate:shouldClose:contextInfo:)

- duplicate(withDelegate:didDuplicate:contextInfo:)

- runModalPageLayout(with:delegate:didRun:contextInfo:)

- print(withSettings:showPrintPanel:delegate:didPrint:contextInfo:)

- runModalPrintOperation(_:delegate:didRun:contextInfo:)

More uses of this method may be added to `NSDocument` in the future.

This method must be invoked on the main thread. If true is passed for the `waitSynchronously` parameter, the method waits on the main thread, blocking further user interaction with the document. The purpose of blocking the main thread is so that the user cannot continue to change the document while an activity is pending. This prevents, for example, the situation in which the user chooses to revert the document, but reverting does not happen immediately because asynchronous saving is still in progress, yet the user is able to continue changing the document, and then those changes are immediately discarded when the asynchronous saving is complete and the document is reverted. All of the `NSDocument` methods listed above pass true for `waitSynchronously`.

You pass false for `waitSynchronously` when the work to be done is instigated by the user so indirectly that the work might begin when a modal dialog is already being presented. For example, another method whose default implementation invokes this method, this time passing false for `waitSynchronously`, is:

autosave(withDelegate:didAutosave:contextInfo:)

This method might present an error alert, but it is typically invoked by a timer. If it passed true for `waitSynchronously`, and the timer fired while the user was looking at a sheet presented by a previous activity, blocking of the main thread would prevent the handling of the user interface events necessary to dismiss that sheet and complete that previous activity. Deadlock would result.

Whether you make this method wait synchronously or asynchronously to do your work is separate from whether your work is done synchronously or asynchronously. For example, as mentioned above, save(to:ofType:for:delegate:didSave:contextInfo:) passes true for `waitSynchronously` when it uses this method, even though the majority of the work it does may be done asynchronously.

You should not invoke this method during the invocation of the block passed to performSynchronousFileAccess(_:) or in between the time performAsynchronousFileAccess(_:) invokes the block passed to it and the time at which the corresponding file access completion handler is invoked. If you do, deadlock can result. In other words, you cannot begin a new activity as part of file access. You can, on the other hand, invoke performSynchronousFileAccess(_:) or performAsynchronousFileAccess(_:) as part of an activity.

Some asynchronous activities, such as saving, need to do work on the main thread as they are completing. A deadlock would be inevitable if there were no way to interrupt this method’s blocking of the main thread. See continueAsynchronousWorkOnMainThread(_:) to find out how to interrupt this method’s blocking of the main thread.

## See Also

### Performing Tasks Serially

func performSynchronousFileAccess(() -> Void)

Waits for any scheduled file access to complete, then invokes the passed-in block.

func performAsynchronousFileAccess((() -> Void) -> Void)

Waits for any scheduled file access to complete but without blocking the main thread, then invokes the passed-in block.

func continueActivity(() -> Void)

Continues to perform the task for a user activity object using a different block.

func continueAsynchronousWorkOnMainThread(() -> Void)

Invokes the passed-in block on the main thread.

