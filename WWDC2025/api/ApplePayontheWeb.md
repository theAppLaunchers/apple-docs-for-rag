Technology

# Apple Pay on the Web

Support Apple Pay on your website with JavaScript-based APIs.

Safari Desktop 10.0+Safari Mobile 10.0+

## [Overview](/documentation/ApplePayontheWeb#overview)

Safari supports two JavaScript APIs that let you accept Apple Pay payments from customers on your website:

*   [Payment Request API](/documentation/ApplePayontheWeb/payment-request-api), a [W3C candidate API](https://www.w3.org/TR/payment-request/)
    
*   [Apple Pay JS API](/documentation/ApplePayontheWeb/apple-pay-js-api), analogous to the [PassKit (Apple Pay and Wallet)](/documentation/PassKit) framework for Apple Pay in apps.
    

Tip

You can try out Apple Pay transactions on the demo page. See [Apple Pay on the Web Interactive Demo](https://applepaydemo.apple.com).

Apple Pay is available on all iOS devices with a Secure Element — an industry-standard, certified chip designed to store payment information safely. In macOS, users must have an Apple Pay-capable iPhone or Apple Watch to authorize the payment, or a Mac with Touch ID.

### [Apple Pay availability by region and platform](/documentation/ApplePayontheWeb#Apple-Pay-availability-by-region-and-platform)

Apple Pay is available in [supported regions](https://www.apple.com/ios/feature-availability/#apple-pay).

The Apple Pay APIs are available in Safari on the following platforms:

**Worldwide (except China)**

**China**

**Apple Pay JS**

iOS 10 and later ![](https://docs-assets.developer.apple.com/published/67dc4b07a8d84366d4cc0e812eb40b4a/spacer.png) macOS 10.12 and later

iOS 11.2 and later ![](https://docs-assets.developer.apple.com/published/67dc4b07a8d84366d4cc0e812eb40b4a/spacer.png) (Not available in macOS)

**Payment Request API**

iOS 11.3 and later ![](https://docs-assets.developer.apple.com/published/67dc4b07a8d84366d4cc0e812eb40b4a/spacer.png) macOS 10.12.6 and later, in Safari 11.1 and later

iOS 11.3 and later ![](https://docs-assets.developer.apple.com/published/67dc4b07a8d84366d4cc0e812eb40b4a/spacer.png) (Not available in macOS)

In iOS, Safari and [`SFSafariViewController`](/documentation/SafariServices/SFSafariViewController) objects support Apple Pay.

See [Checking for Apple Pay availability](/documentation/ApplePayontheWeb/checking-for-apple-pay-availability) to ensure your implementation only displays the Apple Pay button on supported devices.

Note

Regulations in some regions may require specific configurations in your implementation. For more information, see [Complying with regional regulations](/documentation/PassKit/complying-with-regional-regulations).

### [Apple Pay requirements](/documentation/ApplePayontheWeb#Apple-Pay-requirements)

The requirements for using Apple Pay on your website are:

*   Your website must comply with the Apple Pay guidelines. For more information, see [Acceptable Use Guidelines for Apple Pay on the Web](https://developer.apple.com/apple-pay/acceptable-use-guidelines-for-websites/).
    
*   You must have an Apple Developer Account and complete the registration. For more information, see [Configuring Your Environment](/documentation/ApplePayontheWeb/configuring-your-environment).
    
*   All pages that include Apple Pay must be served over HTTPS. For more information, see [Setting Up Your Server](/documentation/ApplePayontheWeb/setting-up-your-server).
    

For design guidance, see [Human Interface Guidelines > Apple Pay](https://developer.apple.com/design/human-interface-guidelines/apple-pay/overview/introduction/).

## [Topics](/documentation/ApplePayontheWeb#topics)

### [Essentials](/documentation/ApplePayontheWeb#Essentials)

[

Loading the latest version of the Apple Pay JS SDK](/documentation/applepayontheweb/loading-the-latest-version-of-apple-pay-js)

Link to the most recent autoupdating version of the Apple Pay JS SDK or a version of your choice.

### [Apple Pay setup](/documentation/ApplePayontheWeb#Apple-Pay-setup)

[

Setting Up Your Server](/documentation/applepayontheweb/setting-up-your-server)

Set up your server for secure communications with Apple Pay.

[

Configuring Your Environment](/documentation/applepayontheweb/configuring-your-environment)

Create your Apple Pay merchant ID and certificates, and verify your domain.

[

Maintaining Your Environment](/documentation/applepayontheweb/maintaining-your-environment)

Prevent interruptions in your Apple Pay service by keeping certificates and domain verification current.

### [Apple Pay Later visual merchandising widget](/documentation/ApplePayontheWeb#Apple-Pay-Later-visual-merchandising-widget)

[

Adding an Apple Pay Later visual merchandising widget](/documentation/applepayontheweb/adding-an-apple-pay-later-visual-merchandising-widget)

Configure and style Apple Pay Later visual merchandising widgets to match your website.

### [Apple order tracking button](/documentation/ApplePayontheWeb#Apple-order-tracking-button)

[

Adding a Track with Apple Wallet button](/documentation/applepayontheweb/adding-a-track-with-apple-wallet-button)

Configure and style an Apple Wallet Button to match your website.

### [Apple Pay buttons](/documentation/ApplePayontheWeb#Apple-Pay-buttons)

[

Displaying Apple Pay Buttons Using JavaScript](/documentation/applepayontheweb/displaying-apple-pay-buttons-using-javascript)

Load and configure the JavaScript Apple Pay button.

[`ApplePayButton`](/documentation/applepayontheweb/applepaybutton)

An object that displays a button either to trigger payments through Apple Pay or to prompt the user to set up a card.

[

API Reference

Displaying Apple Pay Buttons Using CSS](/documentation/applepayontheweb/displaying-apple-pay-buttons-using-css)

Use CSS templates to display Apple Pay buttons in Safari.

### [Apple Pay JavaScript APIs](/documentation/ApplePayontheWeb#Apple-Pay-JavaScript-APIs)

[

Choosing an API for Implementing Apple Pay on Your Website](/documentation/applepayontheweb/choosing-an-api-for-implementing-apple-pay-on-your-website)

Compare Apple Pay JS and Payment Request API to choose the right implementation for your website.

[

API Reference

Apple Pay on the Web version history](/documentation/applepayontheweb/apple-pay-on-the-web-version-history)

Learn about features in each version of Apple Pay on the Web.

[

API Reference

Apple Pay JS API](/documentation/applepayontheweb/apple-pay-js-api)

Implement Apple Pay on the web using Apple’s JavaScript API.

[

API Reference

Payment Request API](/documentation/applepayontheweb/payment-request-api)

Accept payments on your website with Apple Pay using the Payment Request API.

### [Apple Pay JS SDK change log](/documentation/ApplePayontheWeb#Apple-Pay-JS-SDK-change-log)

[

Apple Pay JS change log](/documentation/applepayontheweb/apple-pay-js-change-log)

Learn about new features and updates in the Apple Pay JS SDK.