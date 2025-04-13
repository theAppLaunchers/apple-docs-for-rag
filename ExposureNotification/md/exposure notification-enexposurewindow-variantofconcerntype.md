

- Exposure Notification
- ENExposureWindow
-  variantOfConcernType 

Instance Property

# variantOfConcernType

The variant of concern associated with this user.

iOS 15.2+iPadOS 15.2+Mac Catalyst 15.2+

``` source
var variantOfConcernType: ENVariantOfConcernType { get }
```

## Discussion

The Public Health Authority (PHA) has control over defining the meaning of the types that indicate variants of concern.

## See Also

### Getting Window Properties

var calibrationConfidence: ENCalibrationConfidence

The transmitting device’s calibration confidence.

var date: Date

The date that the exposure occurred.

var diagnosisReportType: ENDiagnosisReportType

The report type of the observed diagnosis.

var infectiousness: ENInfectiousness

How infectious the user is, based on the number of days since the onset of symptoms.

var scanInstances: [ENScanInstance]

An array of scans corresponding to a beacon associated with an exposure.

enum ENVariantOfConcernType

A set of user-definable types that indicate variants of concern.

