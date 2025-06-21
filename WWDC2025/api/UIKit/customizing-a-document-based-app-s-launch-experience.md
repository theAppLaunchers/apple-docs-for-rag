*   [UIKit](/documentation/uikit)
*   [View controllers](/documentation/uikit/view-controllers)
*   Customizing a document-based app’s launch experience

Article

# Customizing a document-based app’s launch experience

Add unique elements to your app’s document launch scene.

## [Overview](/documentation/UIKit/customizing-a-document-based-app-s-launch-experience#overview)

In iOS 18 and later, you can customize the document browsing experience for your app, such as setting the title and action buttons, configuring the background, and adding custom assets to the scene.

SwiftUI equivalent

For information about adopting the document-based launch experience SwiftUI, read [Building a document-based app with SwiftUI](/documentation/SwiftUI/Building-a-document-based-app-with-SwiftUI).

### [Set up a document-based app](/documentation/UIKit/customizing-a-document-based-app-s-launch-experience#Set-up-a-document-based-app)

To create a customized document launch experience, follow these steps:

*   Declare your supported document types in the Document Types section of your app target’s Info tab.
    
*   Set the Supports Document Browser key (`UISupportsDocumentBrowser`) in the Custom iOS Target Properties section of the Info tab.
    
*   Create a [`UIDocument`](/documentation/uikit/uidocument) subclass for each document type your app supports.
    
*   Create a [`UIDocumentViewController`](/documentation/uikit/uidocumentviewcontroller) subclass for your app, and have the subclass adopt the [`UIDocumentBrowserViewControllerDelegate`](/documentation/uikit/uidocumentbrowserviewcontrollerdelegate) protocol.
    
*   Set your document view subclass as your app’s root view controller. Alternatively, you can embed your [`UIDocumentViewController`](/documentation/uikit/uidocumentviewcontroller) subclass in a navigation controller, and set that as the root view controller.
    
*   Implement your delegate’s [`documentDidOpen()`](/documentation/uikit/uidocumentviewcontroller/documentdidopen\(\)) method to configure your document view.
    
*   Configure the launch scene using the document view controller’s [`launchOptions`](/documentation/uikit/uidocumentviewcontroller/launchoptions-swift.property) property.
    

When setting the document type, provide a name and the Uniform Type Identifier for your documents. Add the [`CFBundleTypeRole`](/documentation/BundleResources/Information-Property-List/CFBundleDocumentTypes/CFBundleTypeRole) key with a value of `Viewer` (read-only) or `Editor` (if your app both reads and writes the document type). Finally, add a `UIDocumentClass` key, and set its value to the name of your [`UIDocument`](/documentation/uikit/uidocument) subclass for this document type.

![An Xcode screenshot of the app target’s Document Type settings.](https://docs-assets.developer.apple.com/published/8e73ebd67808b49a364c89a4b356a621/media-4414816%402x.png)

When implementing your [`documentDidOpen()`](/documentation/uikit/uidocumentviewcontroller/documentdidopen\(\)) method, verify that you have a valid document and a valid view before updating the view. For more information, see [`UIDocumentViewController`](/documentation/uikit/uidocumentviewcontroller).

```swift

```swift
override func viewDidLoad() {
    super.viewDidLoad()
    // Configure your launch options.
    mySetupTextView()
}
override func documentDidOpen() {
    mySetupTextView()
}
```swift
```swift
func mySetupTextView() {
```
```
    
    // Make sure you have a valid document.
    guard let document = document as? MyDocument else { return }
            
    // Make sure you have a valid view.
    guard let view else { return }
    
    // Make sure the document is open.
    guard !document.documentState.contains(.closed) else { return }
    // Configure the view.
    textView.text = document.text
}
```

```

### [Create new documents](/documentation/UIKit/customizing-a-document-based-app-s-launch-experience#Create-new-documents)

The document viewer uses app intents to create new documents. It also uses the [`UIDocument.CreationIntent`](/documentation/uikit/uidocument/creationintent) structure to specify the different ways your app can create documents. [`UIDocument`](/documentation/uikit/uidocument) already provides a default intent and the corresponding `.default` enumeration value.

To add your own intents, start by extending [`UIDocument.CreationIntent`](/documentation/uikit/uidocument/creationintent) and adding values for your intents.

```swift

```swift
// Extend the creation intent enumeration to add custom options for document creation.
extension UIDocument.CreationIntent {
    static let template = UIDocument.CreationIntent("template")
}
```

```

Then call the [`UIDocument`](/documentation/uikit/uidocument) class’s [`createDocumentAction(withIntent:)`](/documentation/uikit/uidocumentviewcontroller/launchoptions-swift.class/createdocumentaction\(withintent:\)) method to create the intent. Set the intent’s title, and assign it to your [`UIDocumentViewController.LaunchOptions`](/documentation/uikit/uidocumentviewcontroller/launchoptions-swift.class) instance’s [`primaryAction`](/documentation/uikit/uidocumentviewcontroller/launchoptions-swift.class/primaryaction) or [`secondaryAction`](/documentation/uikit/uidocumentviewcontroller/launchoptions-swift.class/secondaryaction) properties. By default, the system automatically sets the document view controller’s [`primaryAction`](/documentation/uikit/uidocumentviewcontroller/launchoptions-swift.class/primaryaction) to the default create document action.

```swift

```swift
// Provide an action for the secondary action.
```swift
```swift
let templateAction = LaunchOptions.createDocumentAction(withIntent: .template)
```
```
// Set the intent's title.
templateAction.title = "Choose a Template"
// Add the intent to an action.
launchOptions.secondaryAction = templateAction
```

```

Finally, implement the [`UIDocumentBrowserViewControllerDelegate`](/documentation/uikit/uidocumentbrowserviewcontrollerdelegate) protocol’s [`documentBrowser(_:didRequestDocumentCreationWithHandler:)`](/documentation/uikit/uidocumentbrowserviewcontrollerdelegate/documentbrowser\(_:didrequestdocumentcreationwithhandler:\)) method. The system calls this method when something triggers one of the create document intents. In your implementation, use the controller’s [`activeDocumentCreationIntent`](/documentation/uikit/uidocumentbrowserviewcontroller/activedocumentcreationintent) to determine the intent. Create the document, and then pass the URL and the [`UIDocumentBrowserViewController.ImportMode`](/documentation/uikit/uidocumentbrowserviewcontroller/importmode) to the `intentHandler`.

```swift

```swift
override func documentBrowser(_ controller: UIDocumentBrowserViewController, didRequestDocumentCreationWithHandler importHandler: @escaping (URL?, UIDocumentBrowserViewController.ImportMode) -> Void) {
    switch controller.activeDocumentCreationIntent {
    case .template:
        
        // Let someone select a template, and return
        // a URL to that template.
        let templateURL = myPresentTemplateSelection()
        
        // Pass the URL to the import handler.
        importHandler(templateURL, .copy)
        
    default:
        
        // Create the default document.
        let newDocumentURL = myCreateEmptyDocument()
        
        // Pass the URL to the import handler.
        importHandler(newDocumentURL, .move )
    }
}
```

```

### [Customize the document browsing experience](/documentation/UIKit/customizing-a-document-based-app-s-launch-experience#Customize-the-document-browsing-experience)

On iPad, iPhone, and Vision Pro (for compatible iPad apps), the system displays a launch scene that contains a title and any document creation buttons. It also displays the document browser as a sheet over this view. Use your document view controller’s [`launchOptions`](/documentation/uikit/uidocumentviewcontroller/launchoptions-swift.property) property to customize this scene as follows:

*   Set the [`title`](/documentation/uikit/uidocumentviewcontroller/launchoptions-swift.class/title) property to change the name that appears in the title view. By default, the controller uses your app’s name.
    
*   Modify the [`background`](/documentation/uikit/uidocumentviewcontrollerlaunchoptions/background) property to configure the scene’s background.
    
*   Use the [`foregroundAccessoryView`](/documentation/uikit/uidocumentviewcontroller/launchoptions-swift.class/foregroundaccessoryview) or [`backgroundAccessoryView`](/documentation/uikit/uidocumentviewcontroller/launchoptions-swift.class/backgroundaccessoryview) to place [`UIView`](/documentation/uikit/uiview) objects in front of or behind the title view.
    
*   Set the [`primaryAction`](/documentation/uikit/uidocumentviewcontroller/launchoptions-swift.class/primaryaction) or [`secondaryAction`](/documentation/uikit/uidocumentviewcontroller/launchoptions-swift.class/secondaryaction) properties to add buttons to the title view. If you don’t modify the [`primaryAction`](/documentation/uikit/uidocumentviewcontroller/launchoptions-swift.class/primaryaction) property, the controller adds a Create Document button as the default primary action.
    
*   Use [`browserViewController`](/documentation/uikit/uidocumentviewcontroller/launchoptions-swift.class/browserviewcontroller) to access and configure the document browser controller.
    

Typically, you configure the launch options in your view controller’s [`viewDidLoad()`](/documentation/uikit/uiviewcontroller/viewdidload\(\)) method.

```swift

```swift
override func viewDidLoad() {
    super.viewDidLoad()
    
    // Assign the view controller as the browser delegate.
    launchOptions.browserViewController.delegate = self
    
    // Customize launch options.
    launchOptions.title = "My Text Editor"
    launchOptions.background.backgroundColor = .darkGray
    
    // Provide an action for the secondary action.
    let templateAction = LaunchOptions.createDocumentAction(withIntent: .template)
    templateAction.title = "Choose a Template"
    launchOptions.secondaryAction = templateAction
    
    mySetupTextView()
}
```

```

![A screenshot of the document launch scene with the title set to “My Text Editor”. It has the default primary action, and a custom secondary action.](https://docs-assets.developer.apple.com/published/49177beba228e0d1225e5bfac6bed9a5/media-4414815%402x.png)

## [See Also](/documentation/UIKit/customizing-a-document-based-app-s-launch-experience#see-also)

### [Documents and directories](/documentation/UIKit/customizing-a-document-based-app-s-launch-experience#Documents-and-directories)

[

API Reference

Adding a document browser to your app](/documentation/uikit/adding-a-document-browser-to-your-app)

Give users access to their local or remote documents from within your app.

[

Providing access to directories](/documentation/uikit/providing-access-to-directories)

Use a document picker to access the content of a directory outside your app’s container.

[

Building a document browser-based app](/documentation/uikit/building-a-document-browser-based-app)

Use a document browser to provide access to the user’s text files.

[

Building a document browser app for custom file formats](/documentation/uikit/building-a-document-browser-app-for-custom-file-formats)

Implement a custom document file format to manage user interactions with files on different cloud storage providers.

```swift
```swift
```swift
class UIDocumentViewController
```
```

A view controller that manages and presents a document stored locally or in the cloud.
```
```swift
```swift
```swift
class UIDocumentBrowserViewController
```
```

A view controller for browsing and performing actions on documents that you store locally and in the cloud.
```
```swift
```swift
```swift
class UIDocumentPickerViewController
```
```

A view controller that provides access to documents or destinations outside your app’s sandbox.
```
```swift
```swift
```swift
class UIDocumentInteractionController
```
```

A view controller that previews, opens, or prints files with a file format that your app can’t handle directly.
```