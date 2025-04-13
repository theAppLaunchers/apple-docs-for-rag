

- MapKit
- MKAddressFilter
-  includes(\_:) 

Instance Method

# includes(\_:)

Indicates whether options are included for filtering.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+

``` source
func includes(_ options: MKAddressFilter.Options) -> Bool
```

## Parameters 

`options`  

The filters to check for inclusion.

## Return Value

Returns `true` if the passed options are included in the filtering options; otherwise, `false`.

## Discussion

A filter includes or excludes a set of filter options. Use this method to query the filter instance for one or more options.

```
let filter = MKAddressFilter(including: [.locality,  .subLocality])
let result = filter.includes(.locality)
```

The method returns `true` because `filter` includes Locality.

## See Also

### Filtering results

struct Options

A structure that contains options for filtering results in a search.

class var excludingAll: MKAddressFilter

A list of categories to exclude from a search.

class var includingAll: MKAddressFilter

A list of categories to include in a search.

func excludes(MKAddressFilter.Options) -> Bool

Indicates whether options are excluded from filtering.

