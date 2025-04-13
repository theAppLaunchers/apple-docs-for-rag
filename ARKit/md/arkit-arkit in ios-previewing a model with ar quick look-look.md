

- ARKit
- ARKit in iOS
-  Previewing a Model with AR Quick Look 

Article

# Previewing a Model with AR Quick Look

Display a model or scene that the user can move, scale, and share with others.

## Overview

AR Quick Look enables the user to place virtual content that you provide on any surface that ARKit finds in the real-world environment. Users can interact with your virtual content by moving and scaling it using touch gestures, or by sharing it with others through the iOS share sheet.

### Choose an Input Format

You provide content for your AR experience in `.usdz` or `.reality` format:

- To browse a library of `.usdz` files, see the AR Quick Look Gallery.

- To browse a library of `.reality` assets, use Reality Composer. For more information, see `Creating 3D Content with Reality Composer`.

Note

If you include a Reality Composer file (`.rcproject`) in your app’s Copy Files build phase, Xcode automatically outputs a converted `.reality` file in your app bundle at build time.

### Display an AR Experience in Your App

In your app, you enable AR Quick Look by providing QLPreviewController with a supported input file. The following code demonstrates previewing a scene named `myScene` from the app bundle.

```
import UIKit
import QuickLook
import ARKit

class ViewController: UIViewController, QLPreviewControllerDataSource {

    override func viewDidAppear(_ animated: Bool) {
        let previewController = QLPreviewController()
        previewController.dataSource = self
        present(previewController, animated: true, completion: nil)
    }

    func numberOfPreviewItems(in controller: QLPreviewController) -> Int { return 1 }

    func previewController(_ controller: QLPreviewController, previewItemAt index: Int) -> QLPreviewItem {
        guard let path = Bundle.main.path(forResource: "myScene", ofType: "reality") else { fatalError("Couldn't find the supported input file.") }
        let url = URL(fileURLWithPath: path)
        return url as QLPreviewItem
    }    
}
```

To prevent the user from scaling your virtual content or to customize the default share sheet behavior, use ARQuickLookPreviewItem instead of QLPreviewItem.

### Display an AR Experience in Your Web Page

In your web page, you enable AR Quick Look by linking a supported input file.

```

```

When the user clicks the link in Safari or within a web view that’s displayed in your app, iOS presents your scene in an AR Quick Look view on your behalf. For more information, see Viewing Augmented Reality Assets in Safari for iOS.

## See Also

### AR Quick Look

Adding Visual Effects in AR Quick Look and RealityKit

Balance the appearance and performance of your AR experiences with modeling strategies.

Adding an Apple Pay Button or a Custom Action in AR Quick Look

Provide a banner that users can tap to make a purchase or perform a custom action in an AR experience.

class ARQuickLookPreviewItem

An object for customizing the AR Quick Look experience.

USDZ schemas for AR

Add augmented reality functionality to your 3D content using USDZ schemas.

Specifying a lighting environment in AR Quick Look

Add metadata to your USDZ file to specify its lighting characteristics.

