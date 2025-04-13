

- Swift Testing
- Expectations and confirmations
-  Testing asynchronous code 

Article

# Testing asynchronous code

Validate whether your code causes expected events to happen.

## Overview

The testing library integrates with Swift concurrency, meaning that in many situations you can test asynchronous code using standard Swift features. Mark your test function as `async` and, in the function body, `await` any asynchronous interactions:

```
@Test func priceLookupYieldsExpectedValue() async {
  let mozarellaPrice = await unitPrice(for: .mozarella)
  #expect(mozarellaPrice == 3)
}
```

In more complex situations you can use Confirmation to discover whether an expected event happens.

### Confirm that an event happens

Call confirmation(_:expectedCount:isolation:sourceLocation:_:) in your asynchronous test function to create a `Confirmation` for the expected event. In the trailing closure parameter, call the code under test. Swift Testing passes a `Confirmation` as the parameter to the closure, which you call as a function in the event handler for the code under test when the event you’re testing for occurs:

```
@Test("OrderCalculator successfully calculates subtotal for no pizzas")
func subtotalForNoPizzas() async {
  let calculator = OrderCalculator()
  await confirmation() { confirmation in
    calculator.successHandler = { _ in confirmation() }
    _ = await calculator.subtotal(for: PizzaToppings(bases: []))
  }
}
```

If you expect the event to happen more than once, set the `expectedCount` parameter to the number of expected occurrences. The test passes if the number of occurrences during the test matches the expected count, and fails otherwise.

You can also pass a range to confirmation(_:expectedCount:isolation:sourceLocation:_:) if the exact number of times the event occurs may change over time or is random:

```
@Test("Customers bought sandwiches")
func boughtSandwiches() async {
  await confirmation(expectedCount: 0 ..

In this example, there may be zero customers or up to (but not including) 1,000 customers who order sandwiches. Any range expression which includes an explicit lower bound can be used:

| Range Expression | Usage |
|----|----|
| `1...` | If an event must occur *at least* once |
| `5...` | If an event must occur *at least* five times |
| `1 ... 5` | If an event must occur at least once, but not more than five times |
| `0 ..

### Confirm that an event doesn’t happen

To validate that a particular event doesn’t occur during a test, create a `Confirmation` with an expected count of `0`:

```
@Test func orderCalculatorEncountersNoErrors() async {
  let calculator = OrderCalculator()
  await confirmation(expectedCount: 0) { confirmation in
    calculator.errorHandler = { _ in confirmation() }
    calculator.subtotal(for: PizzaToppings(bases: []))
  }
}
```

## See Also

### Confirming that asynchronous events occur

func confirmation&lt;R>(Comment?, expectedCount: Int, isolation: isolated (any Actor)?, sourceLocation: SourceLocation, (Confirmation) async throws -> sending R) async rethrows -> R

Confirm that some event occurs during the invocation of a function.

func confirmation&lt;R>(Comment?, expectedCount: some RangeExpression&lt;Int> &amp; Sendable &amp; Sequence&lt;Int>, isolation: isolated (any Actor)?, sourceLocation: SourceLocation, (Confirmation) async throws -> sending R) async rethrows -> R

Confirm that some event occurs during the invocation of a function.

struct Confirmation

A type that can be used to confirm that an event occurs zero or more times.

