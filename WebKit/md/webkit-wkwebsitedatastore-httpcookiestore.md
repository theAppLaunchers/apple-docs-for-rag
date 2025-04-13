

- WebKit
- WKWebsiteDataStore
-  httpCookieStore 

Instance Property

# httpCookieStore

The object that manages the HTTP cookies for your website.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.1+macOS 10.13+visionOS 1.0+

``` source
@MainActor
var httpCookieStore: WKHTTPCookieStore { get }
```

## Discussion

Use the WKHTTPCookieStore object in this property to manage your website’s cookies. A cookie store object contains methods to add new cookies, and to remove cookies that don’t apply to your content. For example, you might initially use this object to add a cookie for the user’s login credentials and then delete that cookie when the user logs out.

