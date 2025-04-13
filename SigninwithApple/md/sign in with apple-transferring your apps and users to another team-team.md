

- Sign in with Apple
-  Transferring your apps and users to another team 

Article

# Transferring your apps and users to another team

Migrate Sign in with Apple users to another team.

## Overview

Sign in with Apple maintains an assocation between your developer team, your apps, and your users. If your app transfers to another team, the app’s users also transfer. *Migration* is the process of moving your apps and its associated users to a recipient team. Both your team and the recipient team must perform certain steps in order to complete the migration process.

Note

If your app supports multiple platforms, ungroup the apps before starting the transfer. The App Store Connect app won’t let you transfer an app if it’s part of an app group.

For more information on app groups and ungrouping, see Group Apps for Sign in with Apple.

### Protect user privacy

Every Sign in with Apple user has a user identifier. Apple issues a signed ID token for the user that contains the user identifier and, if applicable, the private email address specific to your team. All of your applications share the same identifier for the user.

To avoid exposing the user identifier to a different team, Apple generates a *transfer identifier* for each user. The transfer identifier is unique to the recipient team and remains stable throughout the migration process. This allows you to transfer the user data to the recipient without exposing your team-scoped identifiers and private email addresses.

Note

When exporting the data from your database to transfer to the recipient team, you must exclude the team-scoped identifier and private email address, and include only the transfer identifier to identify the user.

The transfer identifer is specific to the target team and has a one-to-one mapping with your team-scoped user identifier. If you transfer more than one application to the same recipient team (even over time), the transfer identifier for a given user remains the same across all applications.

Because the transfer identifier remains stable across teams, it acts as a bridge between your team-scoped identifiers and the recipient’s team-scoped identifiers for the user. Since the transfer identifier is specific to the transfer process and to the teams, it’s not usable elsewhere.

As part of preparing your data for the recipient team, you must generate a transfer identifier for each user in your database using a REST service endpoint provided by Apple.

### Obtain the user access token

In order to transfer your users, you must obtain their user access token and generate a transfer identifier. You normally obtain the user access token when your user signs in, or when you validate a stored refresh token.

If you don’t have an access token for any user, you can generate user access tokens with your client credential and set `scope` as `user.migration` with the following HTTP POST method.

```
POST /auth/token HTTP/1.1
Host: appleid.apple.com
Content-Type: application/x-www-form-urlencoded

grant_type=client_credentials&scope=user.migration&client_id={client_id}&client_secret={client_secret}
```

The HTTP POST method includes these parameters:

`grant_type`  
The type of grant requested. Set to `client_credentials`. Access the migration endpoint using your client application’s credentials.

`scope`  
The scope of the migration. Set to `user.migration`.

`client_id`  
The identifier (App ID or Services ID) for the transferring app. The identifier must not include your Team ID, to help mitigate the possibility of exposing sensitive data to the end user.

`client_secret`  
The client secret of the transferring team, represented as a JSON Web Token (JWT). The JWT payload should contain a `sub` claim that matches the transferring app’s bundle ID or associated Services ID. For more information on generating a client secret, see Creating a client secret.

Expect an HTTP POST response similar to the following example.

```
HTTP/1.1 200 OK
Content-Type: application/json;charset=UTF-8
Cache-Control: no-store
Pragma: no-cache

{
  "access_token":"adg6105ed7a4def32adec143038877c2b.0.nx.20LreF67Or9",
  "token_type":"Bearer",
  "expires_in":3600
}
```

### Generate the transfer identifier

With the user access token, invoke the `userMigrationInfo` endpoint. Provide the team-scoped identifier of the user as input with the following HTTP POST method.

```
POST /auth/usermigrationinfo HTTP/1.1
Host: appleid.apple.com
Content-Type: application/x-www-form-urlencoded
Authorization: Bearer {access_token}

sub={sub}&target={recipient_team_id}&client_id={client_id}&client_secret={client_secret}
```

The HTTP POST method includes these parameters:

`sub`  
The team-scoped user identifier that Apple provides.

`target`  
The Team ID of the recipient team to which you transfer the application.

`client_id`  
The identifier (App ID or Services ID) for the transferring app. The identifier must not include your Team ID, to help mitigate the possibility of exposing sensitive data to the end user.

`client_secret`  
The client secret of the transferring team, represented as a JSON Web Token (JWT). The JWT payload should contain a `sub` claim that matches the transferring app’s bundle ID or associated Services ID. For more information on generating a client secret, see Creating a client secret.

Expect an HTTP POST response similar to the following example.

```
HTTP/1.1 200 OK
Content-Type: application/json;charset=UTF-8
Cache-Control: no-store
Pragma: no-cache

{
  "transfer_sub":"760417.ebbf12acbc78e1be1668ba852d492d8a.1827"
}
```

The response contains the `transfer_sub`, with the transfer identifier for the user that you send to the recipient team.

Note

After the recipient team accepts the transfer, you have 60 days to generate transfer identifiers for the client.

### Deliver users to the recipient team

Once you’ve generated transfer identifiers for each of your users, prepare to export this information by excluding the team-scoped identifier and the private email address from the payload. Include only the transfer identifier to identify the user to the recipient team.

If you need to communicate with users during this process, do so using their private email addresses.

Important

If a user doesn’t use any other applications from your team, you’ll no longer be able to communicate with them using their private email address after the transfer.

## See Also

### Transfers across teams

Bringing new apps and users into your team

Receive Sign in with Apple users and associated apps from another team.

