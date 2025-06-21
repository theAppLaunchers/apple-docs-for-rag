*   [PassKit (Apple Pay and Wallet)](/documentation/passkit)
*   [PKPaymentRequest](/documentation/passkit/pkpaymentrequest)
*   couponCode

Instance Property

# couponCode

The initial coupon code for the payment request.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+visionOS 1.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
var couponCode: [`String`](/documentation/Swift/String)? { get set }
```
```
```
```
```
```
```
```

## [Discussion](/documentation/PassKit/PKPaymentRequest/couponCode#Discussion)

Set the value to `nil` or the empty string to indicate that there’s no initial coupon.

Important

The system doesn’t send a change event for an initial coupon code. You must apply the code to the initial payment summary items.

## [See Also](/documentation/PassKit/PKPaymentRequest/couponCode#see-also)

### [Working with coupon codes](/documentation/PassKit/PKPaymentRequest/couponCode#Working-with-coupon-codes)

```swift
```swift
```swift
```swift
var supportsCouponCode: Bool
```
```

A Boolean value that determines whether the payment sheet displays the coupon code field.
```
```