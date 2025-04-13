

- Device Management
-  RegisterVppUserRequest 

Object

# RegisterVppUserRequest

The request for registering a user.

Device Assignment ServicesVPP License Management

``` source
object RegisterVppUserRequest
```

## Properties

`clientUserIdStr`

`string`

 (Required) 

The identifier supplied by the client when registering a user. The identifier must be unique within the organization.

`email`

`string`

The user’s email address.

`managedAppleIDStr`

`string`

The Apple ID associated with the user. This ID’s organization must match the organization of the provided `sToken`.

See Associating an Apple ID with a Volume Purchase Program (VPP) User for more information.

`sToken`

`string`

 (Required) 

The authentication token. For more information, see Authentication.

## Discussion

### ClientUserIdStr

The `clientUserIdStr` must be unique within the organization and may not be changed once a user is registered. It should not, for example, be an email address, because an email address might be reused by a future user. It can be, for example, the GUID of the user.

When a user is first registered, the userʼs initial status is `Registered`.

If the user has already been registered, as identified by `clientUserIdStr`, the following occurs:

- If the user’s status is `Registered` or `Associated`, that active user account is returned.

- If the user’s status is `Retired` and the user has never been assigned to an iTunes account, the account’s status is changed to `Registered` and the existing user is returned.

- If the user’s status is `Retired` and the user has previously been assigned to an iTunes account, a new account is created.

Thus, it is possible for more than one user record to exist for the same `clientUserIdStr` value — one for each iTunes account with which the `clientUserIdStr` value has been associated in the past (in addition to a currently active record or a retired and never-associated record). Each of these users has a unique `userId` value. Over time, with iTunes Store assignment, retirement, and reassignment, it is possible for the active user’s `userId` value for a given `clientUserIdStr` to change.

Further, if two user identifiers exist for a given `clientUserIdStr`, one assigned to an iTunes account and the other unassigned, and a user accepts an invitation to be associated, it is possible for the user to use the same iTunes account he or she used previously. If the user does, the unassigned user record gets marked with the `Retired` status, and the formerly retired user record gets moved to the `Associated` status.

## See Also

### Request and Response

object RegisterVppUserResponse

The response from registering a user.

