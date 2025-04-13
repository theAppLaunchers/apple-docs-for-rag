

- UIKit
- UIApplication
-  open(\_:options:completionHandler:) 

Instance Method

# open(\_:options:completionHandler:)

Attempts to asynchronously open the resource at the specified URL.

iOS 10.0+iPadOS 10.0+Mac Catalyst 13.1+tvOS 10.0+visionOS 1.0+

``` source
@MainActor
func open(
    _ url: URL,
    options: [UIApplication.OpenExternalURLOptionsKey : Any] = [:],
    completionHandler completion: (@MainActor (Bool) -> Void)? = nil
)
```

``` source
@MainActor
func open(
    _ url: URL,
    options: [UIApplication.OpenExternalURLOptionsKey : Any] = [:]
) async -> Bool
```

## Parameters 

`url`  

A URL (Universal Resource Locator). The resource identified by this URL may be local to the current app or it may be one that must be provided by a different app. UIKit supports many common schemes, including the `http`, `https`, `tel`, `facetime`, and `mailto` schemes. You can also employ custom URL schemes associated with apps installed on the device.

`options`  

A dictionary of options to use when opening the URL. For a list of possible keys to include in this dictionary, see UIApplication.OpenExternalURLOptionsKey.

`completion`  

The block to execute with the results. Provide a value for this parameter if you want to be informed of the success or failure of opening the URL. This block is executed asynchronously on your app’s main thread. The block has no return value and takes the following parameter:

success  
A Boolean value that indicates whether the URL was opened successfully.

## Discussion

Use this method to open the specified resource. If the specified URL scheme is handled by another app, iOS launches that app and passes the URL to it. (Launching the app brings the other app to the foreground.) If no app is capable of handling the specified scheme, the completion handler is called with the *success* parameter set to false.

To determine whether an app is installed that is capable of handling the URL, call the canOpenURL(_:) method before calling this one. Be sure to read the description of that method for an important note about registering the schemes you want to employ.

## See Also

### Opening a URL resource

func canOpenURL(URL) -> Bool

Returns a Boolean value that indicates whether an app is available to handle a URL scheme.

struct OpenExternalURLOptionsKey

Options for opening a URL.

