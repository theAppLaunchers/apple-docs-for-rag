

- Exposure Notification
- ENTemporaryExposureKey
-  transmissionRiskLevel 

Instance Property

# transmissionRiskLevel

The risk of transmission associated with the person a key came from.

iOS 12.5+iPadOS 12.5+Mac Catalyst 12.5+

``` source
var transmissionRiskLevel: ENRiskLevel { get set }
```

## Discussion

Important

This property is available in iOS 12.5, and in iOS 13.5 and later.

Each app defines its own meaning for each of the risk levels (0-7).

Consistent Transmission Risk Levels across regions facilitate roaming, therefore it’s recommended that the Transmission Risk Levels describe the type of report. The supported report types are determined by the public health authority for each region. Your app must verify the report type with a public health authority before submitting it.

Recommended report types for the different risk levels are:

- `0` = Unused/Custom

- `1` = Confirmed test: Low transmission risk level

- `2` = Confirmed test: Standard transmission risk level

- `3` = Confirmed test: High transmission risk level

- `4` = Confirmed clinical diagnosis

- `5` = Self report

- `6` = Negative case

- `7` = Recursive case

## See Also

### Exposure Criteria

var rollingPeriod: ENIntervalNumber

The length of time that this key is valid.

var keyData: Data

The temporary exposure key information.

var rollingStartNumber: ENIntervalNumber

A number that indicates when a key’s rolling period started.

typealias ENIntervalNumber

A number assigned to each 10-minute window shared between all devices participating in the protocol.

