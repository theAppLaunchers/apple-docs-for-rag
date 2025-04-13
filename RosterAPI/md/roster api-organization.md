

- Roster API
-  Organization 

Object

# Organization

Information about an Apple School Manager organization.

Roster API 1.0.0+

``` source
object Organization
```

## Properties

`dateCreated`

`string`

The date the organization object was created in Apple School Manager. The date string is in ISO 8601 format.

`dateLastModified`

`string`

The date the organization object was modified in Apple School Manager. The date string is in ISO 8601 format.

`domains`

`[`Domain`]`

A list of `Domains` objects.

`id`

`string`

A unique identifier for this organization.

`name`

`string`

This organization’s name.

`type`

`string`

The organization’s type. This string’s value is `EDUCATION`.

## See Also

### Information about the organization

Read the organization

Returns information about the Apple School Manager organization.

object Domain

A DNS domain name associated with an Apple School Manager organization.

