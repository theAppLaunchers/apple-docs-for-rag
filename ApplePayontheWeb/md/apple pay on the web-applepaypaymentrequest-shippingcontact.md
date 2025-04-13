

- Apple Pay on the Web
- ApplePayPaymentRequest
-  shippingContact 

Instance Property

# shippingContact

Shipping contact information for the user.

Safari Desktop 10.0+Safari Mobile 10.0+

``` source
ApplePayPaymentContact shippingContact;
```

## Discussion

If you have an up-to-date shipping address on file, you can set it here. See ApplePayPaymentContact for the fields in shippingContact.

The information you provide in shippingContact is displayed in the payment sheet as the default shipping address. The user can either keep the address you provided or select another address.

Provide your user’s shipping contact info only if you are requiring shipping contact information.

## See Also

### Providing known contact information

billingContact

Billing contact information for the user.

ApplePayPaymentContact

Contact information fields to use for billing and shipping contact information.

