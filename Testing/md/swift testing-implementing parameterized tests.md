

- Swift Testing
-  Implementing parameterized tests 

Article

# Implementing parameterized tests

Specify different input parameters to generate multiple test cases from a test function.

## Overview

Some tests need to be run over many different inputs. For instance, a test might need to validate all cases of an enumeration. The testing library lets developers specify one or more collections to iterate over during testing, with the elements of those collections being forwarded to a test function. An invocation of a test function with a particular set of argument values is called a test *case*.

By default, the test cases of a test function run in parallel with each other. For more information about test parallelization, see Running tests serially or in parallel.

### Parameterize over an array of values

It is very common to want to run a test *n* times over an array containing the values that should be tested. Consider the following test function:

```
enum Food {
  case burger, iceCream, burrito, noodleBowl, kebab
}

@Test("All foods available")
func foodsAvailable() async throws {
  for food: Food in [.burger, .iceCream, .burrito, .noodleBowl, .kebab] {
    let foodTruck = FoodTruck(selling: food)
    #expect(await foodTruck.cook(food))
  }
}
```

If this test function fails for one of the values in the array, it may be unclear which value failed. Instead, the test function can be *parameterized over* the various inputs:

```
enum Food {
  case burger, iceCream, burrito, noodleBowl, kebab
}

@Test("All foods available", arguments: [Food.burger, .iceCream, .burrito, .noodleBowl, .kebab])
func foodAvailable(_ food: Food) async throws {
  let foodTruck = FoodTruck(selling: food)
  #expect(await foodTruck.cook(food))
}
```

When passing a collection to the `@Test` attribute for parameterization, the testing library passes each element in the collection, one at a time, to the test function as its first (and only) argument. Then, if the test fails for one or more inputs, the corresponding diagnostics can clearly indicate which inputs to examine.

### Parameterize over the cases of an enumeration

The previous example includes a hard-coded list of `Food` cases to test. If `Food` is an enumeration that conforms to `CaseIterable`, you can instead write:

```
enum Food: CaseIterable {
  case burger, iceCream, burrito, noodleBowl, kebab
}

@Test("All foods available", arguments: Food.allCases)
func foodAvailable(_ food: Food) async throws {
  let foodTruck = FoodTruck(selling: food)
  #expect(await foodTruck.cook(food))
}
```

This way, if a new case is added to the `Food` enumeration, it’s automatically tested by this function.

### Parameterize over a range of integers

It is possible to parameterize a test function over a closed range of integers:

```
@Test("Can make large orders", arguments: 1 ... 100)
func makeLargeOrder(count: Int) async throws {
  let foodTruck = FoodTruck(selling: .burger)
  #expect(await foodTruck.cook(.burger, quantity: count))
}
```

Note

Very large ranges such as `0 ..Test with more than one collection

It’s possible to test more than one collection. Consider the following test function:

```
@Test("Can make large orders", arguments: Food.allCases, 1 ... 100)
func makeLargeOrder(of food: Food, count: Int) async throws {
  let foodTruck = FoodTruck(selling: food)
  #expect(await foodTruck.cook(food, quantity: count))
}
```

Elements from the first collection are passed as the first argument to the test function, elements from the second collection are passed as the second argument, and so forth.

Assuming there are five cases in the `Food` enumeration, this test function will, when run, be invoked 500 times (5 x 100) with every possible combination of food and order size. These combinations are referred to as the collections’ Cartesian product.

To avoid the combinatoric semantics shown above, use zip():

```
@Test("Can make large orders", arguments: zip(Food.allCases, 1 ... 100))
func makeLargeOrder(of food: Food, count: Int) async throws {
  let foodTruck = FoodTruck(selling: food)
  #expect(await foodTruck.cook(food, quantity: count))
}
```

The zipped sequence will be “destructured” into two arguments automatically, then passed to the test function for evaluation.

This revised test function is invoked once for each tuple in the zipped sequence, for a total of five invocations instead of 500 invocations. In other words, this test function is passed the inputs `(.burger, 1)`, `(.iceCream, 2)`, …, `(.kebab, 5)` instead of `(.burger, 1)`, `(.burger, 2)`, `(.burger, 3)`, …, `(.kebab, 99)`, `(.kebab, 100)`.

### Run selected test cases

If a parameterized test meets certain requirements, the testing library allows people to run specific test cases it contains. This can be useful when a test has many cases but only some are failing since it enables re-running and debugging the failing cases in isolation.

To support running selected test cases, it must be possible to deterministically match the test case’s arguments. When someone attempts to run selected test cases of a parameterized test function, the testing library evaluates each argument of the tests’ cases for conformance to one of several known protocols, and if all arguments of a test case conform to one of those protocols, that test case can be run selectively. The following lists the known protocols, in precedence order (highest to lowest):

1.  CustomTestArgumentEncodable

2.  `RawRepresentable`, where `RawValue` conforms to `Encodable`

3.  `Encodable`

4.  `Identifiable`, where `ID` conforms to `Encodable`

If any argument of a test case doesn’t meet one of the above requirements, then the overall test case cannot be run selectively.

## See Also

### Test parameterization

macro Test&lt;C>(String?, any TestTrait..., arguments: C)

Declare a test parameterized over a collection of values.

macro Test&lt;C1, C2>(String?, any TestTrait..., arguments: C1, C2)

Declare a test parameterized over two collections of values.

macro Test&lt;C1, C2>(String?, any TestTrait..., arguments: Zip2Sequence&lt;C1, C2>)

Declare a test parameterized over two zipped collections of values.

protocol CustomTestArgumentEncodable

A protocol for customizing how arguments passed to parameterized tests are encoded, which is used to match against when running specific arguments.

struct Case

A single test case from a parameterized Test.

