

- Core Location
- CLGeocoder
-  geocodeAddressString(\_:in:completionHandler:) 

Instance Method

# geocodeAddressString(\_:in:completionHandler:)

Submits a forward-geocoding request using the specified string and region information.

iOS 5.0+iPadOS 5.0+Mac Catalyst 13.1+macOS 10.8+tvOS 9.0+watchOS 2.0+

``` source
func geocodeAddressString(
    _ addressString: String,
    in region: CLRegion?,
    completionHandler: @escaping CLGeocodeCompletionHandler
)
```

``` source
func geocodeAddressString(
    _ addressString: String,
    in region: CLRegion?
) async throws -> [CLPlacemark]
```

## Parameters 

`addressString`  

A string describing the location you want to look up. For example, you could specify the string “1 Infinite Loop, Cupertino, CA” to locate Apple headquarters.

`region`  

A geographical region to use as a hint when looking up the specified address. Specifying a region lets you prioritize the returned set of results to locations that are close to some specific geographical area, which is typically the user’s current location. If the application is authorized for location services and you specify `nil` for this parameter, the set of results is prioritized based on the user’s approximate location. Calling this method does not trigger a location services authorization request.

`completionHandler`  

The handler block to execute with the results. The geocoder executes this handler regardless of whether the request was successful or unsuccessful. For more information on the format of this block, see CLGeocodeCompletionHandler.

## Discussion

Important

You can call this method from synchronous code using a completion handler, as shown on this page, or you can call it as an asynchronous method that has the following declaration:

```
func geocodeAddressString(_ addressString: String, in region: CLRegion?) async throws -> [CLPlacemark]
```

For information about concurrency and asynchronous code in Swift, see Calling Objective-C APIs Asynchronously.

This method submits the specified location data to the geocoding server asynchronously and returns. Your completion handler block will be executed on the main thread.

After initiating a forward-geocoding request, do not attempt to initiate another forward- or reverse-geocoding request. Geocoding requests are rate-limited for each app, so making too many requests in a short period of time may cause some of the requests to fail. When the maximum rate is exceeded, the geocoder passes an error object with the value CLError.Code.network to your completion handler.

## See Also

### Geocoding an address

func geocodeAddressString(String, in: CLRegion?, preferredLocale: Locale?, completionHandler: CLGeocodeCompletionHandler)

Submits a forward-geocoding requesting using the specified address string and locale information.

func geocodeAddressString(String, completionHandler: CLGeocodeCompletionHandler)

Submits a forward-geocoding request using the specified string.

func geocodePostalAddress(CNPostalAddress, completionHandler: CLGeocodeCompletionHandler)

Submits a forward-geocoding requesting using the specified Contacts framework information.

func geocodePostalAddress(CNPostalAddress, preferredLocale: Locale?, completionHandler: CLGeocodeCompletionHandler)

Submits a forward-geocoding requesting using the specified locale and Contacts framework information.

func geocodeAddressDictionary([AnyHashable : Any], completionHandler: CLGeocodeCompletionHandler)

Submits a forward-geocoding request using the specified address dictionary.

Deprecated

