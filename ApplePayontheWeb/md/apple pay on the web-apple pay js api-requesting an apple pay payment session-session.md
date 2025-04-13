

- Apple Pay on the Web
- Apple Pay JS API
-  Requesting an Apple Pay payment session 

Article

# Requesting an Apple Pay payment session

Request a valid session from the Apple Pay server.

## Overview

Use a new Apple Pay payment session for each transaction.

### Post a request

Your server posts a request using mutual TLS (mTLS) by calling the Apple Pay server’s Payment Session endpoint.

Endpoint (Global)  
`POST https://apple-pay-gateway.apple.com/paymentservices/paymentSession`

Endpoint (China region)  
`POST https://cn-apple-pay-gateway.apple.com/paymentservices/paymentSession`

The endpoint returns an opaque Apple Pay session object for Apple Pay on the web, Apple Pay on macOS, and for Apple Pay in Apple Messages for Business.

For Apple Pay on the web, you can also use the endpoint `POST https:///paymentSession` with a fully qualified validation URL that you receive in onvalidatemerchant. Be sure to allow all of the domains listed in Setting Up Your Server.

Important

Ensure that your server accesses only the validation URLs provided by Apple in Setting Up Your Server, and fails for other URLs. It’s a best practice to use a strict allow list for the validation URLs. You must send the payment session request from your server; never request the session from the client.

### Provide request parameters

Use the merchant identity certificate associated with your merchant ID in the request. See Configuring Your Environment for more information.

`merchantIdentifier`  
Your merchant ID. For payment platforms registering merchants through the Apple Pay Web Merchant Registration API, this should be the `partnerInternalMerchantIdentifier` defined for the each registered merchant.

`displayName`  
A string of 64 or fewer UTF-8 characters containing the canonical name for your store, suitable for display. A good display name remains a consistent value for the store and doesn’t contain dynamic values such as incrementing order numbers. Don’t localize the name. Use only characters from the supported character sets in the fonts listed in the table below.

`initiative`  
A predefined value that identifies the e-commerce application making the request.

`initiativeContext`  
A value you provide based on the initiative.

The values for `initiative` and `initiativeContext` depend on the kind of application you’re building:

- For Apple Pay on the web, use `“web”` for the `initiative` parameter. For the `initiativeContext` parameter, provide your fully qualified domain name associated with your Apple Pay Merchant Identity Certificate.

- For Apple Messages for Business, use `“messaging”` for the `initiative` parameter. For the `initiativeContext` parameter, provide your payment gateway URL. See Type Interactive for more information.

- For Apple Pay on macOS, use `“in_app”` for the `initiative` parameter. For the `initiativeContext` parameter, provide your developer team ID.

On supported models of MacBook Pro, the Touch Bar displays the value you supply for the `displayName` parameter. The following table lists the valid fonts.

| Language | Font                           |
|----------|--------------------------------|
| Arabic   | MyriadArabic-Regular.otf       |
| Bengali  | KohinoorBangla-Regular.otf     |
| Chinese  | PingFangTC-Regular.otf         |
| English  | SF-Compact-Text-Regular.otf    |
| Hebrew   | Myriad-Hebrew.ttc              |
| Hindi    | KohinoorDevanagari-Regular.otf |
| Japanese | PingFangTC-Regular.otf         |
| Korean   | NanumGothic.ttf                |
| Telegu   | KohinoorTelugu-Regular.otf     |
| Thai     | Ayuthaya.ttf                   |

### Receive the payment session object

In response to the `POST` request, your server receives an opaque Apple Pay session object. The session expires after five minutes.

- For Apple Pay on the web, pass the session object to the completion method, completeMerchantValidation.

- For Apple Pay in Apple Messages for Business, pass the session object to your Messaging Service Provider (MSP), which handles communicating with Apple Messages for Business on your behalf.

### Example

A session request with a JSON payload for Apple Pay on the web.

```
{
    merchantIdentifier: "merchant.com.example.mystore",
    displayName: "MyStore",
    initiative: "web",
    initiativeContext: "mystore.example.com"
}
```

The `displayName` you provide in the payload appears in the Touch Bar like this:

Note

Start Session is being phased out and replaced by Payment Session.

## See Also

### Apple Pay session

Creating an Apple Pay Session

Provide a payment request and create the session.

Providing Merchant Validation

Validate your merchant identity and receive a session object for each payment request.

ApplePaySession

A session object for managing the payment process on the web.

