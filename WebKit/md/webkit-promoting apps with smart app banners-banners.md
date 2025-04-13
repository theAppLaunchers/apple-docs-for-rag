

- WebKit
-  Promoting Apps with Smart App Banners 

Article

# Promoting Apps with Smart App Banners

Create a banner to promote your app on the App Store from a website.

## Overview

Smart App Banners vastly improve users’ browsing experience compared to other promotional methods. In iOS, Smart App Banners provide a consistent look and feel that users come to recognize. They trust that tapping the banner will take them to the App Store and not a third-party advertisement. They appreciate unobtrusive banners at the top of a webpage, instead of a full screen that interrupts their experience with the web content. And with a large and prominent Close button, a banner is easy to dismiss. When the user returns to the webpage, the banner doesn’t reappear.

If the app is already installed on a user’s device, the Smart App Banner intelligently changes its action, and tapping the banner simply opens the app. If the user doesn’t have your app on their device, tapping the banner takes them to the app’s entry in the App Store. When they return to your website, a progress bar appears in the banner, indicating how much longer the download will take to complete. When the app finishes downloading, the View button changes to an Open button, and tapping the banner opens the app while preserving the user’s content from your website.

Smart App Banners automatically determine whether the user’s device supports your app. If it doesn’t, or if your app is unavailable in the user’s location, the banner doesn’t appear.

### Implement a Smart App Banner on Your Website

To add a Smart App Banner to your website, include the following meta tag in the `head` element of each page where you’d like the banner to appear:

```

```

You can include two comma-separated parameters in the content attribute:

`app-id`  
Required. Your app’s unique identifier. To find your app ID from App Store Marketing Tools, type the name of your app in the Search field, and select the appropriate country or region and media type. In the results, select your app. In the detail view for your app, find the Content Link. Your app ID is the number between `id` and `?`. Alternatively, select your app in App Store Connect. Under General, select App Information, then find your app ID in the General Information section that opens in the middle of the screen; your app ID is listed as Apple ID.

`app-argument`  
Optional. A URL that provides context to your native app. If you include the URL and the user has your app installed, they can jump from your website to the corresponding position in your iOS app.

Typically, it’s beneficial to retain navigational context because:

- If the user is deep within the navigational hierarchy of your website, you can pass the document’s entire URL, and then parse it in your app to reroute the user to the correct location in your app.

- If the user performs a search on your website, you can pass the query string so the user can seamlessly continue the search in your app without having to retype their query.

- If the user is in the midst of creating content, you can pass the session ID to download the web session state to your app so the user can nondestructively resume their work.

You can generate the `app-argument` parameter for each page dynamically with a server-side script. You can format it however you like, as long as it’s a valid URL.

Note

You can’t display Smart App Banners inside a frame. Banners don’t appear in the iOS simulator.

### Provide Navigational Context to Your App

Implement the application(_:open:sourceApplication:annotation:): method in your app delegate, which fires when your app is launched from a URL. Then provide logic that can interpret the URL you pass. The value you set for the `app-argument` parameter is available as the NSURL url object.

The code sample below is for a website that passes data to a native iOS app. It first detects whether the URL contains the string `/profile`. If so, it opens the profile view controller and passes the profile ID number that’s in the query string.

```
```

## See Also

### Safari Support

Optimizing Your Website for Safari

Improve your website by optimizing it for Safari.

Delivering Video Content for Safari

Improve the performance and appearance of video in your website in Safari.

