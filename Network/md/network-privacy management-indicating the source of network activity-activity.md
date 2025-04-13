

- Network
- Privacy Management
-  Indicating the source of network activity 

Article

# Indicating the source of network activity

Control whether the App Privacy Report attributes network traffic to the app or to the user.

## Overview

In iOS and iPadOS 15 or later, users can view an App Privacy Report that includes the network domains that apps on the device have recently accessed. The report differentiates between network connections that the user initiates and those that the app initiates.

By default, the system attributes all connections — except those that your app makes using SFSafariViewController or ASWebAuthenticationSession — to the app. However, for network connections that meet certain criteria, you can tell the system to attribute the connection to the user. The API you use to control attribution depends on how you make the network connection.

To learn how to examine all the data your app contributes to the privacy report, see Inspecting app activity data.

### Determine the appropriate attribution

All connections, other than those that use SFSafariViewController or ASWebAuthenticationSession, are classified by default as *app-initiated*. User-initiated network connections are the exception. Network connections to third-party domains can only be classified as *user-initiated* if they meet all of the following criteria:

- User-directed — Network connections to domains that occur only when a user affirmatively chooses to engage with content in your app. For a connection to qualify as user-directed, the user must be provided with a meaningful choice of whether to interact with the content.

- Non-primary functionality — The app’s features must be functional without this particular network connection.

If you don’t categorize your app’s traffic using the APIs, all network connections are classified as app-initiated.

For example, the following connections should retain the app-initiated attribution:

- A podcast app that automatically chooses and downloads podcasts based on the user’s interests. While the loaded content isn’t core to the app, the user has no control over it.

- An app that transmits analytics and other user data for use in improving the app. The access is core to the app’s functionality, and the user has no control over it.

- A maps app that loads and presents content from a review service — for example, for hotels or restaurants — when the user taps on a location pin. The action is core to the app’s functionality, and the user didn’t explicitly request the information.

In contrast, you can attribute these connections to the user:

- Links to user-generated content in a social media app, like when a user clicks or taps a news feed link. The user chooses the link, and the particular link isn’t part of the app’s primary functionality.

- Messages in an email app. The user creates and configures the email account, and no particular email or email account is central to the app’s functionality.

- Pages loaded by a web browser. The user chooses the web sites to visit, and no particular web site is specific to the app’s functionality. Note that connections made by the browser that the user doesn’t choose, like sending analytics data or retrieving user configuration information, should retain app attribution.

To reclassify an access as user-initiated, use API at the same layer of the protocol stack that you use to make the connection.

### Attribute URL Loading System connections

To mark a connection as user-initiated when using the URL Loading System, create an explicit URLRequest and set its attribution property to NSURLRequest.Attribution.user before calling one of the URLSession methods that takes a request, like data(for:delegate:):

```
import Foundation

let url = URL(string: "https://example.com")!
var request = URLRequest(url: url)
request.attribution = .user

let (data, response) = try await URLSession.shared.data(for: request)
```

The NSURLRequest and NSMutableURLRequest classes also have a comparable property. Use this kind of parameterized request for other high level link types as well, as the next few sections describe.

### Attribute WebKit loads

A WebKit network access that you initiate with a URL request using the load(_:) method honors the attribution parameter that you set on the URLRequest instance, just like the previous section describes for a URLSession access. If you want to set an attribution when you use WebKit to load an HTML string, data, or a file URL, use one of the corresponding load methods that takes a request. For example, you can load an HTML string with attribution using the loadSimulatedRequest(_:responseHTML:) method, relying on the `request` defined in the previous section:

```
import WebKit

let webView = WKWebView()
let html = "Hello, world!"

webView.loadSimulatedRequest(request, responseHTML: html)
```

Alternatively, you can load a data version of the same content using the loadSimulatedRequest(_:response:responseData:) method:

```
let data = Data(html.utf8)
let response = URLResponse(
    url: url,
    mimeType: "text/HTML",
    expectedContentLength: data.count,
    textEncodingName: "UTF-8")

webView.loadSimulatedRequest(request, response: response, responseData: data)
```

To load a file called `index.html` from your main bundle’s `resources` directory with user attribution, use the loadFileRequest(_:allowingReadAccessTo:) method:

```
let fileURL = Bundle.main.url(
    forResource: "index",
    withExtension: "html",
    subdirectory: "resources")!

var fileRequest = URLRequest(url: fileURL)
fileRequest.attribution = .user

webView.loadFileRequest(
    fileRequest,
    allowingReadAccessTo: fileURL.deletingLastPathComponent())
```

These load methods — as opposed to their non-request counterparts like loadHTMLString(_:baseURL:) and loadFileRequest(_:allowingReadAccessTo:) — also enable the user to browse backward and forward among the corresponding pages.

### Attribute LinkPresentation metadata fetches

To load link presentation metadata with attribution, use the LPMetadataProvider fetch method that takes a request. Specifically, use the startFetchingMetadata(for:completionHandler:) method — again, relying on the user-attributed `request` value that you defined earlier:

```
import LinkPresentation

let metadataProvider = LPMetadataProvider()
let metadata = try await metadataProvider.startFetchingMetadata(for: request)
```

### Attribute Network framework connections

To control attribution when using the Network framework, set the attribution property of an NWParameters instance to NWParameters.Attribution.user, and use that to create a connection:

```
import Network

let parameters = NWParameters()
parameters.attribution = .user
let endpoint = NWEndpoint.url(url)
let connection = NWConnection(to: endpoint, using: parameters)
```

Alternatively, you can work with an nw_parameters_t instance, and set the attribution to nw_parameters_attribution_t.user with a call to the nw_parameters_set_attribution(_:_:) function:

```
let parameters = nw_parameters_create()
nw_parameters_set_attribution(parameters, .user)
let endpoint = nw_endpoint_create_url("https://example.com")
let connection = nw_connection_create(endpoint, parameters)
```

### Attribute connections made with sockets

To control attribution when working with sockets, import the `ne_socket.h` header file, and use the `ne_socket_set_attribution` function to set the value `NE_SOCKET_ATTRIBUTION_USER` on a socket:

```
#include 
#include 

int tcpSocket = socket(PF_INET, SOCK_STREAM, 0);
if (ne_socket_set_attribution(tcpSocket, NE_SOCKET_ATTRIBUTION_USER) != 0) {
    // Handle error.
}
```

If you use custom DNS resolution, also call `ne_socket_set_domains()` function to associate the resolved domain name (as well as any resolved `CNAME`) with the socket:

```
const char *domains[] = { "resolved.example.com" };
if (ne_socket_set_domains(tcpSocket, domains, 1) != 0) {
    // Handle error.
}
```

This gives the system an opportunity to evaluate whether the resolved domain has been identified as potentially collecting information across apps and sites. After performing any additional configuration, use the socket to create a connection:

```
const struct sockaddr *address = ;
int connectResult = connect(tcpSocket, address, address->sa_len);
```

## See Also

### Traffic Attribution

Inspecting app activity data

Verify that your app accesses only the user data and network resources that you expect it to access.

func nw_parameters_set_attribution(nw_parameters_t, nw_parameters_attribution_t)

Sets a flag that indicates whether the network request originates from the developer or the user.

func nw_parameters_get_attribution(nw_parameters_t) -> nw_parameters_attribution_t

Gets a flag that indicates whether the network request originates from the developer or the user.

enum nw_parameters_attribution_t

The entities that can make a network request.

