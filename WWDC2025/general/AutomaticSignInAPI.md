Framework

# Automatic Sign-In API

Manage sign-in tokens that facilitate single sign-on across the devices of your media streaming service customers from your web server.

Automatic Sign-In API 1.0+

## [Overview](/documentation/AutomaticSignInAPI#overview)

This API works in conjunction with [Video Subscriber Account](/documentation/videosubscriberaccount) to manage sign-in tokens from your web server that implement the [`VSUserAccountManager`](/documentation/videosubscriberaccount/vsuseraccountmanager) Automatic Sign-In feature.

Note

For more on Automatic Sign-In for Apple devices, see [Signing people in to their media accounts automatically](/documentation/videosubscriberaccount/signing-people-in-to-media-apps-automatically).

## [Authenticate your API calls and test using the sandbox](/documentation/AutomaticSignInAPI#Authenticate-your-API-calls-and-test-using-the-sandbox)

The Automatic Sign-In API shares authentication and testing steps with the [App Store Server API](/documentation/AppStoreServerAPI). Before issuing calls to this service, perform the setup in [Authorize your API calls](/documentation/AppStoreServerAPI). To test your web server during development, see [Test using the sandbox environment](/documentation/AppStoreServerAPI).

## [Topics](/documentation/AutomaticSignInAPI#topics)

### [Token updates](/documentation/AutomaticSignInAPI#Token-updates)

[`Update Sign-In Token`](/documentation/automaticsigninapi/update-this-token-for-all-associated-users)

Updates a specific sign-in token to a new value.

[`object UpdateAutoSignInTokenRequest`](/documentation/automaticsigninapi/updateautosignintokenrequest)

The request body that contains the old sign-in token and the new sign-in token.

### [Token deletion](/documentation/AutomaticSignInAPI#Token-deletion)

[`Delete Sign-In Token`](/documentation/automaticsigninapi/delete-this-token-for-all-associated-users)

Deletes a specific sign-in token.

[`object DeleteAutoSignInTokenRequest`](/documentation/automaticsigninapi/deleteautosignintokenrequest)

The request body that contains the sign-in token to be deleted.