

- Apple Pay on the Web
- ApplePayRequest
-  shippingContact 

Instance Property

# shippingContact

The customer’s shipping contact information.

Safari Desktop 10.0+Safari Mobile 10.0+

``` source
ApplePayPaymentContact shippingContact;
```

## Discussion

If you have an up-to-date shipping address on file for the customer, you can set it here. See ApplePayPaymentContact for the fields in shippingContact.

The payment sheet displays the information you provide in shippingContact as the default shipping address. The user can either keep the address you provide or select another address.

Provide your user’s shipping contact info only if you request shipping information by setting `requestShipping` to `true` in your PaymentOptions dictionary.

## See Also

### Known contact information

billingContact

The customer’s billing contact information.

shippingContactEditingMode

A value that indicates if the shipping mode prevents the user editing the shipping address.

ApplePayPaymentContact

Contact information fields to use for billing and shipping contact information.

ApplePayShippingContactEditingMode

Values that indicate whether the shipping mode prevents the user from editing fields of the shipping address.

