

- Swift
- Swift Standard Library
- Numbers and Basic Values
- Result
-  Preserving the Results of a Throwing Expression 

Article

# Preserving the Results of a Throwing Expression

Call the initializer that wraps a throwing expression when you need to serialize or memoize the result.

## Overview

Sometimes you need to preserve the entire result of a function call or other expression that can either throw or return a value. For example, you may need to serialize the result or pass it as a value to another part of your app that handles the result data. Use the Result type in these scenarios to capture the result of a potentially failing operation.

### Identify a Throwing Expression to Preserve

Typically, you use `do-catch` statements to handle throwing expressions immediately, but sometimes you need to store the whole result of the operation for later processing during tasks like analyzing a batch of calls. The following example introduces an API that generates random numbers, but that fails approximately half of the time.

```
enum EntropyError: Error {
    case entropyDepleted
}

struct UnreliableRandomGenerator {
    func random() throws -> Int {
        if Bool.random() {
            return Int.random(in: 1...100)
        } else {
            throw EntropyError.entropyDepleted
        }
    }
}
```

### Convert the Throwing Expression to a Result

You preserve the return value or thrown error from a throwing expression using the Result enumeration’s init(catching:) initializer. Invoke the throwing expression inside the closure you pass to the initializer:

```
let singleSample = Result { try UnreliableRandomGenerator().random() }
```

In most scenarios, you use the preserved result as part of broader functionality in your code. For example, you may run a series of randomness tests and compute the statistical average of both a range of numbers returned from a random number generator, as well as the failure rate of calling the API. In these cases, you need to store the whole result rather than just the success value or that the API call failed.

The following example uses the init(catching:) initializer in the broader context of saving a series of calls for later statistical analysis:

```
struct RandomnessMonitor {
    let randomnessSource: UnreliableRandomGenerator
    var results: [Result] = []

    init(generator: UnreliableRandomGenerator) {
        randomnessSource = generator
    }

    mutating func sample() {
        let sample = Result { try randomnessSource.random() }
        results.append(sample)
    }

    func summary() -> (Double, Double) {
        let totals = results.reduce((sum: 0, count: 0)) { total, sample in
            switch sample {
            case .success(let number):
                return (total.sum + number, total.count)
            case .failure:
                return (total.sum, total.count + 1)
            }
        }

        return (
            average: Double(totals.sum) / Double(results.count - totals.count),
            failureRate: Double(totals.count) / Double(results.count)
        )
    }
}
```

Running the analysis on a sufficiently large sample generates an average number near 50 and a failure rate near 50%:

```
var monitor = RandomnessMonitor(generator: UnreliableRandomGenerator())
(0..

## See Also

### Converting a Throwing Expression to a Result

init(catching: () throws(Failure) -> Success)

Creates a new result by evaluating a throwing closure, capturing the returned value as a success, or any thrown error as a failure.

