

- WebKit
- WKWebView
-  loadFileURL(\_:allowingReadAccessTo:) 

Instance Method

# loadFileURL(\_:allowingReadAccessTo:)

Loads the web content from the specified file and navigates to it.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+visionOS 1.0+

``` source
@MainActor
func loadFileURL(
    _ URL: URL,
    allowingReadAccessTo readAccessURL: URL
) -> WKNavigation?
```

## Parameters 

`URL`  

The URL of a file that contains web content. This URL must be a file-based URL.

`readAccessURL`  

The URL of a file or directory containing web content that you grant the system permission to read. This URL must be a file-based URL and must not be empty. To prevent WebKit from reading any other content, specify the same value as the URL parameter. To read additional files related to the content file, specify a directory.

## Return Value

A new navigation object you use to track the loading progress of the request.

## Discussion

This method sets the source of this load request for app activity data to NSURLRequest.Attribution.developer. To specify the source of this load, use loadFileRequest(_:allowingReadAccessTo:) instead.

## See Also

### Loading web content

func load(URLRequest) -> WKNavigation?

Loads the web content that the specified URL request object references and navigates to that content.

func load(Data, mimeType: String, characterEncodingName: String, baseURL: URL) -> WKNavigation?

Loads the content of the specified data object and navigates to it.

func loadHTMLString(String, baseURL: URL?) -> WKNavigation?

Loads the contents of the specified HTML string and navigates to it.

func loadFileRequest(URLRequest, allowingReadAccessTo: URL) -> WKNavigation

Loads the web content from the file the URL request object specifies and navigates to that content.

func loadSimulatedRequest(URLRequest, response: URLResponse, responseData: Data) -> WKNavigation

Loads the web content from the data you provide as if the data were the response to the request.

func loadSimulatedRequest(URLRequest, responseHTML: String) -> WKNavigation

Loads the web content from the HTML you provide as if the HTML were the response to the request.

var isLoading: Bool

A Boolean value that indicates whether the view is currently loading content.

var estimatedProgress: Double

An estimate of what fraction of the current navigation has been loaded.

