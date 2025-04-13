

- SwiftUI
- Transaction
-  subscript(\_:) 

Instance Subscript

# subscript(\_:)

Accesses the transaction value associated with a custom key.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+watchOS 10.0+

``` source
subscript(key: K.Type) -> K.Value where K : TransactionKey { get set }
```

## Overview

Create custom transaction values by defining a key that conforms to the TransactionKey protocol, and then using that key with the subscript operator of the Transaction structure to get and set a value for that key:

```
private struct MyTransactionKey: TransactionKey {
    static let defaultValue = false
}

extension Transaction {
    var myCustomValue: Bool {
        get { self[MyTransactionKey.self] }
        set { self[MyTransactionKey.self] = newValue }
    }
}
```

## See Also

### Getting information about a transaction

var isContinuous: Bool

A Boolean value that indicates whether the transaction originated from an action that produces a sequence of values.

var scrollTargetAnchor: UnitPoint?

The preferred alignment of the view within a scroll view’s visible region when scrolling to a view.

var tracksVelocity: Bool

Whether this transaction will track the velocity of any animatable properties that change.

