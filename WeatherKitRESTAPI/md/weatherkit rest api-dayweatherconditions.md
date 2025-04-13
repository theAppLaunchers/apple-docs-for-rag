

- WeatherKit REST API
-  DayWeatherConditions 

Object

# DayWeatherConditions

The historical or forecasted weather conditions for a specified day.

Weather API 1.0.0+

``` source
object DayWeatherConditions
```

## Properties

`conditionCode`

`string`

 (Required) 

An enumeration value indicating the condition at the time.

`daytimeForecast`

DayPartForecast

The forecast between 7 AM and 7 PM for the day.

`forecastEnd`

`date-time`

 (Required) 

The ending date and time of the day.

`forecastStart`

`date-time`

 (Required) 

The starting date and time of the day.

`maxUvIndex`

`integer`

 (Required) 

The maximum ultraviolet index value during the day.

`moonPhase`

MoonPhase

 (Required) 

The phase of the moon on the specified day.

`moonrise`

`date-time`

The time of moonrise on the specified day.

`moonset`

`date-time`

The time of moonset on the specified day.

`overnightForecast`

DayPartForecast

The day part forecast between 7 PM and 7 AM for the overnight.

`precipitationAmount`

`number`

 (Required) 

The amount of precipitation forecasted to occur during the day, in millimeters.

`precipitationChance`

`number`

 (Required) 

The chance of precipitation forecasted to occur during the day.

`precipitationType`

PrecipitationType

 (Required) 

The type of precipitation forecasted to occur during the day.

`snowfallAmount`

`number`

 (Required) 

The depth of snow as ice crystals forecasted to occur during the day, in millimeters.

`solarMidnight`

`date-time`

The time when the sun is lowest in the sky.

`solarNoon`

`date-time`

The time when the sun is highest in the sky.

`sunrise`

`date-time`

The time when the top edge of the sun reaches the horizon in the morning.

`sunriseAstronomical`

`date-time`

The time when the sun is 18 degrees below the horizon in the morning.

`sunriseCivil`

`date-time`

The time when the sun is 6 degrees below the horizon in the morning.

`sunriseNautical`

`date-time`

The time when the sun is 12 degrees below the horizon in the morning.

`sunset`

`date-time`

The time when the top edge of the sun reaches the horizon in the evening.

`sunsetAstronomical`

`date-time`

The time when the sun is 18 degrees below the horizon in the evening.

`sunsetCivil`

`date-time`

The time when the sun is 6 degrees below the horizon in the evening.

`sunsetNautical`

`date-time`

The time when the sun is 12 degrees below the horizon in the evening.

`temperatureMax`

`number`

 (Required) 

The maximum temperature forecasted to occur during the day, in degrees Celsius.

`temperatureMin`

`number`

 (Required) 

The minimum temperature forecasted to occur during the day, in degrees Celsius.

## Attributes 

Possible types:

## See Also

### Obtaining daily weather information

object DayPartForecast

A summary forecast for a daytime or overnight period.

object DailyForecast

A collection of day forecasts for a specified range of days.

