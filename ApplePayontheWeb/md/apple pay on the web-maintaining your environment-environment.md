

- Apple Pay on the Web
-  Maintaining Your Environment 

Article

# Maintaining Your Environment

Prevent interruptions in your Apple Pay service by keeping certificates and domain verification current.

## Overview

To prevent interruptions in your website’s Apple Pay service, your domain verification and the certificates that you set up in Configuring Your Environment must remain valid. While your merchant ID never expires, certificates and domain verification do expire, as follows:

- The Payment Processing certificate expires every 25 months.

- The Merchant Identity certificate expires every 25 months.

- A registered domain’s verification expires when its SSL certificate expires.

Important

As the expiration dates for certificates and domain verifications approach, Apple sends an email reminder to the Admin and the Account Holder of the Apple Developer Account. Ensure that your organization continually monitors the inbox of these users so you can renew certificates before they expire to avoid interruptions to your Apple Pay service.

### View Expiration Dates and Update Certificates

You can view expiration dates and update your certificates on the Apple developer website by following these steps:

- Sign in to your account — you need to be an Account Holder or Admin.

- Open the Certificates, Identifiers, and Profiles page.

- Under Identifiers, select Merchant IDs.

- Select your domain’s ID and select Edit.

Certificate expiration dates appear for each of the certificates listed on the page. You can also update the certificates on this page.

### Renew Your Domain Verification

Domain verification expires on the same date that your domain’s SSL certificate expires. Apple servers check if SSL certificates have been renewed at 30, 15, and 7 days before expiration.

- If you update the SSL certificate before it expires, Apple detects the renewed certificate and the domain remains verified. No further action is required on your part.

- If the SSL certificate expires and is not replaced before expiring, you must redo domain verification in your Apple Developer Account. See Verify a Merchant Domain for additional information.

Make sure that the Apple servers — listed in Setting Up Your Server — can access the URL you used to validate the merchant domain. If the URL is behind a proxy or redirect the Apple servers won’t be able to access it. The URL may be similar to `https://yourdomain.com/.well-known/apple-developer-merchantid-domain-association`.

## See Also

### Apple Pay setup

Setting Up Your Server

Set up your server for secure communications with Apple Pay.

Configuring Your Environment

Create your Apple Pay merchant ID and certificates, and verify your domain.

