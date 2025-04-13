

- HomeKit
-  HMCharacteristicTypeCurrentRelativeHumidity 

Global Variable

# HMCharacteristicTypeCurrentRelativeHumidity

The current relative humidity measured by the accessory.

iOS 8.0+iPadOS 8.0+Mac Catalyst 8.0+tvOS 10.0+visionOS 1.0+watchOS 2.0+

``` source
let HMCharacteristicTypeCurrentRelativeHumidity: String
```

## Discussion

The corresponding value is a floating point percentage representing the current relative humidity. This is a measure of the amount of water in the air relative to the maximum it can hold at the current temperature.

## See Also

### Humidity

let HMCharacteristicTypeTargetRelativeHumidity: String

The target relative humidity for the accessory to achieve.

let HMCharacteristicTypeCurrentHumidifierDehumidifierState: String

The current state of a humidifier or dehumidifier accessory.

let HMCharacteristicTypeTargetHumidifierDehumidifierState: String

The state that a humidifier or dehumidifier accessory should try to achieve.

let HMCharacteristicTypeHumidifierThreshold: String

The humidity below which a humidifier should begin to work.

let HMCharacteristicTypeDehumidifierThreshold: String

The humidity above which a dehumidifier should begin to work.

