

- XCTest
- Activities and Attachments
-  Adding Attachments to Tests, Activities, and Issues 

Article

# Adding Attachments to Tests, Activities, and Issues

Use attachments to store a test’s output data for later analysis.

## Overview

Tests often produce output such as files, images, screenshots, and data during their execution. You can store this test output for later analysis by wrapping it in an XCTAttachment instance and adding it to the current test, activity, or issue. You can then view these attachments within Xcode’s test results browser alongside the test, activity, or issue that created them.

XCTAttachment provides several convenience initializers to create attachments for common data types, such as images, screenshots, files, folders, strings, and custom objects, that conform to NSSecureCoding or that you can encode as a property list. Alternatively, you can attach custom test output by creating an attachment from raw data in memory.

You associate an attachment with a test by calling the add(_:) method on an instance of a type that conforms to the XCTActivity protocol. XCTestCase automatically conforms to XCTActivity so you can add an attachment to the current test by calling add(_:) from within any test method.

Listing 1. Attaching a screenshot of an app’s first window to the current test.

```
class MainWindowScreenshotTests: XCTestCase {
    func testTakeScreenshotOfMainWindow() {
        let app = XCUIApplication()
        app.launch()
        let screenshot = app.windows.firstMatch.screenshot()
        let attachment = XCTAttachment(screenshot: screenshot)
        attachment.lifetime = .keepAlways
        add(attachment)
    }
}
```

Alternatively, you can create and run a custom activity by calling the XCTContext runActivityNamed:block: class method from anywhere in your testing code. This method runs a user-provided block of test code, passing an XCTActivity instance to the block. Call add(_:) on this XCTActivity instance to add an attachment to the activity instead of the overall test.

Every attachment you create has a uniformTypeIdentifier property containing a Uniform Type Identifier (UTI) that identifies the type of content in the attachment. Many of XCTAttachment’s convenience initializers determine an appropriate UTI to use from their provided content. Alternatively, you can provide a manual UTI value to represent a custom data format to use in your app.

Listing 2. Adding attachments in response to a background data download

```
func testDownloadAndAttachWebData() {

    // Create an expectation for a background download task.
    let expectation = XCTestExpectation(description: "Download apple.com home page")

    // Create a URL for a web page to download.
    let url = URL(string: "https://apple.com")!

    // Create a background task to download the web page.
    let dataTask = URLSession.shared.dataTask(with: url) { (data, urlResponse, error) in

        // Process the download task's response, adding some of its output as attachments.

        if let error = error {

            XCTFail("Data failed to download with an error: \(error.localizedDescription).")

        } else if let httpURLResponse = urlResponse as? HTTPURLResponse, httpURLResponse.statusCode != 200 {

            // Attach the response's header fields as an XML property list.              
            let headers = XCTAttachment(plistObject: httpURLResponse.allHeaderFields)
            headers.name = "Headers"

            let description = "Unexpected status code: \(httpURLResponse.statusCode)."
            var issue = XCTIssue(type: .assertionFailure, compactDescription: description)
            issue.add(headers)
            self.record(issue)

        } else if let data = data {

            // Attach the retrieved HTML data with an appropriate UTI.
            let html = XCTAttachment(data: data, uniformTypeIdentifier: "public.html")
            html.name = "HTML"
            // Keep the HTML attachment even when the test succeeds.
            html.lifetime = .keepAlways
            self.add(html)

        }

        // Fulfill the expectation to indicate that the background task has finished.
        expectation.fulfill()

    }

    // Start the download task.
    dataTask.resume()

    // Wait until the expectation is fulfilled, with a timeout of 10 seconds.
    wait(for: [expectation], timeout: 10.0)

}
```

Listing 2 performs an integration test of a web page download. The download occurs on a background thread.

The code above produces one of three outcomes from the results of the download:

- If the data task returns an error, the test fails and logs the error’s description as part of the failure.

- If the data task succeeds, but has an HTTP response status code of anything other than `200 OK`, the sample code adds the response’s header fields to a new `XCTIssue` as an XML property list attachment to assist with debugging the problem.

- If the data task succeeds and retrieves some data, the sample code adds the retrieved data to the test as an attachment with a UTI of `public.html`, enabling Xcode to provide an appropriate Quick Look for the data within the Xcode test results browser. The sample code sets the attachment’s lifetime property to XCTAttachment.Lifetime.keepAlways to store the HTML data even though the test succeeds.

See `Testing Asynchronous Operations with Expectations` for more information.

### Attachment Lifetime

By default, when the test passes successfully, it discards the test’s attachments to save storage. To persist an attachment even when its test passes, set the attachment’s lifetime property to XCTAttachment.Lifetime.keepAlways rather than the default value of XCTAttachment.Lifetime.deleteOnSuccess. Alternatively, change the default lifetime for an entire test scheme by deselecting the “Attachments: Delete when each test succeeds” option in the Options tab of the scheme’s Test scheme action.

## See Also

### Attachments

class XCTAttachment

Data from a test method’s execution, such as a file, image, screenshot, data blob, or ZIP file.

