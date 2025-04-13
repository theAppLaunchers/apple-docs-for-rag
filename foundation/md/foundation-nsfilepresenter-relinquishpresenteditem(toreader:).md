

- Foundation
- NSFilePresenter
-  relinquishPresentedItem(toReader:) 

Instance Method

# relinquishPresentedItem(toReader:)

Notifies your object that another object or process wants to read the presented file or directory.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.0+macOS 10.0+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
optional func relinquishPresentedItem(toReader reader: @escaping ((() -> Void)?) -> Void)
```

## Parameters 

`reader`  

A Block object that takes another block as a parameter and returns no value. The `reacquirer` block is one you pass to the `reader` block so that your object can be notified when the `reader` is done. If your object does not need to be notified, it can pass `nil` for the `reacquirer` block.

## Discussion

You use this method to provide an appropriate response when another object wants to read from your presented URL. For example, when this method is called, you might temporarily stop making changes to the file or directory. After taking any appropriate steps, you must execute the block in the `reader` parameter to let the waiting object know that it may now proceed with its task. If you want to be notified when the reader has completed its task, pass your own block to the reader and use that block to reacquire the file or URL for your own uses.

Important

If you implement this method, you must execute the block in the `reader` parameter as part of your implementation. The system waits for you to execute that block before allowing the `reader` to operate on the file. Therefore, failure to execute the block could stall threads in your application or other processes until the user takes corrective actions.

The following listing shows a simple implementation of this method that sets a Boolean flag that the file being monitored is not writable at the moment. After setting the flag, it executes the reader block and passes in yet another block for the reader to execute when it is done.

```
- (void)relinquishPresentedItemToReader:(void (^)(void (^reacquirer)(void))) reader
{
    // Prepare for another object to read the file.
   self.fileIsWritable = NO;

   // Now let the reader know that it can have the file.
   // But pass a reacquisition block so that this object
   // can update itself when the reader is done.
   reader(^{
      self.fileIsWritable = YES;
   });
}
```

Your implementation of this method is executed using the queue in the presentedItemOperationQueue property. Your reacquirer block is executed on the queue associated with the reader.

## See Also

### Relinquishing Managed Files

func relinquishPresentedItem(toWriter: ((() -> Void)?) -> Void)

Notifies your object that another object or process wants to write to the presented file or directory.

