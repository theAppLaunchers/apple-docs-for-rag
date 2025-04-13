

- AdAttributionKit
-  Registering an ad network 

Article

# Registering an ad network

Use the AdAttributionKit APIs for your ad campaigns after registering your ad network with Apple.

## Overview

Note

You can use the ad network ID that you receive during SKAdNetwork registration with AdAttributionKit.

Ad networks provide and cryptographically sign ads that are eligible for ad attribution through AdAttributionKit. Ad networks need to register with Apple before using the AdAttributionKit API.

To register your ad network, go to Ad Network ID Request Form, which prompts you to sign in and opens the request form.

When registering, you:

- Receive your ad network ID.

- Create an elliptic-curve cryptographic key pair, and share your public key with Apple for signature verification.

- Provide a URL where you receive AdAttributionKit postback requests.

## Share your ad network ID with developers

The ad network ID is a unique lowercase identifier in the format of `example123.adattribuitionkit`. Share your ad network ID with app developers who display your ads. Developers need to include your ad network ID in their app’s information property list for your impressions to qualify for postbacks.

Important

Lowercase the ad network ID string; otherwise, the system doesn’t recognize it as valid.

## Generate your private key

Ad networks use a private cryptographic key to generate a signature for each ad that an app displays. During registration, ad networks create a public-private key pair, and send the public key to Apple. The private key you create uses an Elliptic Curve Digital Signature Algorithm (ECDSA) with a prime256v1 curve.

To create your private key, open Terminal and enter the following command, replacing `companyname` with the name of your company:

```
openssl ecparam -name prime256v1 -genkey -noout -out companyname_adattribuitionkit_private_key.pem
```

Important

Secure your private keys as you do other credentials, such as passwords. Don’t share your private keys, store keys in a code repository, or include keys in client-side code. Only share your public key.

## Generate and share your public key

Next, you create a public key from the private key you created in the previous section. The public key is a PEM-encoded PKCS \#8 EC key that uses the prime256v1 curve. In Terminal, enter the following command, again replacing `companyname` with the name of your company:

```
openssl ec -in companyname_adattribuitionkit_private_key.pem -pubout -out companyname_adattribuitionkit_public_key.pem
```

This command creates the file `companyname_adattribuitionkit_public_key.pem`, which contains your public key. Run this command anytime to generate a copy of your public key file.

Send your public key file to Apple when you register your ad network.

## See Also

### Ad network registration and configuration

Configuring a publisher app

Set up a publisher app to participate in ad campaigns.

Configuring an advertised app

Prepare an advertised app to participate in ad campaigns.

