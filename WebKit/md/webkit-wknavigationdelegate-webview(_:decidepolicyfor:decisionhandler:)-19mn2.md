

- WebKit
- WKNavigationDelegate
-  webView(\_:decidePolicyFor:decisionHandler:) 

Instance Method

# webView(\_:decidePolicyFor:decisionHandler:)

Asks the delegate for permission to navigate to new content after the response to the navigation request is known.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+macOS 10.10+visionOS 1.0+

``` source
@MainActor
optional func webView(
    _ webView: WKWebView,
    decidePolicyFor navigationResponse: WKNavigationResponse,
    decisionHandler: @escaping @MainActor (WKNavigationResponsePolicy) -> Void
)
```

``` source
@MainActor
optional func webView(
    _ webView: WKWebView,
    decidePolicyFor navigationResponse: WKNavigationResponse
) async -> WKNavigationResponsePolicy
```

## Parameters 

`webView`  

The web view from which the navigation request began.

`navigationResponse`  

Descriptive information about the navigation response.

`decisionHandler`  

A completion handler block to call with the results about whether to allow or cancel the navigation. This handler has no return value and takes the following parameter:

policy  
A constant that indicates whether to cancel or allow the navigation. For a list of possible values, see WKNavigationResponsePolicy.

## Mentioned in 

Replacing UIWebView in your app

## Discussion

Use this method to allow or deny a navigation request after the web view receives the response to its original URL request. The `navigationResponse` parameter contains the details of the response, including the type of data that the response contains. If you implement this method, always execute the `decisionHandler` block at some point. You may execute it synchronously from your delegate method’s implementation, or execute it asynchronously after your method returns.

## See Also

### Allowing or denying navigation requests

func webView(WKWebView, decidePolicyFor: WKNavigationAction, preferences: WKWebpagePreferences, decisionHandler: (WKNavigationActionPolicy, WKWebpagePreferences) -> Void)

Asks the delegate for permission to navigate to new content based on the specified preferences and action information.

func webView(WKWebView, decidePolicyFor: WKNavigationAction, decisionHandler: (WKNavigationActionPolicy) -> Void)

Asks the delegate for permission to navigate to new content based on the specified action information.

enum WKNavigationActionPolicy

Constants that indicate whether to allow or cancel navigation to a webpage from an action.

enum WKNavigationResponsePolicy

Constants that indicate whether to allow or cancel navigation to a webpage from a response.

