

- Enterprise Program API
-  Creating API Keys for Enterprise Program API 

Article

# Creating API Keys for Enterprise Program API

Create API keys to sign JSON Web Tokens (JWTs) and authorize API requests.

## Overview

The Enterprise Program API requires a JSON Web Token (JWT) to authorize each request you make to the API. You generate JWTs using an API key downloaded from the Apple Developer website.

An API key has two parts: a public portion that Apple keeps, and a private key that you download. You can use the private key to sign tokens that authorize access to your data in the Apple Developer website.

Important

Secure your private keys as you do for other credentials, such as usernames and passwords. If you suspect a private key is compromised, immediately revoke the key in the Apple Developer website. See Revoking API Keys for details.

Enterprise Program API keys are unique to the Enterprise Program API and you can’t use them for other Apple services.

### Generate a Enterprise Program API Key and Assign It a Role

When you create an API key, assign it a role that determines the key’s access to areas of the Enterprise Program API and permissions for performing tasks. For example, keys with the Admin role have broad permissions and can do things like create new users and delete users. The other available role is Developer, which is restricted to provisioning actions, such as creating provisioning profiles and managing development certificates.

When you create an API key, assign it a role that determines the key’s access to areas of the Enterprise Program API and permissions for performing tasks. To learn more information about user roles and permissions, see the Apple Developer website.

To generate Enterprise Program API keys, you must have an Admin account for your developer team in the Apple Developer website. You can generate multiple API keys with the roles you choose.

To generate a key to use with the Enterprise Program API, log in to the Apple Developer website and:

1.  Select Users and Access, and then select the Integrations tab.

2.  Click Generate API Key or the Add (+) button.

3.  Enter a name for the key. The name is for your reference only and isn’t part of the key itself.

4.  Under Access, select the role for the key.

5.  Click Generate.

The new key’s name, key ID, a download link, and other information appears on the page.

### Download and Store a Enterprise Program API Private Key

Once you’ve generated your API key, you can download the private half of the key. The private key is available for download a single time, to begin log in to the Apple Developer website and:

1.  Select Users and Access, and then select the Integrations tab.

2.  Click Download link next to the new API key.

The download link only appears if you haven’t downloaded the private key. Apple doesn’t keep a copy of the private key.

Important

Keep your API keys secure and private. Don’t share your keys, store keys in a code repository, or include keys in client-side code. If the key becomes lost or compromised, remember to revoke it immediately. See Revoking API Keys for more information.

## See Also

### Essentials

Generating Tokens for API Requests

Create JSON Web Tokens (JWTs) signed with your private key to authorize API requests.

Revoking API Keys

Revoke unused, lost, or compromised private keys.

Identifying Rate Limits

Recognize the rate limits that REST API responses provide and handle them in your code.

Enterprise Program API Release Notes

Learn about new features and updates in the Enterprise Program API.

