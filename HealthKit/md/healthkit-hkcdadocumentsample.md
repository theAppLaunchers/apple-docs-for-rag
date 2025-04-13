

- HealthKit
-  HKCDADocumentSample 

Class

# HKCDADocumentSample

A Clinical Document Architecture (CDA) sample that stores a single document.

iOS 10.0+iPadOS 10.0+Mac Catalyst 13.0+macOS 13.0+visionOS 1.0+

``` source
class HKCDADocumentSample
```

## Overview

The sample’s `document` property contains an HKCDADocument object, representing the underlying XML document.

The HKCDADocumentSample class is a concrete subclass of the HKDocumentSample class. Document samples are immutable. HealthKit assigns the document’s properties when the sample is created. They cannot change. If you need to update a document in HealthKit, create a new document sample with the updated CDA document.

## Topics

### Creating CDA Samples

convenience init(data: Data, start: Date, end: Date, metadata: [String : Any]?) throws

Returns a CDA document sample containing the provided XML document and metadata.

let HKDetailedCDAValidationErrorKey: String

A key for accessing validation error information from an error object’s user information dictionary.

### Accessing the Document

var document: HKCDADocument?

The CDA document.

class HKCDADocument

An object representing a Clinical Document Architecture (CDA) document in HealthKit.

### Accessing Validation Errors

let HKDetailedCDAValidationErrorKey: String

A key for accessing validation error information from an error object’s user information dictionary.

### Specifying Predicate Key Paths

let HKPredicateKeyPathCDAAuthorName: String

The key path for accessing the author’s name inside a predicate format string.

let HKPredicateKeyPathCDACustodianName: String

The key path for accessing the custodian’s name inside a predicate format string.

let HKPredicateKeyPathCDAPatientName: String

The key path for accessing the patient’s name inside a predicate format string.

let HKPredicateKeyPathCDATitle: String

The key path for accessing the document’s title inside a predicate format string.

## Relationships

### Inherits From

- HKDocumentSample

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSCoding
- NSObjectProtocol
- NSSecureCoding
- Sendable

## See Also

### Medical records

Accessing Health Records

Read clinical record data from the HealthKit store.

Accessing Sample Data in the Simulator

Set up sample accounts to build and test your app.

Accessing a User’s Clinical Records

Request authorization to query HealthKit for a user’s clinical records and display them in your app.

Accessing Data from a SMART Health Card

Query for and validate a verifiable clinical record.

class HKClinicalRecord

A sample that stores a clinical record.

class HKFHIRResource

An object containing Fast Healthcare Interoperability Resources (FHIR) data.

class HKVerifiableClinicalRecord

A sample that represents the contents of a SMART Health Card or EU Digital COVID Certificate.

class HKVerifiableClinicalRecordSubject

The subject associated with a signed clinical record.

class HKDocumentSample

An abstract class that represents a health document in the HealthKit store.

static let CDA: HKDocumentTypeIdentifier

The CDA Document type identifier, used when requesting permission to read or share CDA documents.

class HKDocumentType

A sample type used to create queries for documents.

