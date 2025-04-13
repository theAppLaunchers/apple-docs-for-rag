

- ProximityReader
- PaymentCardReaderSession
-  readVAS(\_:) 

Instance Method

# readVAS(\_:)

Presents a sheet to read a loyalty card for Value Added Services (VAS), and returns the loyalty card data.

iOS 16.0+iPadOS 16.0+Mac Catalyst 17.0+

``` source
func readVAS(_ request: VASRequest) async throws -> VASReadResult
```

## Parameters 

`request`  

The object that you use to specify the request details, such as the list of supported merchants.

## Return Value

A VASReadResult if the read operation was successful.

## Mentioned in 

Accepting loyalty passes from Wallet

## Discussion

Call this method to read the data from a loyalty card. When you call this method, the system displays UI with instructions on what the person needs to do. This UI remains onscreen until the system reads the person’s card, you cancel the operation, or an error occurs.

Throws

This method throws a PaymentCardReaderSession.ReadError if a person dismisses the sheet or the sheet fails to appear.

## See Also

### Reading a loyalty card

func readPaymentCard(PaymentCardTransactionRequest, vasRequest: VASRequest, stopOnVASResult: Bool) async throws -> (PaymentCardReadResult?, VASReadResult?)

Presents a sheet to read both contactless payments and loyalty cards for a purchase or refund, and returns the relevant card data.

