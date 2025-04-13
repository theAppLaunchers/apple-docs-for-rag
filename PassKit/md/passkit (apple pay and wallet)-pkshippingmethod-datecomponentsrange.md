

- PassKit (Apple Pay and Wallet)
- PKShippingMethod
-  dateComponentsRange 

Instance Property

# dateComponentsRange

An expected range of delivery or shipping dates for a package, or the time range when an item is available for pickup.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+visionOS 1.0+watchOS 8.0+

``` source
@NSCopying
var dateComponentsRange: PKDateComponentsRange? { get set }
```

## Discussion

Use this object to set the expected date range for shipping a package, or the time an item is available for pickup. The payment sheet displays the range as part of the shipping method on the main sheet.

The example below shows setting a two-day time range for shipping a package that starts three days from today:

```
let shippingMethod = PKShippingMethod(label: "Delivery", amount: NSDecimalNumber(string: "10.00"))

let today = Date()
let calendar = Calendar.current

let shippingStart = calendar.date(byAdding: .day, value: 3, to: today)!
let shippingEnd = calendar.date(byAdding: .day, value: 5, to: today)!

let startComponents = calendar.dateComponents([.calendar, .year, .month, .day], from: shippingStart)
let endComponents = calendar.dateComponents([.calendar, .year, .month, .day], from: shippingEnd)

shippingMethod.dateComponentsRange = PKDateComponentsRange(start: startComponents, end: endComponents)
```

## See Also

### Working with shipping methods

var detail: String?

A user-readable description of the shipping method.

var identifier: String?

A unique identifier for the shipping method, used by the app.

class PKDateComponentsRange

An object that specifies the start and end dates for a range of time.

