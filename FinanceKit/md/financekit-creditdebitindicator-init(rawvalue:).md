

- FinanceKit
- CreditDebitIndicator
-  init(rawValue:) 

Initializer

# init(rawValue:)

Creates a new instance with the specified raw value.

iOS 17.4+iPadOS 17.4+

``` source
init?(rawValue: Int16)
```

## Parameters 

`rawValue`  

The raw value to use for the new instance.

## Discussion

If there is no value of the type that corresponds with the specified raw value, this initializer returns `nil`. For example:

```
enum PaperSize: String {
    case A4, A5, Letter, Legal
}

print(PaperSize(rawValue: "Legal"))
// Prints "Optional(PaperSize.Legal)"

print(PaperSize(rawValue: "Tabloid"))
// Prints "nil"
```

