

- UIKit
- UIApplicationDelegate
-  application(\_:handleEventsForBackgroundURLSession:completionHandler:) 

Instance Method

# application(\_:handleEventsForBackgroundURLSession:completionHandler:)

Tells the delegate that events related to a URL session are waiting to be processed.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+tvOSvisionOS 1.0+

``` source
@MainActor
optional func application(
    _ application: UIApplication,
    handleEventsForBackgroundURLSession identifier: String,
    completionHandler: @escaping () -> Void
)
```

``` source
@MainActor
optional func application(
    _ application: UIApplication,
    handleEventsForBackgroundURLSession identifier: String
) async
```

## Parameters 

`application`  

Your singleton app object.

`identifier`  

The identifier of the URL session requiring attention. If your app was just launched, you can use this identifier to create a new URLSession object that can receive the events.

`completionHandler`  

The completion handler to call when you finish processing the events. Calling this completion handler lets the system know that your app’s user interface is updated and a new snapshot can be taken.

## Discussion

The app calls this method after all background transfers associated with an URLSession object are done, whether they finished successfully or resulted in an error. The app also calls this method if authentication is required for one or more transfers.

Use this method to reconnect any URL sessions and to update your app’s user interface. For example, you might use this method to update progress indicators or to incorporate new content into your views. After processing the events, execute the block in the `completionHandler` parameter so that the app can take a new snapshot of your user interface.

If a URL session finishes its work when your app is not running, the system launches your app in the background so that it can process the event. In that situation, use the provided `identifier` to create a new URLSessionConfiguration and URLSession object. You must configure the other options of your URLSessionConfiguration object in the same way that you did when you started the uploads or downloads. Upon creating and configuring the new URLSession object, that object calls the appropriate delegate methods to process the events.

If your app already has a session object with the specified `identifier` and is running or suspended, you do not need to create a new session object using this method. Suspended apps are moved into the background. As soon as the app is running again, the URLSession object with the identifier receives the events and processes them normally.

At launch time, the app does not call this method if there are uploads or downloads in progress but not yet finished. If you want to display the current progress of those transfers in your app’s user interface, you must recreate the session object yourself. In that situation, cache the identifier value persistently and use it to recreate your session object.

## See Also

### Downloading data in the background

enum UIBackgroundFetchResult

Constants that indicate the result of a background fetch operation.

