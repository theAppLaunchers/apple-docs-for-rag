

- WeatherKit
- WeatherService
-  dailyStatistics(for:forDaysIn:including:) 

Instance Method

# dailyStatistics(for:forDaysIn:including:)

Returns daily weather statistics for the requested location, for each day within the specified date interval.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+watchOS 11.0+

``` source
final func dailyStatistics(
    for location: CLLocation,
    forDaysIn interval: DateInterval,
    including dataSets: repeat DailyWeatherStatisticsQuery
) async throws -> (repeat DailyWeatherStatistics) where repeat each T : Decodable, repeat each T : Encodable, repeat each T : Equatable, repeat each T : Sendable
```

## Parameters 

`location`  

The requested location.

`interval`  

The date interval for which to obtain daily weather statistics. The end date of the interval will be capped at 1 year after the start date.

## Return Value

The requested daily weather statistics.

## Discussion

Throws

Weather data error `WeatherError`

The statistics returned for each day are derived from weather data recorded over the past decades, to the present date. Each item returned represents statistics for a particular day of the year, in UTC. For example, if December 31, UTC time, is within the span, the statistics returned for that particular day will be taken from data recorded over the years for day 365 of the year, or 366 if December 31 of the span falls on a leap year.

This is a variadic API in which any combination of data sets can be requested and returned as a tuple. Here’s an example:

```
let (dailyPrecipitationStatistics, dailyTemperatureStatistics) = try await service.dailyStatistics(for: newYork, forDaysIn: timeInterval, including: .precipitation, .temperature)
```

