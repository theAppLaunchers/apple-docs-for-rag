Collection

*   [Swift Testing](/documentation/testing)
*   Traits

API Collection

# Traits

Annotate test functions and suites, and customize their behavior.

## [Overview](/documentation/Testing/Traits#Overview)

Pass built-in traits to test functions or suite types to comment, categorize, classify, and modify the runtime behavior of test suites and test functions. Implement the [`TestTrait`](/documentation/testing/testtrait), and [`SuiteTrait`](/documentation/testing/suitetrait) protocols to create your own types that customize the behavior of your tests.

## [Topics](/documentation/Testing/Traits#topics)

### [Customizing runtime behaviors](/documentation/Testing/Traits#Customizing-runtime-behaviors)

[

Enabling and disabling tests](/documentation/testing/enablinganddisabling)

Conditionally enable or disable individual tests before they run.

[

Limiting the running time of tests](/documentation/testing/limitingexecutiontime)

Set limits on how long a test can run for until it fails.

[`static func enabled(if: @autoclosure () throws -> Bool, Comment?, sourceLocation: SourceLocation) -> Self`](/documentation/testing/trait/enabled\(if:_:sourcelocation:\))

Constructs a condition trait that disables a test if it returns `false`.

[`static func enabled(Comment?, sourceLocation: SourceLocation, () async throws -> Bool) -> Self`](/documentation/testing/trait/enabled\(_:sourcelocation:_:\))

Constructs a condition trait that disables a test if it returns `false`.

[`static func disabled(Comment?, sourceLocation: SourceLocation) -> Self`](/documentation/testing/trait/disabled\(_:sourcelocation:\))

Constructs a condition trait that disables a test unconditionally.

[`static func disabled(if: @autoclosure () throws -> Bool, Comment?, sourceLocation: SourceLocation) -> Self`](/documentation/testing/trait/disabled\(if:_:sourcelocation:\))

Constructs a condition trait that disables a test if its value is true.

[`static func disabled(Comment?, sourceLocation: SourceLocation, () async throws -> Bool) -> Self`](/documentation/testing/trait/disabled\(_:sourcelocation:_:\))

Constructs a condition trait that disables a test if its value is true.

[`static func timeLimit(TimeLimitTrait.Duration) -> Self`](/documentation/testing/trait/timelimit\(_:\))

Construct a time limit trait that causes a test to time out if it runs for too long.

### [Running tests serially or in parallel](/documentation/Testing/Traits#Running-tests-serially-or-in-parallel)

[

Running tests serially or in parallel](/documentation/testing/parallelization)

Control whether tests run serially or in parallel.

[`static var serialized: ParallelizationTrait`](/documentation/testing/trait/serialized)

A trait that serializes the test to which it is applied.

### [Annotating tests](/documentation/Testing/Traits#Annotating-tests)

[

Adding tags to tests](/documentation/testing/addingtags)

Use tags to provide semantic information for organization, filtering, and customizing appearances.

[

Adding comments to tests](/documentation/testing/addingcomments)

Add comments to provide useful information about tests.

[

Associating bugs with tests](/documentation/testing/associatingbugs)

Associate bugs uncovered or verified by tests.

[

Interpreting bug identifiers](/documentation/testing/bugidentifiers)

Examine how the testing library interprets bug identifiers provided by developers.

[`macro Tag()`](/documentation/testing/tag\(\))

Declare a tag that can be applied to a test function or test suite.

[`static func bug(String, Comment?) -> Self`](/documentation/testing/trait/bug\(_:_:\))

Constructs a bug to track with a test.

[`static func bug(String?, id: String, Comment?) -> Self`](/documentation/testing/trait/bug\(_:id:_:\)-10yf5)

Constructs a bug to track with a test.

[`static func bug(String?, id: some Numeric, Comment?) -> Self`](/documentation/testing/trait/bug\(_:id:_:\)-3vtpl)

Constructs a bug to track with a test.

### [Creating custom traits](/documentation/Testing/Traits#Creating-custom-traits)

```swift
```swift
```swift
```swift
protocol Trait
```
```

A protocol describing traits that can be added to a test function or to a test suite.
```
```swift
```swift
```swift
protocol TestTrait
```
```

A protocol describing a trait that you can add to a test function.
```
```swift
```swift
```swift
protocol SuiteTrait
```
```

A protocol describing a trait that you can add to a test suite.
```
```swift
```swift
```swift
protocol TestScoping
```
```

A protocol that tells the test runner to run custom code before or after it runs a test suite or test function.
```
```

### [Supporting types](/documentation/Testing/Traits#Supporting-types)

```swift
```swift
```swift
```swift
struct Bug
```
```

A type that represents a bug report tracked by a test.
```
```swift
```swift
```swift
struct Comment
```
```

A type that represents a comment related to a test.
```
```swift
```swift
```swift
struct ConditionTrait
```
```

A type that defines a condition which must be satisfied for the testing library to enable a test.
```
```swift
```swift
```swift
struct ParallelizationTrait
```
```

A type that defines whether the testing library runs this test serially or in parallel.
```
```swift
```swift
```swift
struct Tag
```
```

A type representing a tag that can be applied to a test.
```
```swift
```swift
```swift
struct List
```
```

A type representing one or more tags applied to a test.
```
```swift
```swift
```swift
struct TimeLimitTrait
```
```

A type that defines a time limit to apply to a test.
```
```