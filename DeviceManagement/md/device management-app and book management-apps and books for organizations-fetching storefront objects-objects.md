

- Device Management
- App and Book Management
- Apps and Books for Organizations
-  Fetching storefront objects 

API Collection

# Fetching storefront objects

Pick a region-specific geographic location to retrieve catalog information from.

## Overview

Apple services operate in many countries, regions, and languages. Content varies from one geographic region to another, so each request needs to contain a *storefront object* that defines the region and the supported languages for that region. For most requests, you specify the storefront associated with the current user, but you may also specify other storefronts as needed. For example, you might specify a storefront that better matches the user’s preferred language.

Each storefront has a default language and may support one or more additional languages. For example, the United States storefront includes American English as the default language, but also includes Mexican Spanish as an additional supported language. Apple services automatically localize responses using the storefront’s default language, but you can localize to a different language using the `l query` parameter. The value of that parameter needs to be one of the values in the `supportedLanguageTags` attribute of the storefront object. For example, the following request asks the U.S. storefront to return an album in the Mexican Spanish (`es-MX`) localization:

```
GET https://api.ent.apple.com/v1/catalog/us/stoken-authenticated-apps?ids=2001350931&platform=iphone&l=es-MX
```

## Topics

### Requesting a catalog storefront

Get a Storefront

Fetch a single storefront by using its identifier.

Get Multiple Storefronts

Fetch one or more storefronts by using their identifiers.

Get All Storefronts

Fetch all the storefronts in alphabetical order.

### Handling the response

object Storefronts

A resource object that represents a region that the content is available in, and supported languages for that region.

## See Also

### Essentials

Generating developer tokens

Create a JSON Web Token to authorize your requests to the Apps and Books for Organizations API.

Handling requests and responses

Write a request for app or book metadata and handle responses from the API.

Fetching resources with extended attributes

Specify additional attributes for the API to include in a response.

Common Objects

Understand the common JSON objects that framework responses contain.

