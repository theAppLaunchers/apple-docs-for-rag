

- Apple Pay on the Web
- ApplePayRequest
-  billingContact 

Instance Property

# billingContact

The customer’s billing contact information.

Safari Desktop 10.0+Safari Mobile 10.0+

``` source
ApplePayPaymentContact billingContact;
```

## Discussion

If you have an up-to-date billing address for the customer on file, you can set it here. This billing address appears in the payment sheet. The user can either use the address you specify or select a different address.

Note

If you supply a billing address, you must also request `“postalAddress”` in requiredBillingContactFields.

## See Also

### Known contact information

shippingContact

The customer’s shipping contact information.

shippingContactEditingMode

A value that indicates if the shipping mode prevents the user editing the shipping address.

ApplePayPaymentContact

Contact information fields to use for billing and shipping contact information.

ApplePayShippingContactEditingMode

Values that indicate whether the shipping mode prevents the user from editing fields of the shipping address.

