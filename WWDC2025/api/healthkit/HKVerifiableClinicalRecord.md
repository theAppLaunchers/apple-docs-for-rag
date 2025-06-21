*   [HealthKit](/documentation/healthkit)
*   HKVerifiableClinicalRecord

Class

# HKVerifiableClinicalRecord

A sample that represents the contents of a SMART Health Card or EU Digital COVID Certificate.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 13.0+visionOS 1.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
class HKVerifiableClinicalRecord
```
```
```
```
```
```
```
```

## [Overview](/documentation/HealthKit/HKVerifiableClinicalRecord#overview)

[`HKVerifiableClinicalRecord`](/documentation/healthkit/hkverifiableclinicalrecord) samples contain data from a SMART Health Card or EU Digital COVID Certificate. Verifiable clinical records combine information about the user’s identity with clinical data, like an immunization record or a lab test result. The organization that produced the data cryptographically signs the bundle.

Apps that use verifiable clinical records can use the cryptographic signature to verify the authenticity of the contents. To verify the card:

1.  Access the card’s raw payload using the clinical record’s [`dataRepresentation`](/documentation/healthkit/hkverifiableclinicalrecord/datarepresentation) property.
    
2.  Unzip the payload and parse out the `iss` value, which contains a URL that identifies the organization that issued the card.
    
3.  Get the public key from the issuer.
    
4.  Verify the payload’s signature.
    

For more information, see [SMART Health Cards Framework](https://smarthealth.cards) and [Electronic Health Certificates](https://github.com/ehn-dcc-development/hcert-spec). You can download example SMART cards for testing and development from [Examples](https://smarthealth.cards/examples/).

## [Topics](/documentation/HealthKit/HKVerifiableClinicalRecord#topics)

### [Identifying the Subject](/documentation/HealthKit/HKVerifiableClinicalRecord#Identifying-the-Subject)

```swift
```swift
```swift
```swift
var subject: HKVerifiableClinicalRecordSubject
```
```

Data about the person whose clinical data the card contains.
```
```

### [Identifying the Issuer](/documentation/HealthKit/HKVerifiableClinicalRecord#Identifying-the-Issuer)

```swift
```swift
```swift
```swift
var issuerIdentifier: String
```
```

An identifier that represents the card’s issuer.
```
```

### [Reading Metadata](/documentation/HealthKit/HKVerifiableClinicalRecord#Reading-Metadata)

```swift
```swift
```swift
```swift
var issuedDate: Date
```
```

The date when the issuer created the card.
```
```swift
```swift
```swift
var relevantDate: Date
```
```

A date relevant to this record, such as when the issuer administered a vaccine or performed a test.
```
```swift
```swift
```swift
var expirationDate: Date?
```
```

The date when the card expires.
```
```swift
```swift
```swift
var recordTypes: [String]
```
```

An array of strings representing the types of records contained in the card.
```
```swift
```swift
```swift
var sourceType: HKVerifiableClinicalRecordSourceType?
```
```

The source for the verifiable clinical record
```
```swift
```swift
```swift
struct HKVerifiableClinicalRecordSourceType
```
```

The source type for the verifiable clinical record.
```
```swift
```swift
```swift
var itemNames: [String]
```
```

A human-readable description of the card’s contents.
```
```

### [Accessing the Raw Payload](/documentation/HealthKit/HKVerifiableClinicalRecord#Accessing-the-Raw-Payload)

```swift
```swift
```swift
```swift
var dataRepresentation: Data
```
```

A raw representation of the record’s data.
```
```swift
```swift
```swift
var jwsRepresentation: Data
```
```

A raw representation of the SMART Health Card’s contents.

Deprecated
```
```

## [Relationships](/documentation/HealthKit/HKVerifiableClinicalRecord#relationships)

### [Inherits From](/documentation/HealthKit/HKVerifiableClinicalRecord#inherits-from)

*   [`HKSample`](/documentation/healthkit/hksample)

### [Conforms To](/documentation/HealthKit/HKVerifiableClinicalRecord#conforms-to)

*   [`CVarArg`](/documentation/Swift/CVarArg)
*   [`CustomDebugStringConvertible`](/documentation/Swift/CustomDebugStringConvertible)
*   [`CustomStringConvertible`](/documentation/Swift/CustomStringConvertible)
*   [`Equatable`](/documentation/Swift/Equatable)
*   [`Hashable`](/documentation/Swift/Hashable)
*   [`NSCoding`](/documentation/Foundation/NSCoding)
*   [`NSObjectProtocol`](/documentation/ObjectiveC/NSObjectProtocol)
*   [`NSSecureCoding`](/documentation/Foundation/NSSecureCoding)
*   [`Sendable`](/documentation/Swift/Sendable)
*   [`SendableMetatype`](/documentation/Swift/SendableMetatype)

## [See Also](/documentation/HealthKit/HKVerifiableClinicalRecord#see-also)

### [Medical records](/documentation/HealthKit/HKVerifiableClinicalRecord#Medical-records)

[

Accessing Health Records](/documentation/healthkit/accessing-health-records)

Read clinical record data from the HealthKit store.

[

Accessing Sample Data in the Simulator](/documentation/healthkit/accessing-sample-data-in-the-simulator)

Set up sample accounts to build and test your app.

[

Accessing a User’s Clinical Records](/documentation/healthkit/accessing-a-user-s-clinical-records)

Request authorization to query HealthKit for a user’s clinical records and display them in your app.

[

Accessing Data from a SMART Health Card](/documentation/healthkit/accessing-data-from-a-smart-health-card)

Query for and validate a verifiable clinical record.

```swift
```swift
```swift
class HKClinicalRecord
```
```

A sample that stores a clinical record.
```
```swift
```swift
```swift
class HKFHIRResource
```
```

An object containing Fast Healthcare Interoperability Resources (FHIR) data.
```
```swift
```swift
```swift
class HKVerifiableClinicalRecordSubject
```
```

The subject associated with a signed clinical record.
```
```swift
```swift
```swift
class HKCDADocumentSample
```
```

A Clinical Document Architecture (CDA) sample that stores a single document.
```
```swift
```swift
```swift
class HKDocumentSample
```
```

An abstract class that represents a health document in the HealthKit store.
```

[`static let CDA: HKDocumentTypeIdentifier`](/documentation/healthkit/hkdocumenttypeidentifier/cda)

The CDA Document type identifier, used when requesting permission to read or share CDA documents.

```swift
```swift
```swift
class HKDocumentType
```
```

A sample type used to create queries for documents.
```