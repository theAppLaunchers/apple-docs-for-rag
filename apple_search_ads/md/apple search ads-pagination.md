

- Apple Search Ads
-  Pagination 

Object

# Pagination

The procedure to refine returned results using limit and offset parameters.

Search Ads 2.0+

``` source
object Pagination
```

## Properties

`limit`

`int32`

The number of items to return per request. For most objects, the default is `20` and the maximum is `1000`.

`offset`

`int32`

The offset pagination that limits the number of returned records. The start of each page is offset by the specified number. You can apply `offset` to most API calls, but not all GET endpoints support it. The default is `0`.

## Discussion

In the following example, the two optional parameters limit the number of campaigns that return. You specify `offset` and `limit` as query string parameters.

```
GET https://api.searchads.apple.com/api/v5/campaigns?limit=&offset=
```

## See Also

### API Usability

object Condition

The list of condition objects that allow users to filter a list of records.

object PageDetail

The number of items that return in the page.

object Selector

The selector objects available to filter returned data.

object Sorting

The order of grouped results.

