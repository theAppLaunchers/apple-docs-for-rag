

- ProximityReader
- PaymentCardReaderSession
-  readPaymentCard(\_:) 

Instance Method

# readPaymentCard(\_:)

Presents a sheet to read a contactless payment card for a purchase or a refund, and returns the encrypted card data.

iOS 16.0+iPadOS 16.0+Mac Catalyst 17.0+

``` source
func readPaymentCard(_ request: PaymentCardTransactionRequest) async throws -> PaymentCardReadResult
```

## Parameters 

`request`  

The transaction object you provide with the payment amount and currency details.

## Return Value

A PaymentCardReadResult if the read operation was successful.

## Discussion

Call this method as the first step in a financial transaction involving Tap to Pay with iPhone. This method displays a system-provided sheet with instructions on what the person needs to do. This UI remains onscreen until the system reads the person’s card, you cancel the operation, or an error occurs. After the read operation concludes successfully, deliver the returned card information to your payment service provider.

Throws

This method throws a PaymentCardReaderSession.ReadError if a person dismisses the sheet or the sheet fails to appear.

## See Also

### Reading a payment card

func readPaymentCard(PaymentCardVerificationRequest) async throws -> PaymentCardReadResult

Presents a sheet to verify a contactless payment card, and returns the card data.

