

- Foundation
- NSValue
-  init(CMTimeMapping:) 

Initializer

# init(CMTimeMapping:)

Creates a new value object containing the specified CoreMedia time mapping structure.

iOS 4.0+iPadOS 4.0+Mac Catalyst 13.1+macOS 10.7+tvOS 9.0+visionOS 1.0+watchOS 1.0+

``` source
init(CMTimeMapping timeMapping: CMTimeMapping)
```

``` source
init(timeMapping: CMTimeMapping)
```

## Parameters 

`timeMapping`  

The value for the new object.

## Return Value

A new value object that contains the time mapping information.

## See Also

### Related Documentation

struct CMTimeMapping

A structure that maps a segment of a source time range to a target time range.

### Working with Media Time Values

init(CMTime: CMTime)

Creates a new value object containing the specified CoreMedia time structure.

init(CMTimeRange: CMTimeRange)

Creates a new value object containing the specified CoreMedia time range structure.

var timeValue: CMTime

The CoreMedia time structure representation of the value.

var timeRangeValue: CMTimeRange

The CoreMedia time range structure representation of the value.

var timeMappingValue: CMTimeMapping

The CoreMedia time mapping structure representation of the value.

