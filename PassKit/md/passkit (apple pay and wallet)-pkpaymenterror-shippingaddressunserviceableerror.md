

- PassKit (Apple Pay and Wallet)
- PKPaymentError
-  shippingAddressUnserviceableError 

Type Property

# shippingAddressUnserviceableError

The error code for an unserviceable shipping address.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.1+macOS 10.13+visionOS 1.0+watchOS 4.0+

``` source
static var shippingAddressUnserviceableError: PKPaymentError.Code { get }
```

## Discussion

Use this error code for a shipping address that is otherwise valid, but is unserviceable. For example, the address is in a country or region you don’t ship to, or it’s a P.O. box and you can’t deliver to P.O. boxes.

## See Also

### Identifying the error

static var billingContactInvalidError: PKPaymentError.Code

The error code to indicate an invalid billing address or billing name.

static var shippingContactInvalidError: PKPaymentError.Code

The error code to indicate an invalid shipping address, email, phone, or name.

static var couponCodeExpiredError: PKPaymentError.Code

The error code that indicates an expired coupon.

static var couponCodeInvalidError: PKPaymentError.Code

The error code that indicates an invalid coupon.

static var unknownError: PKPaymentError.Code

The error code for an unknown error.

enum Code

An error code that you provide to indicate problems with address or contact information on an Apple Pay sheet.

