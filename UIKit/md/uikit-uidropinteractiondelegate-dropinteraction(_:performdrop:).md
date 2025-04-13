

- UIKit
- UIDropInteractionDelegate
-  dropInteraction(\_:performDrop:) 

Instance Method

# dropInteraction(\_:performDrop:)

Tells the delegate it can request the item provider data from the session’s drag items.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.1+visionOS 1.0+

``` source
@MainActor
optional func dropInteraction(
    _ interaction: UIDropInteraction,
    performDrop session: any UIDropSession
)
```

## Parameters 

`interaction`  

The interaction that called this method.

`session`  

The session containing the drag items.

## Mentioned in 

Making a view into a drop destination

## Discussion

You can request a drag item’s itemProvider data within the scope of this method only and not at any other time.

To request the data, iterate over the session items calling loadObject(ofClass:completionHandler:) on each item’s item provider. For example, if you are expecting the drag items to be images, here’s how you can load each image:

```
func dropInteraction(_ interaction: UIDropInteraction, performDrop session: UIDropSession) {
    for item in session.items {
        let itemProvider = item.itemProvider
        guard itemProvider.canLoadObject(ofClass: UIImage.self) 
        else {continue}

        itemProvider.loadObject(ofClass: UIImage.self, completionHandler: { (object, error) in
            if let image = object as? UIImage {
                DispatchQueue.main.async {
                    self.imageView.image = image
                }
            }
        })
    }
}
```

If you need to be more specific about the type of data to load, use one of the following methods to specify the desired data type using its uniform type identifier (UTI):

- loadDataRepresentation(forTypeIdentifier:completionHandler:)

- loadFileRepresentation(forTypeIdentifier:completionHandler:)

- loadInPlaceFileRepresentation(forTypeIdentifier:completionHandler:)

If you want only JPEG images, use the UTI for the JPEG image type:

```
import MobileCoreServices // for kUTTypeJPEG
func dropInteraction(_ interaction: UIDropInteraction, performDrop session: UIDropSession) {
    for item in session.items {
        let itemProvider = item.itemProvider
        itemProvider.loadDataRepresentation(forTypeIdentifier: kUTTypeJPEG as String, completionHandler: { (data, error) in
            guard
                let data = data,
                let image = UIImage(data: data)
                else {return}

            DispatchQueue.main.async {
                self.imageView.image = image
            }        
        })
    }
}
```

You can also use the session’s convenience method loadObjects(ofClass:completion:) to load the data for an item. Note that the completion handler for this method is called on the main thread, which is not true when loading the data from the item provider.

```
func dropInteraction(_ interaction: UIDropInteraction, performDrop session: UIDropSession) {
    session.loadObjects(ofClass: UIImage.self) { objects in
        guard let images = objects as? [UIImage] else {return}
        for image in images {
            self.imageView.image = image
        }
    }
}
```

When you ask the session or item provider to load its data, it gives you a Progress object. You can also get the progress for the session at a later time from its progress property.

The Progress object tells you how much of the data transfer is complete and if the transfer has finished. What’s more, it can be used to cancel, pause, and resume the data-load process.

## See Also

### Handling the drop

func dropInteraction(UIDropInteraction, canHandle: any UIDropSession) -> Bool

Asks the delegate whether it can handle the session’s drag items.

