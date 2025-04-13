

- XCTest
-  Expected Failures 

API Collection

# Expected Failures

Anticipate known test failures to prevent failing tests from affecting your workflows.

## Overview

When you have a workflow that requires all of your tests to pass before continuing, issues that you can’t fix quickly, and cause your tests to fail, create a difficult situation: either you stop using your workflow, or you disable the failing tests to allow your workflow to continue.

Configure your test to handle an expected assertion failure by calling `XCTExpectFailure` with a reason for the expected failure before the assertion you expect to fail.

```
func testExpectedFailure() throws {
    let thingThatFails: Bool = false
    XCTExpectFailure("Working on a fix for this problem.")
    XCTAssertTrue(thingThatFails, "This is not working right now.")
}
```

If any assertions fail in a test after you call `XCTExpectFailure`, Xcode marks the test as an expected failure instead of a test failure.

If no assertion failures occur, Xcode marks the test as failing because the expected failure doesn’t occur. Remove the expected failure to have Xcode mark the test as passing in future tests, or use the expected failure options below to refine your expected failure.

To specify which assertion you expect to fail, call `XCTExpectFailure` with a block that contains the assertion.

```
func testExpectedFailureInBlock() throws {
    let thingThatFails: Bool = false
    XCTExpectFailure("Working on a fix for this problem.") {
        XCTAssertTrue(thingThatFails, "This is not working right now.")
    }
}
```

Alternatively, provide options when calling `XCTExpectFailure` to disable the expectation in circumstances you specify, such as when a test only passes in a target environment for Mac Catalyst.

```
func testExpectedFailureDisabledWithOptions() throws {
    var thingThatFails: Bool = true
    let options = XCTExpectedFailure.Options()

    #if !targetEnvironment(macCatalyst)
    thingThatFails = false
    options.isEnabled = false
    #endif

    XCTExpectFailure("Working on a fix for this problem.", options: options) {
        XCTAssertTrue(thingThatFails, "Thing that fails failed.")
    }
}
```

Specify an `issueMatcher` closure to match an assertion. Add code in the closure to examine the issue provided by the assertion failure:

- If the issue matches what you expect, return `true` from the closure.

- Otherwise, return `false,` then the test system records a test failure for your unmatched expected failure.

```
func testExpectedFailureWithOptions() throws {    let thingThatFails: Bool = false
    let options = XCTExpectedFailure.Options()
    options.issueMatcher = { issue in
        issue.type == .assertionFailure && issue.compactDescription.contains("SPECIFIC BROKEN THING")
    }

    XCTExpectFailure("Working on a fix for this problem.", options: options)

    XCTAssertTrue(true, "This always works.")
    XCTAssertTrue(thingThatFails, "SPECIFIC BROKEN THING failed.")
}
```

If you set an expected failure for a test that fails occasionally and unpredictably, set `isStrict` to `false` to prevent an unmatched expectation from causing a test failure.

```
func testExpectedIntermittentFailure() throws {
    let testResultOfSomeActivity = performSomeActivity()

    let options = XCTExpectedFailure.Options()
    options.isStrict = false
    XCTExpectFailure("Working on a fix for this intermittent problem.", options: options)

    XCTAssertTrue(true, "This always works.")
    XCTAssertTrue(testResultOfSomeActivity, "This only seems to work half the time.")
}
```

When you call `XCTExpectFailure` multiple times in the same test, the following rules apply:

- If you call `XCTExpectFailure` with a closure, the test system restricts the scope for matching failures to the code in the closure.

- If you call `XCTExpectFailure` without a closure, the test system compares a test failure to the matcher for each `XCTExpectFailure` call in the test, from the most recent call to oldest. If the test finds a match, it associates the test failure with the matching `XCTExpectFailure` call.

The test system records a test failure for each `XCTExpectFailure` call that did not match a test failure. To avoid this, remove the unmatched `XCTExpectFailure` calls from your tests. If your test fails intermittently and you don’t want the test system to record an unmatched `XCTExpectFailure` call as a test failure, set `isStrict` to false in options you provide to your `XCTExpectFailure` call.

Note

Code coverage metrics include tests with expected failures. Consider this when evaluating code coverage and attempt to resolve issues as soon as possible.

## Topics

### Expected Failures

class XCTExpectedFailure

An object that represents an expected test failure.

class Options

Options that determine how the test matches the expected failure to an actual test failure, and whether an unfulfilled expected failure results in a test failure.

func XCTExpectFailure(String?, options: XCTExpectedFailure.Options)

Instructs the test to expect a failure in an upcoming assertion, with options to customize expected failure checking and handling.

func XCTExpectFailure(String?, enabled: Bool?, strict: Bool?, issueMatcher: ((XCTIssue) -> Bool)?)

Instructs the test to expect a failure in an upcoming assertion, with parameters to customize expected failure checking and handling.

func XCTExpectFailure&lt;R>(String?, options: XCTExpectedFailure.Options, failingBlock: () throws -> R) rethrows -> R

Instructs the test to expect a failure in an assertion in the provided block of code, with options to customize expected failure checking and handling.

func XCTExpectFailure&lt;R>(String?, enabled: Bool?, strict: Bool?, failingBlock: () throws -> R, issueMatcher: ((XCTIssue) -> Bool)?) rethrows -> R

Instructs the test to expect a failure in an assertion in the provided block of code, with parameters to customize expected failure checking and handling.

## See Also

### Test assertions

Boolean Assertions

Test a condition that generates a true or false result.

Nil and Non-Nil Assertions

Check whether a test condition has, or doesn’t have, a value.

Equality and Inequality Assertions

Check whether two values are equal or unequal.

Comparable Value Assertions

Compare two values to determine whether one is larger or smaller than the other.

Error Assertions

Check whether a function call throws, or doesn’t throw, an error.

NSException Assertions

Check whether a function call throws, or doesn’t throw, an exception.

Unconditional Test Failures

Generate a failure immediately and unconditionally.

Methods for Skipping Tests

Skip tests when meeting specified conditions.

