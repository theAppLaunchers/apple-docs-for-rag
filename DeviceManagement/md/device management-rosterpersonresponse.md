

- Device Management
-  RosterPersonResponse 

Object

# RosterPersonResponse

The response that contains the people in the organization.

Device Assignment ServicesVPP License Management

``` source
object RosterPersonResponse
```

## Properties

`cursor`

`string`

A hex string that should be used for the next request to paginate. This field data type has a maximum length of 512 UTF-8 characters.

`more_to_follow`

`boolean`

Indicates whether the request’s limit and cursor values resulted in only a partial list of classes. If `true`, the Mobile Device Management server should then make another request (starting from the newly returned cursor) to obtain additional records.

`persons`

`[`RosterPerson`]`

Provides information about persons, both teachers and students, sorted in lexical order by a person `source_system_identifier`. The organization must provide this identifier to Apple.

