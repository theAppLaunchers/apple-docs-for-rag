

- XCTest
- XCTestCase
-  waitForExpectations(timeout:handler:) 

Instance Method

# waitForExpectations(timeout:handler:)

Waits until the test fulfills all expectations or until it times out.

``` source
@MainActor
func waitForExpectations(
    timeout: TimeInterval,
    handler: (((any Error)?) -> Void)? = nil
)
```

## Parameters 

`timeout`  

The time, in seconds, the test allows for the fulfillment of the expectations. The default timeout allows the test to run until it reaches its execution time allowance.

`handler`  

An optional XCWaitCompletionHandler block to invoke after a test fulfills all expectations or the wait time elapses. A test treats a timeout as a failure.

## Discussion

This method creates a point of synchronization in the flow of a test. Only one waitForExpectations(timeout:handler:) can be active at any given time, but you can chain together multiple discrete sequences of “create expectations and wait for them to be fulfilled”.

Important

This method waits on expectations created with XCTestCase‘s convenience methods only. This method *doesn’t* wait on expectations created manually through initializers on XCTestExpectation or its subclasses.

To wait for manually created expectations, use the wait(for:timeout:) or wait(for:timeout:enforceOrder:) methods, or the corresponding methods on XCTWaiter, passing an explicit list of expectations.

Note

Clients shouldn’t manipulate the run loop while using this API.

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

typealias XCWaitCompletionHandler

A block the test runner calls when the test fulfills a waiter’s expectations, or when it times out.

struct XCTestError

A type of error that can occur while the test waits to fulfill expectations.

enum Code

Error codes for errors that can occur while the test is waiting to fulfill expectations.

let XCTestErrorDomain: String

The error domain for errors that can occur while the test is waiting to fulfill expectations.

