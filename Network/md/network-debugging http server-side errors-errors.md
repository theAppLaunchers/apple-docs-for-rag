

- Network
-  Debugging HTTP Server-Side Errors 

Article

# Debugging HTTP Server-Side Errors

Understand HTTP server-side errors and how to debug them.

## Overview

Apple’s HTTP APIs report transport errors and server-side errors:

- A transport error occurs due to a problem getting your request to, or getting the response from, the server. This NSError value is typically passed to your completion handler block or to a delegate method like urlSession(_:task:didCompleteWithError:). If you get a transport error, investigate what is happening with your network traffic. To get started, read Choosing a Network Debugging Tool.

- A server-side error occurs due to problems detected by the server. The statusCode property of the HTTPURLResponse contains the error.

The status codes returned by the server aren’t always easy to interpret (see Section 6, *Response Status Codes*, of RFC 7231) . Many HTTP server-side errors don’t give you a way to determine, from the client side, what went wrong. These include the 5xx errors (like *500 Internal Server Error*) and many 4xx errors (for example, with *400 Bad Request*, it’s hard to know exactly why the server considers the request bad).

Note

Xcode 13 includes the HTTP Tracing instrument to aid in debugging HTTP issues. See Analyzing HTTP traffic with Instruments.

The following sections explain how to debug these server-side problems.

### Print the HTTP Response Body

In some cases, the error response from the server includes an HTTP response body that explains what the problem is. Look at the HTTP response body to see whether such an explanation is present. If it is, that’s the easiest way to figure out what went wrong. For example, consider this standard URLSession request code.

```
URLSession.shared.dataTask(with: url) { (responseBody, response, error) in
    if let error = error {
        // Handle transport error.
    }
    let response = response as! HTTPURLResponse
    let responseBody = responseBody!
    if !(200...299).contains(response.statusCode) {
        // Handle HTTP server-side error.
    }
    // Handle success.
    print("success")
}.resume()
```

A server-side error runs the line labeled “Handle HTTP server-side error.” To see if the server’s response contains any helpful hints as to what went wrong, add some code that prints the HTTP response body.

```
        // Handle HTTP server-side error.
        if let responseString = String(bytes: responseBody, encoding: .utf8) {
            // The response body seems to be a valid UTF-8 string, so print that.
            print(responseString)
        } else {
            // Otherwise print a hex dump of the body.
            print(responseBody as NSData)
        }
```

### Compare Against a Working Client

If the HTTP response body doesn’t help, compare your request to a request issued by a working client. For example, the server might not fail if you send it the same request from:

- A web browser, like Safari

- A command-line tool, like `curl`

- An app running on a different platform

If you have a working client, it’s relatively straightforward to debug your problem:

1.  Use the same network debugging tool to record the requests made by your client and the working client. If you’re using HTTP (not HTTPS), use a low-level packet trace tool to record these requests (see Recording a Packet Trace). If you’re using HTTPS, with Transport Layer Security (TLS), you can’t see the HTTP request. In that case, if your server has a debugging mode that lets you see the plaintext request, look there. If not, a debugging HTTP proxy may let you see the request; see Debugging HTTP Proxies for more information.

2.  Compare the two requests. Focus on the most significant values first. Do the URL paths match? Do the HTTP methods match? Do the `Content-Type` headers match? What about the remaining headers? Do the request bodies match? If these all match and things still don’t work, you may need to look at more obscure values, like the HTTP transfer encoding and, if you’re using HTTPS, various TLS parameters.

3.  Address any discrepancies.

4.  Retry with your updated client.

5.  If things still fail, go back to step 1.

### Debug on the Server

If you don’t have access to a working client, or you can’t get things to work using the steps described in the previous section, your only remaining option is to debug the problem on the server. Ideally, the server has documented debugging options that offer more insight into the failure. If not, escalate the problem through the support channel associated with your server software.

## See Also

### Network Debugging

Choosing a Network Debugging Tool

Decide which tool works best for your network debugging problem.

Debugging HTTPS Problems with CFNetwork Diagnostic Logging

Use CFNetwork diagnostic logging to investigate HTTP and HTTPS problems.

Recording a Packet Trace

Learn how to record a low-level trace of network traffic.

Taking Advantage of Third-Party Network Debugging Tools

Learn about the available third-party network debugging tools.

Testing and Debugging L4S in Your App

Learn how to verify your app on an L4S-capable host and network to improve your app’s responsiveness.

