

- HealthKit
- HKCorrelation
-  init(type:start:end:objects:device:metadata:) 

Initializer

# init(type:start:end:objects:device:metadata:)

Instantiates and returns a new correlation instance with the provided device and metadata.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.0+macOS 13.0+visionOS 1.0+watchOS 2.0+

``` source
convenience init(
    type correlationType: HKCorrelationType,
    start startDate: Date,
    end endDate: Date,
    objects: Set,
    device: HKDevice?,
    metadata: [String : Any]?
)
```

## Parameters 

`correlationType`  

The type for this correlation. For a complete list of correlation types, see Correlation Identifiers in HealthKit Constants.

`startDate`  

The start date for the sample. This date must be equal to or earlier than the end date; otherwise, this method throws an exception (invalidArgumentException).

`endDate`  

The end date for the sample. This date must be equal to or later than the start date; otherwise, this method throws an exception (invalidArgumentException).

`objects`  

A set of HKSample objects. Specifically, this set contains the quantity and category samples to be grouped into this correlation.

`device`  

The device that generated the data for this sample.

`metadata`  

The metadata dictionary containing extra information that describes this correlation. The dictionary’s keys are all NSString objects . The values may be NSString, NSNumber, or NSDate objects. For a complete list of predefined metadata keys, see Metadata Keys.

Using predefined keys helps facilitate sharing data between apps; however, you are also encouraged to create custom keys as needed to extend the HealthKit sample’s capabilities.

When creating correlations representing food, always use the HKMetadataKeyFoodType key to provide the food’s name.

## Return Value

A new correlation instance.

## Discussion

Use a correlation object to represent composite data—that is, a sample that requires more than a single value. To create a correlation sample, first create the quantity and category samples you intend to combine into the correlation. Next, create the correlation’s type. Finally, instantiate the correlation, passing in the type, start date, end date, samples, device, and metadata as shown below.

Use this method when recording data using external hardware. If you do not need to include additional metadata, pass `nil` for the `metadata` parameter.

- Swift
- Objective-C

```
let date = NSDate()

// Create systolic sample

guard let systolicType = HKObjectType.quantityTypeForIdentifier(HKQuantityTypeIdentifierBloodPressureSystolic) else {
    fatalError("*** Unable to create the systolic type ****")
}

let systolicQuantity =
    HKQuantity(unit: HKUnit.millimeterOfMercuryUnit(), doubleValue: 120.0)

let systolicSample = HKQuantitySample(type: systolicType,
                                      quantity: systolicQuantity, startDate: date, endDate: date)

// Create diastolic sample

guard let diastolicType = HKObjectType.quantityTypeForIdentifier(HKQuantityTypeIdentifierBloodPressureDiastolic) else {
    fatalError("*** Unable to create the diastolic type ***")
}

let diastolicQuantity =
    HKQuantity(unit: HKUnit.millimeterOfMercuryUnit(), doubleValue: 75.0)

let diastolicSample = HKQuantitySample(type: diastolicType,
                                       quantity: diastolicQuantity, startDate: date, endDate: date)

// Create blood pressure sample

guard let bloodPressureType = HKObjectType.correlationTypeForIdentifier(HKCorrelationTypeIdentifierBloodPressure) else {
    fatalError("*** Unable to create the blood pressure type ***")
}

let objects: Set = [systolicSample, diastolicSample]

let device = HKDevice(name: deviceName,
                      manufacturer: manufacturerName,
                      model: modelName,
                      hardwareVersion: hardwareVersionNumber,
                      firmwareVersion: firmwareVersionNumber,
                      softwareVersion: softwareVersionNumber,
                      localIdentifier: localIdentifier,
                      UDIDeviceIdentifier: deviceIdentifier)

let metadata : [String : AnyObject] =
    [HKMetadataKeyDigitalSignature:digitalSignature,
     HKMetadataKeyTimeZone:timeZone]

let bloodpressure = HKCorrelation(type: bloodPressureType, startDate: date, endDate: date, objects:objects, device: device, metadata: metadata)
```

```
NSDate *date = [NSDate date];

// Create systolic sample

HKQuantityType *systolicType =
[HKObjectType quantityTypeForIdentifier:
 HKQuantityTypeIdentifierBloodPressureSystolic];

HKQuantity *systolicQuantity =
[HKQuantity quantityWithUnit:[HKUnit millimeterOfMercuryUnit]
                 doubleValue:120.0];

HKQuantitySample *systolicSample =
[HKQuantitySample quantitySampleWithType:systolicType
                                quantity:systolicQuantity
                               startDate:date
                                 endDate:date];

// Create diastolic sample

HKQuantityType *diastolicType =
[HKObjectType quantityTypeForIdentifier:
 HKQuantityTypeIdentifierBloodPressureDiastolic];

HKQuantity *diastolicQuantity =
[HKQuantity quantityWithUnit:[HKUnit millimeterOfMercuryUnit]
                 doubleValue:75.0];

HKQuantitySample *diastolicSample =
[HKQuantitySample quantitySampleWithType:diastolicType
                                quantity:diastolicQuantity
                               startDate:date
                                 endDate:date];

// Create blood pressure sample

HKCorrelationType *bloodPressureType =
[HKObjectType correlationTypeForIdentifier:
 HKCorrelationTypeIdentifierBloodPressure];

NSSet *objects = [NSSet setWithObjects:systolicSample, diastolicSample, nil];

HKDevice *device = [[HKDevice alloc] initWithName:deviceName
                                     manufacturer:manufacturerName
                                            model:modelName
                                  hardwareVersion:hardwareVersionNumber
                                  firmwareVersion:firmwareVersionNumber
                                  softwareVersion:softwareVersionNumber
                                  localIdentifier:localIdentifier
                              UDIDeviceIdentifier:deviceIdentifier];

NSDictionary *metadata = @{HKMetadataKeyDigitalSignature:digitalSignature,
                           HKMetadataKeyTimeZone:timeZone};

HKCorrelation *bloodPressure =
[HKCorrelation correlationWithType:bloodPressureType
                         startDate:date
                           endDate:date
                           objects:objects
                            device:device
                          metadata:metadata];
```

## See Also

### Related Documentation

var objects: Set&lt;HKSample>

The set of sample objects that make up the correlation.

class func correlationType(forIdentifier: HKCorrelationTypeIdentifier) -> HKCorrelationType?

Returns the shared correlation type for the provided identifier.

var endDate: Date

The sample’s end date.

var correlationType: HKCorrelationType

The type for this correlation.

var metadata: [String : Any]?

The metadata for this HealthKit object.

var startDate: Date

The sample’s start date.

### Creating Correlations

convenience init(type: HKCorrelationType, start: Date, end: Date, objects: Set&lt;HKSample>)

Instantiates and returns a new correlation instance.

convenience init(type: HKCorrelationType, start: Date, end: Date, objects: Set&lt;HKSample>, metadata: [String : Any]?)

Instantiates and returns a new correlation instance with the provided metadata.

