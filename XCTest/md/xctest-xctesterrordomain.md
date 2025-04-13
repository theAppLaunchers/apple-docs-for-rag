

- XCTest
-  XCTestErrorDomain 

Global Variable

# XCTestErrorDomain

The error domain for errors that can occur while the test is waiting to fulfill expectations.

``` source
let XCTestErrorDomain: String
```

## See Also

### Waiting for Expectations

func fulfillment(of: [XCTestExpectation], timeout: TimeInterval, enforceOrder: Bool) async

Waits on a group of expectations for up to the specified timeout, optionally enforcing their order of fulfillment.

func wait(for: [XCTestExpectation])

Waits on a group of expectations.

func wait(for: [XCTestExpectation], enforceOrder: Bool)

Waits on a group of expectations optionally enforcing their order of fulfillment.

func wait(for: [XCTestExpectation], timeout: TimeInterval)

Waits for the test to fulfill a set of expectations within a specified time.

func wait(for: [XCTestExpectation], timeout: TimeInterval, enforceOrder: Bool)

Waits for the test to satisfy an array of expectations and specifies whether they must occur in the array’s order.

func waitForExpectations(timeout: TimeInterval, handler: (((any Error)?) -> Void)?)

Waits until the test fulfills all expectations or until it times out.

typealias XCWaitCompletionHandler

A block the test runner calls when the test fulfills a waiter’s expectations, or when it times out.

struct XCTestError

A type of error that can occur while the test waits to fulfill expectations.

enum Code

Error codes for errors that can occur while the test is waiting to fulfill expectations.

