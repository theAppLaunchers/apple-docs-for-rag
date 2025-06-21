Web Service

# Apple Maps Server API

Reduce API calls and conserve device power by streamlining your app’s georelated searches.

Apple Maps Server API 1.2+

## [Overview](/documentation/AppleMapsServerAPI#overview)

Use this web-based service to streamline your app’s API by moving georelated searches for places, points of interest, geocoding, directions, possible autocompletions for searches, and estimated time of arrival (ETA) calculations from inside your app to your server.

To try the Maps Server API, generate a temporary token as described in [Creating a Maps token](/documentation/MapKitJS/creating-a-maps-token). Use these credentials to access the API from your app, or use them on [Try Maps Server API](https://developer.apple.com/maps/try-maps-server-api/).

The Apple Maps Server API is a web-based API similar to the [MapKit JS](/documentation/MapKitJS) API, and uses the same authorization infrastructure. It requires authorization using a JSON Web Token (JWT) for API calls. You obtain a key for creating the token when you complete the setup in your Apple Developer account.

To start using the API, you first need to generate an identifier and a private key, and authenticate with the service, following the steps below:

*   To create an identifier and private key, follow the steps in [Creating a Maps identifier and a private key](/documentation/applemapsserverapi/creating-a-maps-identifier-and-a-private-key).
    
*   To create tokens from your identifier and private key with the Apple Maps Server API, follow the steps in [Creating and using tokens with Maps Server API](/documentation/applemapsserverapi/creating-and-using-tokens-with-maps-server-api).
    
*   Use the Token API to [`Generate a Maps token`](/documentation/applemapsserverapi/-v1-token) for API access.
    

The service provides up to 25,000 service calls per day per team between Apple Maps Server API and MapKit JS. If your app exceeds this quota, the service returns an HTTP 429 error (Too Many Requests) and your app needs to retry later. If your app requires a larger daily quota, submit a [quota increase request form](https://developer.apple.com/contact/request/mapkitjs/).

## [Topics](/documentation/AppleMapsServerAPI#topics)

### [Essentials](/documentation/AppleMapsServerAPI#Essentials)

[

Creating and using tokens with Maps Server API](/documentation/applemapsserverapi/creating-and-using-tokens-with-maps-server-api)

Sign JSON Web Tokens to use Maps Server API and debug common signing errors.

[

Creating a Maps identifier and a private key](/documentation/applemapsserverapi/creating-a-maps-identifier-and-a-private-key)

Create a Maps identifier and a private key before generating tokens for MapKit JS.

[`Generate a Maps token`](/documentation/applemapsserverapi/-v1-token)

Returns a JWT maps access token that you use to call the service API.

[

Debugging an Invalid token](/documentation/applemapsserverapi/debugging-an-invalid-token)

Inspect the JavaScript console logs, the token, and events to determine why a token is invalid.

[

API Reference

Common objects](/documentation/applemapsserverapi/common-objects)

Understand the common JSON objects that API responses contain.

[

Integrating the Apple Maps Server API into Java server applications](/documentation/applemapsserverapi/integrating-the-apple-maps-server-api-into-java-server-applications)

Streamline your app’s API by moving georelated searches from inside your app to your server.

### [Geocoding](/documentation/AppleMapsServerAPI#Geocoding)

[`Geocode an address`](/documentation/applemapsserverapi/-v1-geocode)

Returns the latitude and longitude of the address you specify.

[`Reverse geocode a location`](/documentation/applemapsserverapi/-v1-reversegeocode)

Returns an array of addresses present at the coordinates you provide.

### [Searching](/documentation/AppleMapsServerAPI#Searching)

[`type AddressCategory`](/documentation/applemapsserverapi/addresscategory)

Search categories related to political geographical boundaries.

[`type SearchACResultType`](/documentation/applemapsserverapi/searchacresulttype)

An enumerated string that indicates the result type for the search request.

[`type SearchResultType`](/documentation/applemapsserverapi/searchresulttype)

An enumerated string that indicates the result type for the search autocomplete request.

[`object AlternateIdsResponse`](/documentation/applemapsserverapi/alternateidsresponse)

A list of alternate Place IDs and associated errors.

[`object AlternateIdsResponse.AlternateIds`](/documentation/applemapsserverapi/alternateidsresponse/alternateids)

Contains a list of alternate Place IDs for a given Place ID.

[`object PlacesResponse`](/documentation/applemapsserverapi/placesresponse)

A list of Place IDs and errors.

[`object PlacesResponse.PlaceLookupError`](/documentation/applemapsserverapi/placesresponse/placelookuperror)

An error associated with a lookup call.

[`Search for places that match specific criteria`](/documentation/applemapsserverapi/-v1-search)

Find places by name or by specific search criteria.

[`Search for places that meet specific criteria to autocomplete a place search`](/documentation/applemapsserverapi/-v1-searchautocomplete)

Find results that you can use to autocomplete searches.

[`Search for a place using an identifier`](/documentation/applemapsserverapi/-v1-place-:id)

Obtain a Place object for a given Place ID.

[`Search for places using mulitple identifiers`](/documentation/applemapsserverapi/-v1-place)

Obtain a set of Place objects for a given set of Place IDs.

[`Obtain a list of alternate place identifiers`](/documentation/applemapsserverapi/-v1-place-alternateids)

Get a list of alternate Place IDs given one or more Place IDs.

### [Directions](/documentation/AppleMapsServerAPI#Directions)

[`Search for directions and estimated travel time between locations`](/documentation/applemapsserverapi/-v1-directions)

Find directions by specific criteria.

[`Determine estimated arrival times and distances to one or more destinations`](/documentation/applemapsserverapi/-v1-etas)

Returns the estimated time of arrival (ETA) and distance between starting and ending locations.