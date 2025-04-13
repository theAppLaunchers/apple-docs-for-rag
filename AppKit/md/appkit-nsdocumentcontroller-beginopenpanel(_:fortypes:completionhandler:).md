

- AppKit
- NSDocumentController
-  beginOpenPanel(\_:forTypes:completionHandler:) 

Instance Method

# beginOpenPanel(\_:forTypes:completionHandler:)

Presents a nonmodal Open dialog that displays files you can open from a list of UTIs.

macOS 10.8+

``` source
@MainActor
func beginOpenPanel(
    _ openPanel: NSOpenPanel,
    forTypes inTypes: [String]?,
    completionHandler: @escaping (Int) -> Void
)
```

``` source
@MainActor
func beginOpenPanel(
    _ openPanel: NSOpenPanel,
    forTypes inTypes: [String]?
) async -> Int
```

## Parameters 

`openPanel`  

The Open dialog to present.

`inTypes`  

A list of file types that the user can choose from in the Open dialog.

`completionHandler`  

The completion handler that runs when the user clicks the OK or Cancel button in the Open dialog.

The block takes the following parameter:

`result`  
Either NSOKButton or NSCancelButton, depending on which button the user clicks to dismiss the dialog.

## Discussion

openDocument(_:) and beginOpenPanel(completionHandler:) call this method to do the actual work. You typically don’t call this method directly. Override this method as necessary to customize the Open dialog or to alter the list of UTIs in the `inTypes` parameter.

You can also override this method if you want to perform additional cleanup (for example, if you customize the Open dialog and need to tear down an accessory view). Your overridden implementation needs to call the underlying method on `super`, passing a custom completion handler. That handler does the additional cleanup work, and then calls the completion handler block that the caller provides.

## See Also

### Managing the Open Dialog

func beginOpenPanel(completionHandler: ([URL]?) -> Void)

Presents an Open dialog and delivers the results to a completion handler as an array of URLs for the chosen files (or `nil`).

func runModalOpenPanel(NSOpenPanel, forTypes: [String]?) -> Int

Presents a modal Open dialog and limits selection to specific file types.

var currentDirectory: String?

The directory path to be used as the starting point in the Open panel.

func urlsFromRunningOpenPanel() -> [URL]?

An array of URLs corresponding to the files selected in a running open panel.

