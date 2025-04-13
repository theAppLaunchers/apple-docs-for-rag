

- ProximityReader
- PaymentCardReaderSession
-  cancelRead() 

Instance Method

# cancelRead()

Dismiss the sheet that prompts someone to present their card for reading.

iOS 15.4+iPadOS 15.4+Mac Catalyst 17.0+

``` source
func cancelRead() async throws -> Bool
```

## Discussion

You can cancel a read operation before the device detects the card and starts reading it, but not after. Once the device begins reading the card, you cannot dismiss the sheet.

The reader supports only one read operation at a time. This method affects only the currently active read operation.

