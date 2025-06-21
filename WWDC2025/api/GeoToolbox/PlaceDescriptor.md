*   [GeoToolbox](/documentation/geotoolbox)
*   PlaceDescriptor Beta

Structure

# PlaceDescriptor

A structure that contains identifying information about a place that a mapping service may use to attempt to find rich place information such as phone numbers, websites, and so on.

iOS 26.0+BetaiPadOS 26.0+BetaMac Catalyst 26.0+BetamacOS 26.0+BetatvOS 26.0+BetavisionOS 26.0+BetawatchOS 26.0+Beta

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
struct PlaceDescriptor
```
```
```
```
```
```
```
```

## [Discussion](/documentation/GeoToolbox/PlaceDescriptor#Discussion)

A [`PlaceDescriptor`](/documentation/geotoolbox/placedescriptor) allows you to construct a collection of metadata about a place, including at least one [`PlaceDescriptor.PlaceRepresentation`](/documentation/geotoolbox/placedescriptor/placerepresentation) which contains common geographic concepts like an address or coordinate. `PlaceDescriptor` may optionally include a [`supportingRepresentations`](/documentation/geotoolbox/placedescriptor/supportingrepresentations) which contains identifiers that match the place for mapping service providers. Use `PlaceDescriptor` in conjunction with a mapping service to request rich information about a place.

For example to create a [`PlaceDescriptor`](/documentation/geotoolbox/placedescriptor) that describes an address with a common name use [`init(representations:commonName:supportingRepresentations:)`](/documentation/geotoolbox/placedescriptor/init\(representations:commonname:supportingrepresentations:\)) as shown here.

```swift
    
```swift
let fountain = PlaceDescriptor(
        representations: [.address("121-122 James's St \n Dublin 8 \n D08 ET27 \n Ireland")],
        commonName: "Obelisk Fountain"
    )
```

```

You can also initialize a `PlaceDescriptor` using an [`MKMapItem`](/documentation/MapKit/MKMapItem) as shown below.

```swift
    
```swift
guard let descriptor = PlaceDescriptor(item: myMapItem) else {
        return
    }
```

```

## [Topics](/documentation/GeoToolbox/PlaceDescriptor#topics)

### [Creating place descriptors](/documentation/GeoToolbox/PlaceDescriptor#Creating-place-descriptors)

[`init(representations: [PlaceDescriptor.PlaceRepresentation], commonName: String?, supportingRepresentations: [PlaceDescriptor.SupportingPlaceRepresentation])`](/documentation/geotoolbox/placedescriptor/init\(representations:commonname:supportingrepresentations:\))

Creates a place descriptor, suitable for use when searching or retrieving rich data about a place.

[`init?(item: MKMapItem)`](/documentation/geotoolbox/placedescriptor/init\(item:\))

Creates a place descriptor from a map item.

### [Getting the attributes of a place descriptor](/documentation/GeoToolbox/PlaceDescriptor#Getting-the-attributes-of-a-place-descriptor)

```swift
```swift
```swift
```swift
let commonName: String?
```
```

Publicly known name of the area or place of interest.
```
```swift
```swift
```swift
var address: String?
```
```

A full address, that one could use in postal or administrative scenarios.
```
```swift
```swift
```swift
var coordinate: CLLocationCoordinate2D?
```
```

The latitude and longitude for a place.
```
```swift
```swift
```swift
let representations: [PlaceDescriptor.PlaceRepresentation]
```
```

An array of representations of the place using common mapping concepts.
```
```swift
```swift
```swift
let supportingRepresentations: [PlaceDescriptor.SupportingPlaceRepresentation]
```
```

An array of proprietary or non-uniform representations of the place, such as representations you can use with other mapping services.
```
```swift
```swift
```swift
func serviceIdentifier(for: String) -> String?
```
```

Retrieves the identifier for the specified service provider, if available.
```
```

### [Enumeration values that describe places and mapping service representations](/documentation/GeoToolbox/PlaceDescriptor#Enumeration-values-that-describe-places-and-mapping-service-representations)

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

### [Operators](/documentation/GeoToolbox/PlaceDescriptor#Operators)

[`static func == (PlaceDescriptor, PlaceDescriptor) -> Bool`](/documentation/geotoolbox/placedescriptor/==\(_:_:\))

Returns a Boolean value indicating whether two values are equal.

### [Initializers](/documentation/GeoToolbox/PlaceDescriptor#Initializers)

[`init(from: any Decoder) throws`](/documentation/geotoolbox/placedescriptor/init\(from:\))

Creates a new instance by decoding from the given decoder.

### [Instance Methods](/documentation/GeoToolbox/PlaceDescriptor#Instance-Methods)

```swift
```swift
```swift
```swift
func encode(to: any Encoder) throws
```
```

Encodes this value into the given encoder.
```
```

### [Type Aliases](/documentation/GeoToolbox/PlaceDescriptor#Type-Aliases)

```swift
```swift
```swift
```swift
typealias Specification
```
```
```
```swift
```swift
```swift
typealias UnwrappedType
```
```
```
```swift
```swift
```swift
typealias ValueType
```
```
```
```

### [Type Properties](/documentation/GeoToolbox/PlaceDescriptor#Type-Properties)

[`static var defaultResolverSpecification: some ResolverSpecification`](/documentation/geotoolbox/placedescriptor/defaultresolverspecification)

### [Default Implementations](/documentation/GeoToolbox/PlaceDescriptor#Default-Implementations)

[

API Reference

Equatable Implementations](/documentation/geotoolbox/placedescriptor/equatable-implementations)

[

API Reference

InstanceDisplayRepresentable Implementations](/documentation/geotoolbox/placedescriptor/instancedisplayrepresentable-implementations)

[

API Reference

PersistentlyIdentifiable Implementations](/documentation/geotoolbox/placedescriptor/persistentlyidentifiable-implementations)

[

API Reference

TypeDisplayRepresentable Implementations](/documentation/geotoolbox/placedescriptor/typedisplayrepresentable-implementations)

## [Relationships](/documentation/GeoToolbox/PlaceDescriptor#relationships)

### [Conforms To](/documentation/GeoToolbox/PlaceDescriptor#conforms-to)

*   [`Copyable`](/documentation/Swift/Copyable)
*   [`CustomLocalizedStringResourceConvertible`](/documentation/Foundation/CustomLocalizedStringResourceConvertible)
*   [`Decodable`](/documentation/Swift/Decodable)
*   [`DisplayRepresentable`](/documentation/AppIntents/DisplayRepresentable)
*   [`Encodable`](/documentation/Swift/Encodable)
*   [`Equatable`](/documentation/Swift/Equatable)
*   [`InstanceDisplayRepresentable`](/documentation/AppIntents/InstanceDisplayRepresentable)
*   [`PersistentlyIdentifiable`](/documentation/AppIntents/PersistentlyIdentifiable)
*   [`Sendable`](/documentation/Swift/Sendable)
*   [`SendableMetatype`](/documentation/Swift/SendableMetatype)
*   [`TypeDisplayRepresentable`](/documentation/AppIntents/TypeDisplayRepresentable)

Beta Software

This documentation contains preliminary information about an API or technology in development. This information is subject to change, and software implemented according to this documentation should be tested with final operating system software.

[Learn more about using Apple's beta software](https://developer.apple.com/support/beta-software/)