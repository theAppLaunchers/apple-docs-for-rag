

- Swift
- Result
- Result.Publisher
-  map(\_:\_:\_:) 

Instance Method

# map(\_:\_:\_:)

Publishes the values of three key paths as a tuple.

SwiftCombineiOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
func map(
    _ keyPath0: KeyPath,
    _ keyPath1: KeyPath,
    _ keyPath2: KeyPath
) -> Publishers.MapKeyPath3
```

## Parameters 

`keyPath0`  

The key path of a property on `Output`.

`keyPath1`  

The key path of a second property on `Output`.

`keyPath2`  

The key path of a third property on `Output`.

## Return Value

A publisher that publishes the values of three key paths as a tuple.

## Discussion

In the following example, the map(_:_:_:) operator uses the Swift key path syntax to access the `die1`, `die2`, and `die3` members of the `DiceRoll` structure published by the `Just` publisher.

The downstream sink subscriber receives only these three values (as an `(Int, Int, Int)` tuple), not the entire `DiceRoll`.

```
struct DiceRoll {
    let die1: Int
    let die2: Int
    let die3: Int
}

cancellable = Just(DiceRoll(die1:Int.random(in:1...6),
                            die2: Int.random(in:1...6),
                            die3: Int.random(in:1...6)))
    .map(\.die1, \.die2, \.die3)
    .sink { values in
        print ("Rolled: \(values.0), \(values.1), \(values.2) (total \(values.0 + values.1 + values.2))")
    }
// Prints "Rolled: 5, 4, 2 (total 11)" (or other random values).
```

