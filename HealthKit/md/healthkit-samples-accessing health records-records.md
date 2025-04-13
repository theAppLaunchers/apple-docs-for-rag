

- HealthKit
- Samples
-  Accessing Health Records 

Article

# Accessing Health Records

Read clinical record data from the HealthKit store.

## Overview

Use HealthKit’s clinical record support to read Fast Healthcare Interoperability Resources (FHIR) from the HealthKit store. Users can download their FHIR records from supported healthcare institutions. The system then updates the records in the background on a regular basis.

Instead of focusing on documents, FHIR breaks the user’s medical history into discrete records. HealthKit then represents each FHIR record as an HKClinicalRecord sample that stores a single condition, procedure, or result.

To use clinical records, you must request permission to read each record type. Then, use HealthKit’s queries to access the individual records. Finally, you need to parse and handle each record’s FHIR JSON data.

Xcode’s simulator provides sample accounts you can use when building and testing your app. For more information, see Accessing Sample Data in the Simulator.

### Set Up HealthKit

Due to their sensitive nature, clinical records have additional setup requirements. First, when you enable your app’s HealthKit capabilities, you must also select the Clinical Health Records checkbox.

Next, you must provide a Health Records Usage string for your app. Use this string to describe what your app does with the user’s records, and why it’s important for the user to share this data.

For projects created using Xcode 13 or later, set the usage key in the Target Properties list on the app’s Info tab. For projects created with Xcode 12 or earlier, set it in the apps `Info.plist` file. For more information, see Information Property List.

You request authorization to read clinical records using the HKClinicalTypeIdentifier enumeration. This enumeration specifies the types of FHIR data supported by HealthKit. You must request permission to read all the types that your app intends to use. Additionally, clinical records are read-only, so you can’t request authorization to share clinical record types. You can’t create or save new HKClinicalRecord objects.

```
guard let allergiesType = HKObjectType.clinicalType(forIdentifier: .allergyRecord),
let medicationsType = HKObjectType.clinicalType(forIdentifier: .medicationRecord) else {
    fatalError("*** Unable to create the requested types ***")
}

// Clinical types are read-only.
store.requestAuthorization(toShare: nil, read: [allergiesType, medicationsType]) { (success, error) in

    guard success else {
        // Handle errors here.
        fatalError("*** An error occurred while requesting authorization: \(error!.localizedDescription) ***")
    }

    // You can start accessing clinical record data.
}
```

You can request authorization of clinical record types and regular HealthKit types in the same method call; however, HealthKit presents the clinical record types in a separate permission sheet to ensure the user understands exactly what they’re approving.

Note

Like all HealthKit apps, apps that read clinical record data must have a valid Privacy Policy URL in the app store submission. This URL appears as a link on the clinical record permission sheet. Make sure the URL works as expected, and is both accessible and legible on supported iOS devices.

App Review may reject apps that don’t use clinical record data appropriately. For more information, see the Health and Health Research section of the App Store Review Guidelines.

### Query for Health Records

You can use HealthKit’s regular queries to look up clinical records.

```
// Get all the allergy records.
guard let allergyType = HKObjectType.clinicalType(forIdentifier: .allergyRecord) else {
    fatalError("*** Unable to create the allergy type ***")
}

let allergyQuery = HKSampleQuery(sampleType: allergyType, predicate: nil, limit: HKObjectQueryNoLimit, sortDescriptors: nil) { (query, samples, error) in

    guard let actualSamples = samples else {
        // Handle the error here.
        print("*** An error occurred: \(error?.localizedDescription ?? "nil") ***")
        return
    }

    let allergySamples = actualSamples as? [HKClinicalRecord]
    // Do something with the allergy samples here...
}

store.execute(allergyQuery)
```

Each query returns a single clinical record type. HealthKit also provides two predicates to further refine your queries:

predicateForClinicalRecords(from:fhirResourceType:identifier:)  
Search for a particular FHIR record. Note that the system only guarantees that the FHIR identifier is unique for a particular resource type from a given source. To identify a record uniquely, you must check the identifier, type, and source.

predicateForClinicalRecords(withFHIRResourceType:)  
Search for a specific FHIR resource type. In most cases, there’s a one-to-one correspondence between the clinical record types and the FHIR resource types; therefore, most queries already return samples from a single FHIR resource type. However, queries for the medicationRecord type can return records from the medicationOrder, medicationRequest, medicationDispense, and medicationStatement FHIR resource types. You can use this predicate to limit your query to one of these FHIR types.

### Examine FHIR Data

Once you have an HKClinicalRecord sample, you can access the FHIR data through its fhirResource property. The HKFHIRResource object represents the underlying data from the user’s health care institution. While the resource object provides properties to access a few, useful attributes (identifier, resourceType, and sourceURL), use the data property to access the underlying JSON, which contains the complete clinical data.

```
guard let fhirRecord = clinicalRecord.fhirResource else {
    print("No FHIR record found!")
    return
}

do {
    let jsonDictionary = try JSONSerialization.jsonObject(with: fhirRecord.data, options: [])

    // Do something with the JSON data here.
}
catch let error {
    print("*** An error occurred while parsing the FHIR data: \(error.localizedDescription) ***")
    // Handle JSON parse errors here.
}
```

The HKFHIRResource object’s resourceType property contains a HKFHIRResourceType value. While the HKFHIRResourceType enumeration is similar to the HKClinicalTypeIdentifier values, there isn’t a one-to-one relationship between them.

For example, HealthKit splits the observation type into the labResultRecord and vitalSignRecord identifiers. As a result, you must query for lab results and vital signs separately.

Similarly, a medicationRecord identifier matches medicationStatement, medicationOrder, medicationRequest, and medicationDispense types. Therefore—unless you use the predicateForClinicalRecords(withFHIRResourceType:) predicate—when you query for medication, you can get a mixture of statement, order, request, and dispense records.

The following sample shows JSON data for an FHIR Condition resource:

```
{
    "asserter": {
        "display": "Juan Chavez",
        "reference": "Practitioner/20"
    },
    "category": {
        "coding": [
            {
                "code": "diagnosis",
                "system": "http://hl7.org/fhir/condition-category"
            }
        ]
    },
    "clinicalStatus": "active",
    "code": {
        "coding": [
            {
                "code": "367498001",
                "display": "Seasonal allergic rhinitis",
                "system": "http://snomed.info/sct"
            }
        ],
        "text": "Seasonal Allergic Rhinitis"
    },
    "dateRecorded": "2012-01-02",
    "id": "2",
    "notes": "Worse when visiting family in NC during the spring",
    "onsetDateTime": "1994-05-12",
    "resourceType": "Condition",
    "verificationStatus": "confirmed"
}
```

Juan Chavez recorded this resource in 2012. It describes seasonal allergic rhinitis (SNOMED code 367498001), with an onset date of May 12, 1994.

The FHIR data contains a considerable amount of additional information; however, to access this data you need to understand the FHIR specification.

For more information, see the following websites:

- Argonaut Data Query Implementation Guide 1.0.0

- FHIR specification (DSTU2, 1.0.2)

- FHIR Foundation

## See Also

### Medical records

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

class HKCDADocumentSample

A Clinical Document Architecture (CDA) sample that stores a single document.

class HKDocumentSample

An abstract class that represents a health document in the HealthKit store.

static let CDA: HKDocumentTypeIdentifier

The CDA Document type identifier, used when requesting permission to read or share CDA documents.

class HKDocumentType

A sample type used to create queries for documents.

