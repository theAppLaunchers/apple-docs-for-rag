

- XCTest
- XCTNSPredicateExpectation
-  handler 

Instance Property

# handler

An optional handler that performs custom evaluation when `predicate` evaluates as `true`.

``` source
var handler: XCTNSPredicateExpectation.Handler? { get set }
```

## Discussion

If a handler isn’t provided, the first successful evaluation of the predicate fulfills the expectation. If you provide a handler, the handler can override this default behavior to tailor the conditions that fulfill the expectation.

## See Also

### Handling Predicate Resolution

typealias Handler

A handler XCTest calls when evaluating the predicate returns `true`.

