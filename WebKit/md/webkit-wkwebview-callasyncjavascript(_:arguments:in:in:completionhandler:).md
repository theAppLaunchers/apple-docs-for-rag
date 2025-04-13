

- WebKit
- WKWebView
-  callAsyncJavaScript(\_:arguments:in:in:completionHandler:) 

Instance Method

# callAsyncJavaScript(\_:arguments:in:in:completionHandler:)

Executes the specified string as an asynchronous JavaScript function.

iOS 14.0+iPadOS 14.0+Mac CatalystmacOS 11.0+visionOS

``` source
@MainActor @preconcurrency
func callAsyncJavaScript(
    _ functionBody: String,
    arguments: [String : Any] = [:],
    in frame: WKFrameInfo? = nil,
    in contentWorld: WKContentWorld,
    completionHandler: (@MainActor (Result) -> Void)? = nil
)
```

## Parameters 

`functionBody`  

The JavaScript string to use as the function body. This method treats the string as an anonymous JavaScript function body and calls it with the named arguments in the `arguments` parameter.

`arguments`  

A dictionary of the arguments to pass to the function call. Each key in the dictionary corresponds to the name of an argument in the `functionBody` string, and the value of that key is the value to use during the evaluation of the code. Supported value types are NSNumber, NSString, NSDate, NSArray, NSDictionary, or NSNull. All items in an array or dictionary must also be one of the supported types.

`frame`  

The frame in which to evaluate the JavaScript code. Specify `nil` to target the main frame. If this frame is no longer valid when script evaluation begins, this method returns a WKError.Code.javaScriptInvalidFrameTarget error.

`contentWorld`  

The namespace in which to evaluate the JavaScript code. This parameter doesn’t apply to changes you make to the underlying web content, such as the document’s DOM structure. Those changes remain visible to all scripts, regardless of which content world you specify. For more information about content worlds, see WKContentWorld.

`completionHandler`  

A handler block to execute when script evaluation finishes. The method calls your block whether script evaluation completes successfully or fails. The block has no return value and takes the following parameter:

result  
The result of the script evaluation, or an error object that contains information about the problem that occurred. If your function body doesn’t return an explicit value, WebKit passes `nil` to your completion handler on success. If your function explicitly returns `null`, WebKit returns that value as an NSNull object.

## Discussion

Don’t format the string in the `functionBody` parameter as a function-like callable object, as you would in pure JavaScript. Instead, put only the body of the function in the string. For example, the following string shows a valid function body that takes `x`, `y`, and `z` arguments and returns a result.

```
return x ? y : z
```

If your JavaScript code returns an object with a callable `then` property, WebKit calls that property on the resulting object and waits for its resolution. If resolution succeeds, WebKit passes the resulting object to your completion handler. If resolution fails, WebKit returns a `WKErrorJavaScriptAsyncFunctionResultRejected` error to your completion handler. Examine the userInfo dictionary of the error object to determine the reason for the object’s rejection. If the garbage collector reclaims the object before resolution finishes, WebKit returns a `WKErrorJavaScriptAsyncFunctionResultUnreachable` error to your completion handler.

Because this method calls your JavaScript code asynchronously, you can call `await` on objects with a `then` property inside your function body. The following code example illustrates this technique.

```
var p = new Promise(function (f) {
   window.setTimeout("f(42)", 1000);
});
await p;
return p;
```

## See Also

### Executing JavaScript

func evaluateJavaScript(String, completionHandler: ((Any?, (any Error)?) -> Void)?)

Evaluates the specified JavaScript string.

func evaluateJavaScript(String, in: WKFrameInfo?, in: WKContentWorld, completionHandler: ((Result&lt;Any, any Error>) -> Void)?)

Evaluates a JavaScript string in the context of the specified frame and content world.

func evaluateJavaScript(String, in: WKFrameInfo?, contentWorld: WKContentWorld) async throws -> Any?

Evaluates a JavaScript string in the context of the specified frame and content world.

func callAsyncJavaScript(String, arguments: [String : Any], in: WKFrameInfo?, contentWorld: WKContentWorld) async throws -> Any?

Executes the specified string as an asynchronous JavaScript function.

