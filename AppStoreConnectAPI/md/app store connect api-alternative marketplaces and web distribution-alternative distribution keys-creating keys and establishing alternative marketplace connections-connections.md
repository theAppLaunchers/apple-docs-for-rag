

- App Store Connect API
- Alternative Marketplaces and Web Distribution
- Alternative Distribution Keys
-  Creating keys and establishing alternative marketplace connections 

Article

# Creating keys and establishing alternative marketplace connections

Manage keys you use to sign JSON web tokens and connect marketplaces with apps.

## Overview

Use alternative distribution keys to establish an alternative marketplace. To create an alternative distribution key, you must have an existing alternative marketplace app in App Store Connect. If a marketplace app doesn’t already exist, see Create a marketplace app before continuing.

After you create these keys, generate JSON web tokens (JWTs) to connect your marketplace to the apps it distributes. Unlike the auth tokens referenced in Generating Tokens for API Requests, this JWT — the marketplace token — is specifically created by your marketplace and shared with the app developer to upload to App Store Connect.

### Generate your private key

App Store Connect uses a private cryptographic key to generate a signature for each app that your alternative marketplace distributes. During registration, marketplace apps create a public-private key pair, and send the public key to App Store Connect. The private key you create uses an Elliptic Curve Digital Signature Algorithm (ECDSA) with the P-256 curve and the SHA-256 hash algorithm.

To create your private key, open Terminal and enter the following command:

```
openssl ecparam -name prime256v1 -genkey -noout -out private_key.pem
```

This command creates the file `private_key.pem`, which contains your private key.

Important

Secure your private keys as you do other credentials, such as passwords. Don’t share your private keys, store keys in a code repository, or include keys in client-side code. Share only your public key.

### Generate your public key

Next, you create a public key from the private key you created in the previous section. The public key is a PEM-encoded PKCS#8 EC key that uses the P-256 curve. In Terminal, enter the following command:

```
openssl ec -in private_key.pem -pubout > public_key.pem
```

This command creates the file `public_key.pem`, which contains your public key. Run this command any time to generate a copy of your public key file. To request your existing public key from App Store Connect, see Read an app’s alternative distribution key.

### Create an alternative distribution key

Next, upload your public key to App Store Connect using the endpoint described in Add an alternative distribution key.

An alternative distribution key applies to all apps in your account. You can optionally make an application-specific alternative distirbution key by adding the app Apple ID for your marketplace app in the `relationships` object in the JSON payload when calling Add an alternative distribution key. You can find this app Apple ID by calling List Apps and filtering for your app name or by going to App Store Connect. This relationship is optional. If you don’t include a relationship to an app Apple ID, the alternative distribution key is associated with all alternative distubution apps on your account.

To access your marketplace app’s app Apple ID, log in to App Store Connect.

1.  Select Apps.

2.  Select your marketplace app from the list.

3.  Under General, select App Information.

4.  Scroll down to General Information, and locate your app Apple ID below your SKU.

The following request uploads the public key to App Store Connect:

```
POST https://api.appstoreconnect.apple.com/v1/alternativeDistributionKeys
{
  "data": {
    "type": "alternativeDistributionKeys",
    "id": null,
    "attributes": {
      "publicKey": "-----BEGIN PUBLIC KEY-----\nMFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAE7rsxeCw+hrwRgStk0J2vYmnGQZha\ngSt0fm511aTjpDVsaIy9z7jmUKjJ1jgb8P5UKmQfmw0ovD+fNTSefjrw5A==\n-----END PUBLIC KEY-----\n"
    }
  }
}
```

### Obtain Developer ID

When developers request to distribute their app on your marketplace, you give them a JWT that’s signed with the private key you created earlier. They upload the JWT to App Store Connect, which uses your public key to verify that the token signature is authentic and creates the relationship to your app marketplace.

Ask the app developer for their Developer ID, to learn more, see Manage distribution on an alternative app marketplace.

### Create the JSON web token

Generate the marketplace token after creating the alternative distribution key and receiving the Developer ID from the app developer. To generate a signed JWT:

1.  Create the JWT header.

2.  Create the JWT payload.

3.  Sign the JWT.

To create a JWT for the app developer to upload to App Store Connect, use the information in the following table to fill in the header details:

| Header Field | Description |
|----|----|
| `alg` | The algorithm used to sign the token. For marketplace tokens, use `ES256` as a `String`. |
| `typ` | The type of the JWT. For marketplace tokens, use `JWT` as a `String`. |

The JWT payload contains information specific to the App Store Connect APIs, such as the issuer, issued at, expiration time, audience, principal developer identifier, and nonce. Use the information in the following table to fill in the payload claims:

| Payload Claim | Description |
|----|----|
| `iss` | The *issuer* registered claim identifies the principal (or “Verifier”) that issued the token. Because the token belongs to your marketplace, use the marketplace’s app Apple ID, as a `String`. |
| `iat` | The *issued* *at* registered claim indicates the time at which you generated the token, in terms of the number of seconds following the epoch (January 1 1970 00:00:00), in UTC, as an `Int`. |
| `exp` | The *expiration time* registered claim identifies the time on or after which the token expires, in terms of the number of seconds following the epoch (January 1 1970 00:00:00), in UTC, as an `Int`.  Use an expiration time less than 7 days into the future. |
| `aud` | The *audience* registered claim identifies the intended recipient of the token. Because the token is for App Store Connect APIs, use `appstoreconnect-v1` as the audience. |
| `pid` | The *principal developer identifier* registered claim identifies the user (or “Holder”) of the token. Because the user of the token is the alternative distribution app developer, use the app’s Developer ID, as a `String`. |

### Sign the token and share it with the app developer

After creating the JWT, sign it with the private key you created earlier using ECDSA with the P-256 curve and the SHA-256 hash algorithm. A decoded token has the following format:

```
{
  "alg": "ES256",
  "typ": "JWT"
}
{
  "iss": "512345679",
  "iat": 1623085200,
  "exp": 1623086400,
  "aud": "appstoreconnect-v1",
  "pid": "57246542-96fe-1a63-e053-0824d011072a"
}
```

There are a variety of open-source libraries in various programming language for creating and signing JWTs. For more information, see JWT.io.

After you sign the JWT, provide the token to the app developer so they can upload it to App Store Connect, which uses your public key to verify that the token signature is authentic and creates the relationship to your app marketplace. While uploading the JWT, the app developer selects the apps they want to associate with your marketplace. To learn how an app developer can associate their apps with your marketplace and upload your JWT, see Manage distribution on an alternative app marketplace.

## See Also

### Creating and reading keys

Creating and configuring keys for web distribution

Manage keys you use to sign JSON web tokens (JWTs).

Add an alternative distribution key

Add an alternative distribution key for your alternative marketplace app or web distribution.

List alternative distribution keys

List the alternative distribution key for your account.

Read alternative distribution key information

Read the public key information for a specific alternative distribution key.

Remove an alternative distribution key

Remove an alternative distribution key from your account.

