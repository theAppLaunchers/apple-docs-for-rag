

- UIKit
- UIViewController
-  encodeRestorableState(with:) 

Instance Method

# encodeRestorableState(with:)

Encodes state-related information for the view controller.

iOS 6.0+iPadOS 6.0+Mac Catalyst 13.1+tvOSvisionOS 1.0+

``` source
@MainActor
func encodeRestorableState(with coder: NSCoder)
```

## Parameters 

`coder`  

The coder object to use to encode the state of the view controller.

## Discussion

Do not call this method directly. The system calls this method during the state preservation process to give your view controller or view-controller subclass a chance to save state-related information.

When deciding what data to save, write the smallest amount of data needed to restore the view controller to its current configuration. The information you save should be data that you could not easily recreate, such as the user’s current selection. You might also save references to any data objects that the view controller was using, but never write the data objects themselves to the coder. Instead, store enough information so that you can retrieve the data objects from your app’s main data structures again.

Important

This method is not a substitute for saving your app’s data structures persistently to disk. You should continue to save your app’s actual data to iCloud or the local file system using existing techniques. This method is intended only for saving configuration state or other information related to your app’s user interface. You should consider any data you write to the coder as purgeable and be prepared for it to be unavailable during subsequent launches.

It is strongly recommended that you call `super` at some point during your implementation to give parent classes an opportunity to save information. A UIViewController object saves a reference to the presented view controller and to the storyboard (if any) that was used to create the view controller. The view controller also asks the views in its view hierarchy to save any relevant information. However, a view controller does not automatically save references to contained child view controllers. If you are implementing a custom container view controller, you must encode the child view controller objects yourself if you want them to be preserved.

Your implementation of this method can encode other restorable objects views, view controllers, and objects that adopt the UIStateRestoring protocol, using the encode(_:forKey:) method of the provided coder object. Encoding a restorable object writes that object’s restoration identifier to the coder. That identifier is then used during the decode process to locate the new version of the object. If the view or view controller defines its own version of this method, that method is also called at some point so that the object can encode its own state.

For objects that are not restorable, encoding the object writes its data (and not a restoration identifier) to the archive. Such objects must adopt the NSCoding protocol. During decoding, the system creates a new object that is initialized with the data from the archive.

## See Also

### Managing state restoration

Restoring your app’s state

Provide continuity for the user by preserving current activities.

var restorationIdentifier: String?

The identifier that determines whether the view controller supports state restoration.

var restorationClass: (any UIViewControllerRestoration.Type)?

The class responsible for recreating this view controller when restoring the app’s state.

func decodeRestorableState(with: NSCoder)

Decodes and restores state-related information for the view controller.

func applicationFinishedRestoringState()

Called on restored view controllers after other object decoding is complete.

