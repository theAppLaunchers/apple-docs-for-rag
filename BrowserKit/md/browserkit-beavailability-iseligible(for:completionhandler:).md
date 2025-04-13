

- BrowserKit
- BEAvailability
-  isEligible(for:completionHandler:) 

Type Method

# isEligible(for:completionHandler:)

Tests whether the device is eligible to use an app that contains an alternative browser engine.

iOS 18.4+iPadOS 18.4+

``` source
class func isEligible(
    for context: BEAvailability.Context,
    completionHandler: @escaping (Bool, (any Error)?) -> Void
)
```

``` source
class func isEligible(for context: BEAvailability.Context) async throws -> Bool
```

## Parameters 

`context`  

The type of app for which you test eligibility.

`completionHandler`  

A closure that receives the result of the eligibility check, and an error if any occurs.

## Discussion

The completion handler in the synchronous version of this method receives `true` as its first parameter if the device is eligible to run a version of the app that contains an alternative browser engine; otherwise, it receives `false`. The second parameter that the completion handler receives is an error if any occurs; otherwise, it’s `nil`.

The `async` version of this method returns `true` if the device is eligible to run a version of the app that contains an alternative browser engine; otherwise, it returns `false`. The method throws an error if it encounters one.

To use the BEAvailability.Context.webBrowser context to test whether the device is eligible to use a web browser with an alternative browser engine, your app needs to have the com.apple.developer.web-browser entitlement. For information on adopting the web browser entitlement, see Preparing your app to be the default web browser.

