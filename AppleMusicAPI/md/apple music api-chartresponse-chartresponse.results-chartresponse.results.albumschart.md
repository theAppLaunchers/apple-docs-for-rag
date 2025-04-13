

- Apple Music API
- ChartResponse
- ChartResponse.Results
-  ChartResponse.Results.AlbumsChart 

Object

# ChartResponse.Results.AlbumsChart

The albums results of a chart.

Apple Music 1.0+

``` source
object ChartResponse.Results.AlbumsChart
```

## Properties

`chart`

`string`

 (Required) 

The unique name of the chart to use when fetching a specific chart.

`data`

`[`Albums`]`

 (Required) 

The popularity-ordered albums for the chart.

`href`

`string`

A relative location to fetch the chart results directly.

`name`

`string`

 (Required) 

The localized display name for the chart.

`next`

`string`

A relative cursor to fetch the next paginated results for the chart if more exist.

## See Also

### Related Objects

object ChartResponse.Results.MusicVideosChart

The music videos results of a chart.

object ChartResponse.Results.PlaylistsChart

The playlists results of a chart.

object ChartResponse.Results.SongsChart

The songs results of a chart.

