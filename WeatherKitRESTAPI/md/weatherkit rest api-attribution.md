

- WeatherKit REST API
-  Attribution 

Object

# Attribution

A list of image asset URLs for attribution.

Weather API 1.0.0+

``` source
object Attribution
```

## Properties

`logoDark@1x`

`string`

The partial URL of the dark appearance of the Apple Weather logo with a scale factor of 1, or @1x.

`logoDark@2x`

`string`

The partial URL of the dark appearance of the Apple Weather logo with a scale factor of 2, or @2x.

`logoDark@3x`

`string`

The partial URL of the dark appearance of the Apple Weather logo with a scale factor of 3, or @3x.

`logoLight@1x`

`string`

The partial URL of the light appearance of the Apple Weather logo with a scale factor of 1, or @1x.

`logoLight@2x`

`string`

The partial URL of the light appearance of the Apple Weather logo with a scale factor of 2, or @2x.

`logoLight@3x`

`string`

The partial URL of the light appearance of the Apple Weather logo with a scale factor of 3, or @3x.

`logoSquare@1x`

`string`

The partial URL of a square weather logo with a scale factor of 1, or @1x.

`logoSquare@2x`

`string`

The partial URL of a square weather logo with a scale factor of 2, or @2x.

`logoSquare@3x`

`string`

The partial URL of a square weather logo with a scale factor of 3, or @3x.

`serviceName`

`string`

The name of the service.

## Attributes 

Possible types:

## Discussion

Attribution URLs of image assets are partial. Append the partial URL to `https://weatherkit.apple.com` to obtain the image asset.

## See Also

### Performing attribution

GET /attribution/{language}

Receive attribution information.

