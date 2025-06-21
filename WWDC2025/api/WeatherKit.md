Framework

# WeatherKit

Deliver weather conditions and alerts to your users.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

## [Overview](/documentation/WeatherKit#overview)

WeatherKit provides timely weather information including current conditions, minute precipitation, along with hourly, and daily forecasts. It also provides severe weather alerts.

## [Topics](/documentation/WeatherKit#topics)

### [Fundamentals](/documentation/WeatherKit#Fundamentals)

[

Fetching weather forecasts with WeatherKit](/documentation/weatherkit/fetching_weather_forecasts_with_weatherkit)

Request and display weather data for destination airports in a flight-planning app.

```swift
```swift
```swift
struct Weather
```
```

A model representing the aggregate weather data the caller requests.
```
```swift
```swift
```swift
class WeatherService
```
```

Provides an interface for obtaining weather data.
```

### [Requests](/documentation/WeatherKit#Requests)

```swift
```swift
```swift
```swift
struct WeatherQuery
```
```

A structure that encapsulates a generic weather dataset request.
```
```swift
```swift
```swift
struct CurrentWeather
```
```

A structure that describes the current conditions observed at a location.
```
```swift
```swift
```swift
struct WeatherAttribution
```
```

A structure that defines the necessary information for attributing a weather data provider.
```
```swift
```swift
```swift
struct WeatherMetadata
```
```

A structure that provides additional weather information.
```
```swift
```swift
```swift
enum WeatherSeverity
```
```

A description of the severity of the severe weather event.
```
```

### [Characteristics](/documentation/WeatherKit#Characteristics)

```swift
```swift
```swift
```swift
enum Precipitation
```
```

The form of precipitation.
```
```swift
```swift
```swift
enum PressureTrend
```
```

The atmospheric pressure change over time.
```
```swift
```swift
```swift
struct UVIndex
```
```

The expected intensity of ultraviolet radiation from the sun.
```
```swift
```swift
```swift
struct Wind
```
```

Contains wind data of speed, direction, and gust.
```
```swift
```swift
```swift
enum WeatherCondition
```
```

A description of the current weather condition.
```
```

### [Alerts and forecasts](/documentation/WeatherKit#Alerts-and-forecasts)

```swift
```swift
```swift
```swift
struct WeatherAlert
```
```

A weather alert issued for the requested location by a governmental authority.
```
```swift
```swift
```swift
struct WeatherAvailability
```
```

A structure that indicates the availability of data at the requested location.
```
```swift
```swift
```swift
struct Forecast
```
```

A forecast collection for minute, hourly, and daily forecasts.
```
```swift
```swift
```swift
struct MinuteWeather
```
```

A structure that represents the next hour minute forecasts.
```
```swift
```swift
```swift
struct HourWeather
```
```

A structure that represents the weather conditions for the hour.
```
```swift
```swift
```swift
struct DayWeather
```
```

A structure that represents the weather conditions for the day.
```
```

### [Celestial information](/documentation/WeatherKit#Celestial-information)

```swift
```swift
```swift
```swift
struct SunEvents
```
```

An enumeration that represents dates of solar events, including sunrise, sunset, dawn, and dusk.
```
```swift
```swift
```swift
struct MoonEvents
```
```

A structure that represents lunar events.
```
```swift
```swift
```swift
enum MoonPhase
```
```

An enumeration that specifies the moon phase kind.
```
```

### [Errors](/documentation/WeatherKit#Errors)

```swift
```swift
```swift
```swift
enum WeatherError
```
```

An error WeatherKit returns.
```
```

### [Structures](/documentation/WeatherKit#Structures)

```swift
```swift
```swift
```swift
struct CloudCoverByAltitude
```
```

Contains the percentage of sky covered by low, medium and high altitude cloud.
```
```swift
```swift
```swift
struct DailyWeatherStatistics
```
```

A structure that holds a collection of day weather statistics data.
```
```swift
```swift
```swift
struct DailyWeatherStatisticsQuery
```
```

A structure that encapsulates a generic daily weather statistics dataset request.
```
```swift
```swift
```swift
struct DailyWeatherSummary
```
```

A structure that holds a collection of day weather summaries.
```
```swift
```swift
```swift
struct DailyWeatherSummaryQuery
```
```

A structure that encapsulates a generic daily weather summary dataset request.
```
```swift
```swift
```swift
struct DayPartForecast
```
```

A structure that represents the weather forecast for part of the day.
```
```swift
```swift
```swift
struct DayPrecipitationStatistics
```
```

A structure that describes precipitation statistics for a day.
```
```swift
```swift
```swift
struct DayPrecipitationSummary
```
```

A structure that describes the precipitation summary for a day.
```
```swift
```swift
```swift
struct DayTemperatureStatistics
```
```

A structure that describes temperature statistics for a day.
```
```swift
```swift
```swift
struct DayTemperatureSummary
```
```

A structure that describes the temperature summary for a day.
```
```swift
```swift
```swift
struct HistoricalComparisons
```
```

A structure that represents the weather condition comparisons for a specific location. It’s a list of comparisons between current readings and historical averages. The list is ordered by significance of deviation.
```
```swift
```swift
```swift
struct HourTemperatureStatistics
```
```

A structure that describes temperature statistics for a specific hour.
```
```swift
```swift
```swift
struct HourlyWeatherStatistics
```
```

A structure that holds a collection of hour weather statistics data.
```
```swift
```swift
```swift
struct HourlyWeatherStatisticsQuery
```
```

A structure that encapsulates a generic hourly weather statistics dataset request.
```
```swift
```swift
```swift
struct MonthPrecipitationStatistics
```
```

A structure that describes precipitation statistics for a specific month.
```
```swift
```swift
```swift
struct MonthTemperatureStatistics
```
```

A structure that describes temperature statistics for a specific month.
```
```swift
```swift
```swift
struct MonthlyWeatherStatistics
```
```

A structure that holds a collection of month weather statistics data.
```
```swift
```swift
```swift
struct MonthlyWeatherStatisticsQuery
```
```

A structure that encapsulates a generic monthly weather statistics dataset request.
```
```swift
```swift
```swift
struct Percentiles
```
```

A structure that describes probability distributions for a measurable weather condition.
```
```swift
```swift
```swift
struct PrecipitationAmountByType
```
```

A structure that provides a breakdown of amounts of all forms of precipitation that is expected to occur over a period of time.
```
```swift
```swift
```swift
struct SnowfallAmount
```
```

A structure that describes the snowfall amount over a period of time.
```
```swift
```swift
```swift
struct Trend
```
```

A structure describing an observed pattern in the data for weather at a location for a specific condition.
```
```swift
```swift
```swift
struct TrendBaseline
```
```

A type encapsulating everything there is to know about what a trend baseline is.
```
```swift
```swift
```swift
struct WeatherChange
```
```

A structure that informs how certain measurable weather aspects are expected to change relative to before.
```
```swift
```swift
```swift
struct WeatherChanges
```
```

A structure that represents the Weather Change forecast. It provides a qualitative assessment of whether upcoming weather is significantly different from prior conditions.
```
```

### [Enumerations](/documentation/WeatherKit#Enumerations)

```swift
```swift
```swift
```swift
enum Deviation
```
```

Describes a comparison between two values in a trend.
```
```swift
```swift
```swift
enum HistoricalComparison
```
```

An enum that represents a recognized comparison in the statistical analysis of a location’s historical weather data.
```
```