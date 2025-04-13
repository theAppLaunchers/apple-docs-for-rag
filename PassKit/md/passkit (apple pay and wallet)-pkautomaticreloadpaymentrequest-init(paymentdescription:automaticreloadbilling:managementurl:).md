

- PassKit (Apple Pay and Wallet)
- PKAutomaticReloadPaymentRequest
-  init(paymentDescription:automaticReloadBilling:managementURL:) 

Initializer

# init(paymentDescription:automaticReloadBilling:managementURL:)

Create an automatic reload payment object with a description, automatic billing information, and a management URL.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+visionOS 1.0+

``` source
init(
    paymentDescription: String,
    automaticReloadBilling: PKAutomaticReloadPaymentSummaryItem,
    managementURL: URL
)
```

## Parameters 

`paymentDescription`  

The description you provide of the automatic reload payment and that Apple Pay displays to the user in the payment sheet.

`automaticReloadBilling`  

The summary item for the automatic reload payment that includes the threshold amount and reload amount.

`managementURL`  

The URL to a web page where the user can update or delete the payment method for the recurring payment.

## Discussion

Important

You must set the automaticReloadPaymentRequest property on a PKPaymentRequest object to set up an automatic reload payment.

