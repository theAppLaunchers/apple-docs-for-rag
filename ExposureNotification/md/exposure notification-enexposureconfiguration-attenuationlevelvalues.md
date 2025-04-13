

- Exposure Notification
- ENExposureConfiguration
-  attenuationLevelValues 

Instance Property

# attenuationLevelValues

The level values for attenuation.

iOS 12.5+iPadOS 12.5+Mac Catalyst 12.5+

``` source
var attenuationLevelValues: [NSNumber] { get set }
```

## Discussion

Important

This property is available in iOS 12.5, and in iOS 13.5 and later.

This property contains eight risk-level values in the range 0-8, one for each range of attenuation.

- `attenuationLevelValues[0]` when attenuation \> 73.

- `attenuationLevelValues[1`\] when 73 \>= attenuation \> 63.

- `attenuationLevelValues[2]` when 63 \>= attenuation \> 51.

- `attenuationLevelValues[3]` when 51 \>= attenuation \> 33.

- `attenuationLevelValues[4]` when 33 \>= attenuation \> 27.

- `attenuationLevelValues[5]` when 27 \>= attenuation \> 15.

- `attenuationLevelValues[6]` when 15 \>= attenuation \> 10.

- `attenuationLevelValues[7]` when 10 \>= attenuation.

Note

On iOS 13.7 and 14.0, the framework ignores the values of this property. Instead, it uses `[1, 2, 3, 4, 5, 6, 7, 8]` for the attenuation level values.

## See Also

### Level Configuration

var attenuationDurationThresholds: [NSNumber]

The configurable signal-loss thresholds for calculating exposure risk.

var daysSinceLastExposureLevelValues: [NSNumber]

The level values for days since last exposure.

var durationLevelValues: [NSNumber]

The level values for duration.

var transmissionRiskLevelValues: [NSNumber]

The level values for transmission risk.

var metadata: [AnyHashable : Any]?

The metadata you use to configure the exposure calculations.

