Web Service

# Roster API

Read information about people and classes from an Apple School Manager organization.

Roster API 1.0.0+

## [Overview](/documentation/RosterAPI#overview)

Roster API provides access to people and class information in Apple School Manager (ASM). Use this REST API if you need to support a workflow within your app to automatically create student or teacher records in advance of the first day of school. A typical use case is when your app requires teachers to input assignments and due dates for students in each class.

Accessing the user and class information requires authorization from an administrator of the ASM organization. When you begin the Roster API authorization flow, use the scopes defined below to request the appropriate level of access:

`edu.users.read`

Request read access to ASM users

`edu.classes.read`

Request read access to ASM classes

At the end of the authorization flow, use the access token you receive to access the Roster API endpoints, which you use to fetch people and class information. For more information on requesting an access token, see [Generate and validate tokens](/documentation/signinwithapplerestapi/generate_and_validate_tokens).

Include the access token you receive in the Authorization header for every request. The Roster API associates the access token with an ASM organization. The endpoints return user and class information contained within that ASM organization. The unique account identifier from Sign in with Apple at Work & School is the same identifier provided in the Roster API user information. You may use this identifier to associate user information from the Roster API with a user signing in to your app.

## [Topics](/documentation/RosterAPI#topics)

### [Essentials](/documentation/RosterAPI#Essentials)

[

Obtaining information about people and classes](/documentation/rosterapi/obtaining-information-about-people-and-classes)

Prepare your app to request organizational information from a server.

[

Validating with the Roster API test scope](/documentation/rosterapi/validating-with-the-roster-api-test-scope)

Use test data to ensure your integration with the Roster API works correctly.

### [Authentication](/documentation/RosterAPI#Authentication)

[

Integrating with Roster API and Sign in with Apple](/documentation/rosterapi/integrating-with-roster-api-and-sign-in-with-apple)

Associate someone’s Managed Apple ID with their identity in Apple School Manager.

### [Information about users](/documentation/RosterAPI#Information-about-users)

[`Read a user`](/documentation/rosterapi/returns-a-specific-user-in-an-apple-school-manager-organization)

Read a user in an Apple School Manager organization.

[`object User`](/documentation/rosterapi/user)

A user in an Apple School Manager organization.

[`object RoleLocation`](/documentation/rosterapi/rolelocation)

A mapping between a role assumed by a user in an Apple School Manager organization, and the corresponding location.

[`List users`](/documentation/rosterapi/returns-a-list-of-users-in-an-apple-school-manager-organization)

List users in an Apple School Manager organization.

[`List users in a class`](/documentation/rosterapi/returns-a-users-for-an-apple-school-manager-class)

List users in a class of an Apple School Manager organization.

[`object Users`](/documentation/rosterapi/users)

A list of users, with a token for pagination.

### [Information about classes](/documentation/RosterAPI#Information-about-classes)

[`Read a class`](/documentation/rosterapi/returns-a-specific-class-in-an-apple-school-manager-organization.)

Read a class from an Apple School Manager organization.

[`object Class`](/documentation/rosterapi/class)

A class in an Apple School Manager organization.

[`List classes`](/documentation/rosterapi/returns-a-list-of-classes-for-an-apple-school-manager-organization)

List classes in an Apple School Manager organization.

[`object Classes`](/documentation/rosterapi/classes)

A list of classes, with a token for pagination.

### [Information about locations](/documentation/RosterAPI#Information-about-locations)

[`Read a location`](/documentation/rosterapi/returns-a-specific-location-in-an-apple-school-manager-organization)

Returns a specific location in an Apple School Manager organization.

[`object Location`](/documentation/rosterapi/location)

A location in an Apple School Manager organization.

[`List locations`](/documentation/rosterapi/returns-a-list-of-locations-for-an-apple-school-manager-organization)

Returns a list of locations in an Apple School Manager organization.

[`object Locations`](/documentation/rosterapi/locations)

A list of locations, with a token for pagination.

### [Information about the organization](/documentation/RosterAPI#Information-about-the-organization)

[`Read the organization`](/documentation/rosterapi/returns-organization-infrmation)

Returns information about the Apple School Manager organization.

[`object Organization`](/documentation/rosterapi/organization)

Information about an Apple School Manager organization.

[`object Domain`](/documentation/rosterapi/domain)

A DNS domain name associated with an Apple School Manager organization.