*   [Apple Pay on the Web](/documentation/applepayontheweb)
*   PaymentMethodChangeEvent

Class

# PaymentMethodChangeEvent

The Apple Pay extensions to the Payment Request payment change event.

Safari Desktop 10.0+Safari Mobile 10.0+

```swift
```swift
```swift
```swift
```swift
```swift
```

```
interface PaymentMethodChangeEvent
```

```
```
```
```
```
```
```

## [Mentioned in](/documentation/ApplePayontheWeb/PaymentMethodChangeEvent#mentions)

[

Setting up the payment request API to accept Apple Pay](/documentation/applepayontheweb/setting-up-the-payment-request-api-to-accept-apple-pay)

[

Apple Pay on the Web Version 12 Release Notes](/documentation/applepayontheweb/apple-pay-on-the-web-version-12-release-notes)

## [Overview](/documentation/ApplePayontheWeb/PaymentMethodChangeEvent#overview)

The Payment Request API sends a [`PaymentMethodChangeEvent`](/documentation/applepayontheweb/paymentmethodchangeevent) when the user updates transaction information. For more information on [`PaymentMethodChangeEvent`](/documentation/applepayontheweb/paymentmethodchangeevent), see the [W3C Payment Request API](https://www.w3.org/TR/payment-request/#paymentmethodchangeevent-interface).

### [Apple Pay Events](/documentation/ApplePayontheWeb/PaymentMethodChangeEvent#Apple-Pay-Events)

Custom Apple Pay events include information in the [`methodDetails`](/documentation/applepayontheweb/paymentmethodchangeevent/methoddetails) attribute of the change event:

[`ApplePayCouponCodeDetails`](/documentation/applepayontheweb/applepaycouponcodedetails)

A dictionary type that indicates the user updated the coupon code.

[`ApplePayPaymentMethod`](/documentation/applepayontheweb/applepaypaymentmethod)

A dictionary type that indicates that the user changed the payment method.

## [Topics](/documentation/ApplePayontheWeb/PaymentMethodChangeEvent#topics)

### [Change Information](/documentation/ApplePayontheWeb/PaymentMethodChangeEvent#Change-Information)

[`methodName`](/documentation/applepayontheweb/paymentmethodchangeevent/methodname)

The identifier for the payment method to use for the transaction.

[`methodDetails`](/documentation/applepayontheweb/paymentmethodchangeevent/methoddetails)

A dictionary that contains the details of the change.

## [See Also](/documentation/ApplePayontheWeb/PaymentMethodChangeEvent#see-also)

### [Related Documentation](/documentation/ApplePayontheWeb/PaymentMethodChangeEvent#Related-Documentation)

[`ApplePayPaymentMethod`](/documentation/applepayontheweb/applepaypaymentmethod)

A dictionary that describes an Apple Pay payment method.

### [Respond to payment request change events](/documentation/ApplePayontheWeb/PaymentMethodChangeEvent#Respond-to-payment-request-change-events)

[`ApplePayCouponCodeDetails`](/documentation/applepayontheweb/applepaycouponcodedetails)

A dictionary that contains the updated coupon code.