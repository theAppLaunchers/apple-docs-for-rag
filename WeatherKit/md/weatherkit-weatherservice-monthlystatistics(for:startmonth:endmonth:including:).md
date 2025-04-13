

- WeatherKit
- WeatherService
-  monthlyStatistics(for:startMonth:endMonth:including:) 

Instance Method

# monthlyStatistics(for:startMonth:endMonth:including:)

Returns monthly weather statistics for the requested location, for each month from the start month to the end month, inclusively.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+watchOS 11.0+

``` source
final func monthlyStatistics(
    for location: CLLocation,
    startMonth: Int,
    endMonth: Int,
    including dataSets: repeat MonthlyWeatherStatisticsQuery
) async throws -> (repeat MonthlyWeatherStatistics) where repeat each T : Decodable, repeat each T : Encodable, repeat each T : Equatable, repeat each T : Sendable
```

## Parameters 

`location`  

The requested location.

`startMonth`  

The first month of the span, between 1 and 12.

`endMonth`  

The last month of the span, between 1 and 12.

## Return Value

The requested monthly weather statistics.

## Discussion

Throws

Weather data error `WeatherError`

The statistics returned for each month are derived from weather data recorded over the past decades, to the present date. Each item returned represents statistics for a particular Gregorian Calendar month of the year.

This is a variadic API in which any combination of data sets can be requested and returned as a tuple. The following example will return statistics for all months of the year.

```
let (monthlyPrecipitationStatistics, monthlyTemperatureStatistics) = try await service.monthlyStatistics(for: newYork, startMonth: 1, endMonth: 12, including: .precipitation, .temperature)
```

If `start` comes after `end` in the year, then a wrap around will occur. This next example will return statistics for months 11, 12, 1, and 2.

```
let (monthlyPrecipitationStatistics, monthlyTemperatureStatistics) = try await service.monthlyStatistics(for: newYork, startMonth: 11, endMonth: 2, including: .precipitation, .temperature)
```

Precondition

`startMonth in 1...12 && endMonth in 1...12`

