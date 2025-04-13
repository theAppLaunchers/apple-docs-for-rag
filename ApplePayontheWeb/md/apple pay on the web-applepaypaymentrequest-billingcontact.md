

- Apple Pay on the Web
- ApplePayPaymentRequest
-  billingContact 

Instance Property

# billingContact

Billing contact information for the user.

Safari Desktop 10.0+Safari Mobile 10.0+

``` source
ApplePayPaymentContact billingContact;
```

## Discussion

If you have an up-to-date billing address on file, you can set it here. This billing address appears in the payment sheet. The user can either use the address you specify or select a different address.

Note

If you supply a billing address, you must also request “`postalAddress`” in requiredBillingContactFields.

## See Also

### Providing known contact information

shippingContact

Shipping contact information for the user.

ApplePayPaymentContact

Contact information fields to use for billing and shipping contact information.

