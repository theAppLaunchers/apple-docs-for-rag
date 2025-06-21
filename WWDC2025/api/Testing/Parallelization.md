*   [Swift Testing](/documentation/testing)
*   [Traits](/documentation/testing/traits)
*   Running tests serially or in parallel

Article

# Running tests serially or in parallel

Control whether tests run serially or in parallel.

## [Overview](/documentation/Testing/Parallelization#Overview)

By default, tests run in parallel with respect to each other. Parallelization is accomplished by the testing library using task groups, and tests generally all run in the same process. The number of tests that run concurrently is controlled by the Swift runtime.

## [Disabling parallelization](/documentation/Testing/Parallelization#Disabling-parallelization)

Parallelization can be disabled on a per-function or per-suite basis using the [`serialized`](/documentation/testing/trait/serialized) trait:

```swift

```swift
@Test(.serialized, arguments: Food.allCases) func prepare(food: Food) {
  // This function will be invoked serially, once per food, because it has the
  // .serialized trait.
}
@Suite(.serialized) struct FoodTruckTests {
  @Test(arguments: Condiment.allCases) func refill(condiment: Condiment) {
    // This function will be invoked serially, once per condiment, because the
    // containing suite has the .serialized trait.
  }
  @Test func startEngine() async throws {
    // This function will not run while refill(condiment:) is running. One test
    // must end before the other will start.
  }
}
```

```

When added to a parameterized test function, this trait causes that test to run its cases serially instead of in parallel. When applied to a non-parameterized test function, this trait has no effect. When applied to a test suite, this trait causes that suite to run its contained test functions and sub-suites serially instead of in parallel.

This trait is recursively applied: if it is applied to a suite, any parameterized tests or test suites contained in that suite are also serialized (as are any tests contained in those suites, and so on.)

This trait doesn’t affect the execution of a test relative to its peers or to unrelated tests. This trait has no effect if test parallelization is globally disabled (by, for example, passing `--no-parallel` to the `swift test` command.)

## [See Also](/documentation/Testing/Parallelization#see-also)

### [Running tests serially or in parallel](/documentation/Testing/Parallelization#Running-tests-serially-or-in-parallel)

[`static var serialized: ParallelizationTrait`](/documentation/testing/trait/serialized)

A trait that serializes the test to which it is applied.