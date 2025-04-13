

- CKTool JS
- PromisesApi
-  getContainers 

Instance Method

# getContainers

Fetches containers for a team.

CKTool JS 1.2.15+

``` source
CancellablePromise getContainers(
 GetContainersParams params
);
```

## Parameters 

`params`  

A dictionary as described in the Discussion section.

## Return Value

A `CancellablePromise` with the following resolutions.

## Discussion

If the promise is successful, it will resolve with one of the following dictionaries:

- `{ statusCode: 200; result: ContainersResponse }`

The promise may reject and throw the following:

- `DocumentedResponseError`, if the HTTP status code is 421. The result member will be a dictionary conforming to AuthenticationRequiredError.

- `DocumentedResponseError`, if the HTTP status code is none of the above and in the range 400 to 599. The result member will be a dictionary conforming to RequestError.

- `ValidationError`, if the parameters to the method are incorrect.

- A `FetchError` descendant, if there is a problem with the network request. A reference to the request object can be used to examine the underlying cause.

## Discussion

The `params` dictionary has the following properties:

```
dictionary GetContainersParams {
  string teamId;
  Int32? limit;
  string? startingAfterKey;
  string? endingBeforeKey;
  SortDirection? sortDirection;
  string? q;
  ContainersSortByField? sortBy;
  boolean? showHidden;
}
```

- `teamId`: The team identifier. For more information, see `Team`.

- `limit`: The limit of results returned. If set to 0, all results are returned.

- `startingAfterKey`: The record key for forward pagination. If provided, the results start after the record referred to by this key.

- `endingBeforeKey`: The record key for backward pagination. If provided, the results end before the record referred to by this key.

- `sortDirection`: A value that indicates the sort order of the result set. The default value is `SortDirection.ASC`. For valid values, see `SortDirection`.

- `q`: An optional search query string. If provided, the server only returns containers with names or identifiers containing the query string. Wildcards are not supported.

- `sortBy`: An optional field to sort on. When not provided, the server uses the ID as the sort field. For valid values, see `ContainersSortByField`.

- `showHidden`: if set to true, response will contain hidden containers.

If successful, the result contains a `ContainersResponse` object. For more information about containers, see `Container`.

## See Also

### Database Management

exportSchema

Downloads the container’s schema.

importSchema

Uploads a file that defines the new schema for the container.

resetConfigToProduction

Resets the container configuration to production.

resetToProduction

Resets the schema of the environment to production.

validateSchema

Validates the uploaded schema file for the container.

