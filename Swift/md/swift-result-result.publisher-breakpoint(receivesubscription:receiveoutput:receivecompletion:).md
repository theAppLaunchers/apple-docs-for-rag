

- Swift
- Result
- Result.Publisher
-  breakpoint(receiveSubscription:receiveOutput:receiveCompletion:) 

Instance Method

# breakpoint(receiveSubscription:receiveOutput:receiveCompletion:)

Raises a debugger signal when a provided closure needs to stop the process in the debugger.

SwiftCombineiOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
func breakpoint(
    receiveSubscription: ((any Subscription) -> Bool)? = nil,
    receiveOutput: ((Self.Output) -> Bool)? = nil,
    receiveCompletion: ((Subscribers.Completion) -> Bool)? = nil
) -> Publishers.Breakpoint
```

## Parameters 

`receiveSubscription`  

A closure that executes when the publisher receives a subscription. Return `true` from this closure to raise `SIGTRAP`, or false to continue.

`receiveOutput`  

A closure that executes when the publisher receives a value. Return `true` from this closure to raise `SIGTRAP`, or false to continue.

`receiveCompletion`  

A closure that executes when the publisher receives a completion. Return `true` from this closure to raise `SIGTRAP`, or false to continue.

## Return Value

A publisher that raises a debugger signal when one of the provided closures returns `true`.

## Discussion

Use breakpoint(receiveSubscription:receiveOutput:receiveCompletion:) to examine one or more stages of the subscribe/publish/completion process and stop in the debugger, based on conditions you specify. When any of the provided closures returns `true`, this operator raises the `SIGTRAP` signal to stop the process in the debugger. Otherwise, this publisher passes through values and completions as-is.

In the example below, a `PassthroughSubject` publishes strings to a breakpoint republisher. When the breakpoint receives the string “`DEBUGGER`”, it returns `true`, which stops the app in the debugger.

```
let publisher = PassthroughSubject()
cancellable = publisher
    .breakpoint(
        receiveOutput: { value in return value == "DEBUGGER" }
    )
    .sink { print("\(String(describing: $0))" , terminator: " ") }

publisher.send("DEBUGGER")

// Prints: "error: Execution was interrupted, reason: signal SIGTRAP."
// Depending on your specific environment, the console messages may
// also include stack trace information, which is not shown here.
```

