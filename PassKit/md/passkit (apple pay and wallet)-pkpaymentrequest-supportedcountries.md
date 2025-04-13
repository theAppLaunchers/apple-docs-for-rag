

- PassKit (Apple Pay and Wallet)
- PKPaymentRequest
-  supportedCountries 

Instance Property

# supportedCountries

A list of ISO 3166 country codes to limit payments to cards from specific countries or regions.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.1+macOS 10.13+visionOS 1.0+watchOS 4.0+

``` source
var supportedCountries: Set? { get set }
```

## Discussion

Use the list of supported countries or regions to limit payments to cards that were issued in specific countries or regions. For example, debit cards may expect transactions only in the country or region where the card was issued. Indicate the supported countries or regions by using ISO 3166 country codes.

The supported countries or regions list does not affect the currency used for the transaction.

## See Also

### Setting currency and region information

var currencyCode: String

The three-letter ISO 4217 currency code that determines the currency the payment request uses.

var countryCode: String

The merchant’s two-letter ISO 3166 country code.

