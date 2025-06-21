*   [Apple Pay on the Web](/documentation/applepayontheweb)
*   ApplePayModifier

Structure

# ApplePayModifier

A dictionary that defines the Apple Pay modifiers for a payment type in the W3C Payment Request API.

Safari Desktop 10.0+Safari Mobile 10.0+

```swift
```swift
```swift
```swift
```swift
```swift
```

```
dictionary ApplePayModifier {
	ApplePayPaymentMethodType paymentMethodType;
	ApplePayLineItem total;
	sequence <ApplePayLineItem> additionalLineItems;
	sequence <ApplePayShippingMethod> additionalShippingMethods;
	sequence <ApplePayPaymentTokenContext> multiTokenContexts;
	ApplePayAutomaticReloadPaymentRequest automaticReloadPaymentRequest;
	ApplePayRecurringPaymentRequest recurringPaymentRequest;
	ApplePayDeferredPaymentRequest deferredPaymentRequest;
};
```

```
```
```
```
```
```
```

## [Mentioned in](/documentation/ApplePayontheWeb/ApplePayModifier#mentions)

[

Setting up the payment request API to accept Apple Pay](/documentation/applepayontheweb/setting-up-the-payment-request-api-to-accept-apple-pay)

[

Apple Pay on the Web Version 12 Release Notes](/documentation/applepayontheweb/apple-pay-on-the-web-version-12-release-notes)

[

Apple Pay on the Web Version 14 Release Notes](/documentation/applepayontheweb/apple-pay-on-the-web-version-14-release-notes)

## [Overview](/documentation/ApplePayontheWeb/ApplePayModifier#overview)

This dictionary contains the supported Apple Pay properties for the `PaymentDetailsModifier` `data` object in the [Payment Request API](/documentation/ApplePayontheWeb/payment-request-api). For more information about `PaymentDetailsModifier`, see the [W3C Payment Request API specification](https://www.w3.org/TR/payment-request/#paymentdetailsmodifier-dictionary).

In the Payment Request API, modifiers contain transaction details that apply only under certain conditions. For example, you can create a modifier that adds a surcharge for paying with a credit card. Each transaction contains the modifier details, but the payment sheet only displays the surcharge if the user chooses to pay with a credit card.

In Apple Pay, define display items using an [`ApplePayModifier`](/documentation/applepayontheweb/applepaymodifier) based on the user’s choice of payment method type: `"credit"`, `"debit"`, `"prepaid"`, or `"store"`. When the user selects their payment method, the transaction displays the information on the payment sheet based on the modifier corresponding to the payment method. To create a modifier that works with all payment types, don’t include the [`paymentMethodType`](/documentation/applepayontheweb/applepaymodifier/paymentmethodtype) attribute.

The following example shows a modifier that applies to the `credit` payment type that changes the total to $15, adds a $5 “Surcharge” line item, and adds a shipping method with an estimated delivery of 3 to 5 days:

```swift
```swift
```swift
```swift
```swift
```swift
let shippingStart = new Date;
```
```
shippingStart.setDate(shippingStart.getDate() + 3);
```swift
```swift
let shippingEnd = new Date;
```
```
shippingEnd.setDate(shippingEnd.getDate() + 5);
```swift
```swift
let modifiers = [
```
```
    {
        supportedMethods: "https://apple.com/apple-pay",
        data: {
            paymentMethodType: "credit",
            total: {
                label: "Total",
                amount: "15.00",
            },
            additionalLineItems: [
                {
                    label: "Surcharge",
                    amount: "5.00",
                },
            ],
            additionalShippingMethods: [
                {
                    amount: "0.00",
                    dateComponentsRange: {
                        startDateComponents: {
                            year: shippingStart.getFullYear(),
                            months: shippingStart.getMonth() + 1,
                            days: shippingStart.getDate(),
                        },
                        endDateComponents: {
                            year: shippingEnd.getFullYear(),
                            months: shippingEnd.getMonth() + 1,
                            days: shippingEnd.getDate(),
                        },
                    },
                    detail: "Tickets sent to your address",
                    identifier: "delivery",
                    label: "Delivery",
                },
            ],
        },
    },
];
```
```
```
```

Applying the modifier overwrites the total in the payment request when the modifier also includes a total.

Important

The payment sheet displays data only. You’re responsible for supplying all values, including calculating new totals that result from using a modifier.

For more information about using the Apple Pay modifier, see [Setting up the payment request API to accept Apple Pay](/documentation/ApplePayontheWeb/setting-up-the-payment-request-api-to-accept-apple-pay).

### [Providing multiple modifiers](/documentation/ApplePayontheWeb/ApplePayModifier#Providing-multiple-modifiers)

To provide an Apple Pay modifier that applies to all payment methods, include an [`ApplePayModifier`](/documentation/applepayontheweb/applepaymodifier) with no [`paymentMethodType`](/documentation/applepayontheweb/applepaymodifier/paymentmethodtype) specified. However, if this modifier appears first in an array of modifiers, the payment request always uses it, and ignores the subsequent Apple Pay modifiers.

If you provide multiple Apple Pay modifiers for the same [`paymentMethodType`](/documentation/applepayontheweb/applepaymodifier/paymentmethodtype), such as multiple modifiers for a `"credit"` payment method type, Apple Pay uses only the first [`ApplePayModifier`](/documentation/applepayontheweb/applepaymodifier) for that payment method. Apple Pay ignores the remaining modifiers with a `"credit"` payment method type.

### [Requesting optional payment types](/documentation/ApplePayontheWeb/ApplePayModifier#Requesting-optional-payment-types)

A typical payment request is for a one-time payment. To support different types of payment requests, include one of the following options in the [`ApplePayModifier`](/documentation/applepayontheweb/applepaymodifier):

*   The [`recurringPaymentRequest`](/documentation/applepayontheweb/applepaymodifier/recurringpaymentrequest) property to request a recurring payment.
    
*   The [`automaticReloadPaymentRequest`](/documentation/applepayontheweb/applepaymodifier/automaticreloadpaymentrequest) property to set up automatic reload payments.
    
*   The [`multiTokenContexts`](/documentation/applepayontheweb/applepaymodifier/multitokencontexts) property to request multiple payment tokens to support multimerchant payments.
    

Note

You can set only one of these optional payment type properties in the [`ApplePayModifier`](/documentation/applepayontheweb/applepaymodifier).

### [Requesting a recurring payment](/documentation/ApplePayontheWeb/ApplePayModifier#Requesting-a-recurring-payment)

Use the [`recurringPaymentRequest`](/documentation/applepayontheweb/applepaymodifier/recurringpaymentrequest) property to set up a recurring payment request in the [`ApplePayModifier`](/documentation/applepayontheweb/applepaymodifier). Recurring payments, such as subscriptions, can feature different payment intervals (for example, annually or monthly), and billing cycles (for example, regular or trial).

### [Requesting automatic reload payments](/documentation/ApplePayontheWeb/ApplePayModifier#Requesting-automatic-reload-payments)

Use the [`automaticReloadPaymentRequest`](/documentation/applepayontheweb/applepaymodifier/automaticreloadpaymentrequest) property to set up an automatic reload payment in the [`ApplePayModifier`](/documentation/applepayontheweb/applepaymodifier). You can set up automatic reload payments, such as store card top-ups, that feature a balance threshold and a reload amount. The card automatically reloads with the reload amount when the account drops below the balance threshold.

### [Requesting multitoken or multimerchant payments](/documentation/ApplePayontheWeb/ApplePayModifier#Requesting-multitoken-or-multimerchant-payments)

Use the [`multiTokenContexts`](/documentation/applepayontheweb/applepaymodifier/multitokencontexts) property to set up payment data for multimerchant payments in the [`ApplePayModifier`](/documentation/applepayontheweb/applepaymodifier). You can set up multitoken transactions to process and display payment requests with multiple merchants on one payment sheet, for example, a booking site where a user pays for a hotel, flight, and car rental from different merchants.

## [Topics](/documentation/ApplePayontheWeb/ApplePayModifier#topics)

### [Payment method type](/documentation/ApplePayontheWeb/ApplePayModifier#Payment-method-type)

[`paymentMethodType`](/documentation/applepayontheweb/applepaymodifier/paymentmethodtype)

The type of card the customer uses to complete the transaction.

[`ApplePayPaymentMethodType`](/documentation/applepayontheweb/applepaypaymentmethodtype)

A string that represents the type of the payment method.

### [Payment line items](/documentation/ApplePayontheWeb/ApplePayModifier#Payment-line-items)

[`total`](/documentation/applepayontheweb/applepaymodifier/total)

A line item that represents the total payment.

[`additionalLineItems`](/documentation/applepayontheweb/applepaymodifier/additionallineitems)

A set of line items that explain additional charges and discounts.

### [Shipping methods](/documentation/ApplePayontheWeb/ApplePayModifier#Shipping-methods)

[`additionalShippingMethods`](/documentation/applepayontheweb/applepaymodifier/additionalshippingmethods)

An array of shipping method dictionaries that describe the shipping methods that the payment request supports.

[`ApplePayShippingMethod`](/documentation/applepayontheweb/applepayshippingmethod)

A dictionary that describes the shipping method for delivering physical goods.

### [Updating recurring payments](/documentation/ApplePayontheWeb/ApplePayModifier#Updating-recurring-payments)

[`recurringPaymentRequest`](/documentation/applepayontheweb/applepaymodifier/recurringpaymentrequest)

A property that requests a recurring payment, typically a subscription.

[`ApplePayRecurringPaymentRequest`](/documentation/applepayontheweb/applepayrecurringpaymentrequest)

A dictionary that represents a request to set up a recurring payment, typically a subscription.

### [Updating automatic reload payments](/documentation/ApplePayontheWeb/ApplePayModifier#Updating-automatic-reload-payments)

[`automaticReloadPaymentRequest`](/documentation/applepayontheweb/applepaymodifier/automaticreloadpaymentrequest)

A property that requests an automatic reload payment, such as a store card top-up.

[`ApplePayAutomaticReloadPaymentRequest`](/documentation/applepayontheweb/applepayautomaticreloadpaymentrequest)

A dictionary that represents a request to set up an automatic reload payment, such as a store card top-up or a prepaid account.

### [Updating multitoken or multimerchant payments](/documentation/ApplePayontheWeb/ApplePayModifier#Updating-multitoken-or-multimerchant-payments)

[`multiTokenContexts`](/documentation/applepayontheweb/applepaymodifier/multitokencontexts)

An array of payment token contexts that requests multiple payment tokens to support a multimerchant payment.

[`ApplePayPaymentTokenContext`](/documentation/applepayontheweb/applepaypaymenttokencontext)

A dictionary that defines the context for a single payment token in a payment request for multimerchant payments.

### [Updating deferred payments](/documentation/ApplePayontheWeb/ApplePayModifier#Updating-deferred-payments)

[`deferredPaymentRequest`](/documentation/applepayontheweb/applepaymodifier/deferredpaymentrequest)

A property that requests a recurring payment, such as a hotel booking or a pre-order.

## [See Also](/documentation/ApplePayontheWeb/ApplePayModifier#see-also)

### [Payment request](/documentation/ApplePayontheWeb/ApplePayModifier#Payment-request)

[

Setting up the payment request API to accept Apple Pay](/documentation/applepayontheweb/setting-up-the-payment-request-api-to-accept-apple-pay)

Support payments using Apple Pay on your website.

[`ApplePayRequestBase`](/documentation/applepayontheweb/applepayrequestbase)

A dictionary that defines basic payment and contact information that the Apple Pay payment request object uses for the W3C Payment Request API.

[`ApplePayRequest`](/documentation/applepayontheweb/applepayrequest)

A dictionary that defines the Apple Pay payment request object to use for the W3C Payment Request API.

[`ApplePayPaymentCompleteDetails`](/documentation/applepayontheweb/applepaypaymentcompletedetails)