

- CKTool JS
- PromisesApi
-  deleteZone 

Instance Method

# deleteZone

Deletes a zone.

CKTool JS 1.2.15+

``` source
CancellablePromise deleteZone(
 DeleteZoneParams params
);
```

## Parameters 

`params`  

A dictionary as described in the Discussion section.

## Return Value

A `CancellablePromise` with the following resolutions.

## Discussion

If the promise is successful, it will resolve with one of the following dictionaries:

- `{ statusCode: 204 }`

The promise may reject and throw the following:

- `DocumentedResponseError`, if the HTTP status code is 421. The result member will be a dictionary conforming to AuthenticationRequiredError.

- `DocumentedResponseError`, if the HTTP status code is none of the above and in the range 400 to 599. The result member will be a dictionary conforming to RequestError.

- `ValidationError`, if the parameters to the method are incorrect.

- A `FetchError` descendant, if there is a problem with the network request. A reference to the request object can be used to examine the underlying cause.

## Discussion

The `params` dictionary has the following properties:

```
dictionary DeleteZoneParams {
  string containerId;
  CKEnvironment environment;
  string databaseType;
  string zoneName;
}
```

- `containerId`: The container identifier. See `Container`.

- `environment`: The container environment. For valid values, see `CKEnvironment`.

- `databaseType`: The database type. For valid values, see `CKDatabaseType`.

- `zoneName`: The zone name. See `CKDBZone`.

If the operation completes successfully, the server returns a success response.

## See Also

### Zone Management

createZone

Creates a new zone.

getZone

Returns details for a zone.

getZones

Returns a collection of zones.

