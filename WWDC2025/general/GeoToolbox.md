Framework

# GeoToolbox

Determine place descriptor information for map coordinates.

iOS 26.0+BetaiPadOS 26.0+BetaMac Catalyst 26.0+BetamacOS 26.0+BetatvOS 26.0+BetavisionOS 26.0+BetawatchOS 26.0+Beta

## [Overview](/documentation/GeoToolbox#overview)

Use `GeoToolbox` to create `PlaceDescriptor` structures for use across Maps technologies and third-party mapping systems.

## [Topics](/documentation/GeoToolbox#topics)

### [Getting rich information about a place](/documentation/GeoToolbox#Getting-rich-information-about-a-place)

```swift
```swift
```swift
```swift
struct PlaceDescriptor
```
```

A structure that contains identifying information about a place that a mapping service may use to attempt to find rich place information such as phone numbers, websites, and so on.
```
```

### [Creating a place descriptor](/documentation/GeoToolbox#Creating-a-place-descriptor)

[`init?(item: MKMapItem)`](/documentation/geotoolbox/placedescriptor/init\(item:\))

Creates a place descriptor from a map item.

[`init(representations: [PlaceDescriptor.PlaceRepresentation], commonName: String?, supportingRepresentations: [PlaceDescriptor.SupportingPlaceRepresentation])`](/documentation/geotoolbox/placedescriptor/init\(representations:commonname:supportingrepresentations:\))

Creates a place descriptor, suitable for use when searching or retrieving rich data about a place.

### [Values that describe places and mapping service providers](/documentation/GeoToolbox#Values-that-describe-places-and-mapping-service-providers)

```swift
```swift
```swift
```swift
enum PlaceRepresentation
```
```

Values that represent a physical place, suitable for use when searching or retrieving rich data.
```
```swift
```swift
```swift
enum SupportingPlaceRepresentation
```
```

Values that describe the representation of a physical place using proprietary attributes, such as an alphanumeric location identifier from a mapping service provider.
```
```

Beta Software

This documentation contains preliminary information about an API or technology in development. This information is subject to change, and software implemented according to this documentation should be tested with final operating system software.

[Learn more about using Apple's beta software](https://developer.apple.com/support/beta-software/)