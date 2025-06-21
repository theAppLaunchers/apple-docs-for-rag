*   [PassKit (Apple Pay and Wallet)](/documentation/passkit)
*   PKPaymentAuthorizationControllerDelegate

Protocol

# PKPaymentAuthorizationControllerDelegate

Methods that let you respond to user interactions with your payment authorization controller.

iOSiPadOSMac CatalystmacOSvisionOSwatchOS

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
protocol PKPaymentAuthorizationControllerDelegate : [`NSObjectProtocol`](/documentation/ObjectiveC/NSObjectProtocol)
```
```
```
```
```
```
```
```

## [Overview](/documentation/PassKit/PKPaymentAuthorizationControllerDelegate#overview)

The [`PKPaymentAuthorizationControllerDelegate`](/documentation/passkit/pkpaymentauthorizationcontrollerdelegate) protocol is implemented by the payment authorization controller’s delegate. You implement this protocol to respond to user interaction with that controller.

In most cases, the payment authorization controller automatically waits for its delegate to finish responding to one method before it calls other delegate methods. You indicate that the delegate is finished with the current method by calling that method’s completion block. This action tells the pay authorization controller to proceed with the next step in the authorization process.

There is one exception to this step-by-step procedure: The pay authorization controller calls the [`paymentAuthorizationControllerDidFinish(_:)`](/documentation/passkit/pkpaymentauthorizationcontrollerdelegate/paymentauthorizationcontrollerdidfinish\(_:\)) method as soon as the user cancels a payment without authorizing. The controller can call this method at any time.

## [Topics](/documentation/PassKit/PKPaymentAuthorizationControllerDelegate#topics)

### [Handling user interactions](/documentation/PassKit/PKPaymentAuthorizationControllerDelegate#Handling-user-interactions)

```swift
```swift
```swift
```swift
func presentationWindow(for: PKPaymentAuthorizationController) -> UIWindow?
```
```

Returns the window in which to present a payment authorization sheet.

**Required**
```
```

### [Handling user’s payment method selection](/documentation/PassKit/PKPaymentAuthorizationControllerDelegate#Handling-users-payment-method-selection)

```swift
```swift
```swift
```swift
func paymentAuthorizationController(PKPaymentAuthorizationController, didSelectPaymentMethod: PKPaymentMethod, handler: (PKPaymentRequestPaymentMethodUpdate) -> Void)
```
```

Tells the delegate that the user changed the payment method, and asks for an updated payment request.
```
```swift
```swift
```swift
func paymentAuthorizationController(PKPaymentAuthorizationController, didSelectPaymentMethod: PKPaymentMethod, completion: ([PKPaymentSummaryItem]) -> Void)
```
```

Tells the delegate that the user changed the payment method, and asks for an updated payment request.

Deprecated
```
```

### [Handling coupons](/documentation/PassKit/PKPaymentAuthorizationControllerDelegate#Handling-coupons)

```swift
```swift
```swift
```swift
func paymentAuthorizationController(PKPaymentAuthorizationController, didChangeCouponCode: String, handler: (PKPaymentRequestCouponCodeUpdate) -> Void)
```
```

Tells the delegate that the user entered or updated a coupon code.
```
```

### [Handling shipping information](/documentation/PassKit/PKPaymentAuthorizationControllerDelegate#Handling-shipping-information)

```swift
```swift
```swift
```swift
func paymentAuthorizationController(PKPaymentAuthorizationController, didSelectShippingContact: PKContact, handler: (PKPaymentRequestShippingContactUpdate) -> Void)
```
```

Tells the delegate that the user selected a shipping address.
```
```swift
```swift
```swift
func paymentAuthorizationController(PKPaymentAuthorizationController, didSelectShippingContact: PKContact, completion: (PKPaymentAuthorizationStatus, [PKShippingMethod], [PKPaymentSummaryItem]) -> Void)
```
```

Tells the delegate that the user selected a shipping address.

Deprecated
```
```swift
```swift
```swift
func paymentAuthorizationController(PKPaymentAuthorizationController, didSelectShippingMethod: PKShippingMethod, handler: (PKPaymentRequestShippingMethodUpdate) -> Void)
```
```

Tells the delegate that the user selected a shipping method.
```
```swift
```swift
```swift
func paymentAuthorizationController(PKPaymentAuthorizationController, didSelectShippingMethod: PKShippingMethod, completion: (PKPaymentAuthorizationStatus, [PKPaymentSummaryItem]) -> Void)
```
```

Tells the delegate that the user selected a shipping method.

Deprecated
```
```

### [Handling user’s payment authorization](/documentation/PassKit/PKPaymentAuthorizationControllerDelegate#Handling-users-payment-authorization)

```swift
```swift
```swift
```swift
func paymentAuthorizationController(PKPaymentAuthorizationController, didRequestMerchantSessionUpdate: (PKPaymentRequestMerchantSessionUpdate) -> Void)
```
```

Requests an object that validates the identity of a merchant for a payment request.
```
```swift
```swift
```swift
func paymentAuthorizationControllerWillAuthorizePayment(PKPaymentAuthorizationController)
```
```

Tells the delegate that the user is authorizing the payment request.
```
```swift
```swift
```swift
func paymentAuthorizationController(PKPaymentAuthorizationController, didAuthorizePayment: PKPayment, handler: (PKPaymentAuthorizationResult) -> Void)
```
```

Tells the delegate that the user authorized the payment request, and asks for a result.
```
```swift
```swift
```swift
func paymentAuthorizationController(PKPaymentAuthorizationController, didAuthorizePayment: PKPayment, completion: (PKPaymentAuthorizationStatus) -> Void)
```
```

Tells the delegate that the user authorized the payment request, and asks for a result.

Deprecated
```
```swift
```swift
```swift
func paymentAuthorizationControllerDidFinish(PKPaymentAuthorizationController)
```
```

Tells the delegate that payment authorization has completed.

**Required**
```
```

## [Relationships](/documentation/PassKit/PKPaymentAuthorizationControllerDelegate#relationships)

### [Inherits From](/documentation/PassKit/PKPaymentAuthorizationControllerDelegate#inherits-from)

*   [`NSObjectProtocol`](/documentation/ObjectiveC/NSObjectProtocol)

## [See Also](/documentation/PassKit/PKPaymentAuthorizationControllerDelegate#see-also)

### [Handling user interactions](/documentation/PassKit/PKPaymentAuthorizationControllerDelegate#Handling-user-interactions)

```swift
```swift
```swift
```swift
var delegate: (any PKPaymentAuthorizationControllerDelegate)?
```
```

The controller’s delegate.
```
```swift
```swift
```swift
func present(completion: ((Bool) -> Void)?)
```
```

Presents the payment sheet modally over your app.
```
```swift
```swift
```swift
func dismiss(completion: (() -> Void)?)
```
```

Dismisses the payment sheet.
```
```