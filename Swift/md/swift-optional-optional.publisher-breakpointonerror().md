

- Swift
- Optional
- Optional.Publisher
-  breakpointOnError() 

Instance Method

# breakpointOnError()

Raises a debugger signal upon receiving a failure.

SwiftCombineiOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
func breakpointOnError() -> Publishers.Breakpoint
```

## Return Value

A publisher that raises a debugger signal upon receiving a failure.

## Discussion

When the upstream publisher fails with an error, this publisher raises the `SIGTRAP` signal, which stops the process in the debugger. Otherwise, this publisher passes through values and completions as-is.

In this example a `PassthroughSubject` publishes strings, but its downstream tryMap(_:) operator throws an error. This sends the error downstream as a `Subscribers/Completion/failure(_:)`. The breakpointOnError() operator receives this completion and stops the app in the debugger.

```
 struct CustomError : Error {}
 let publisher = PassthroughSubject()
 cancellable = publisher
     .tryMap { stringValue in
         throw CustomError()
     }
     .breakpointOnError()
     .sink(
         receiveCompletion: { completion in print("Completion: \(String(describing: completion))") },
         receiveValue: { aValue in print("Result: \(String(describing: aValue))") }
     )

 publisher.send("TEST DATA")

 // Prints: "error: Execution was interrupted, reason: signal SIGTRAP."
 // Depending on your specific environment, the console messages may
 // also include stack trace information, which is not shown here.
```

