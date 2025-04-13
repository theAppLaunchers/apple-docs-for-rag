

- Analytics Reports
-  ARKit Capture Frame Rate Throttling 

Article

# ARKit Capture Frame Rate Throttling

Analyze how long it takes for ARKit to throttle the camera frame rate.

## Overview

The data in this report contains information about the time until ARKit starts to throttle the capturing camera frame rate.

- Territories: Worldwide

- Platforms: iOS, iPadOS. For more information about iOS and iPadOS, see the Platforms section in Data Completeness and Corrections.

- Availability:

  - Daily: Every day.

- History: On request, data is available beginning with iOS 17.4 and iPadOS 17.4.

- Completeness: Data from devices that contribute to this report can arrive as late as 8 days after the date it generates on device. You can download recent data daily, but it might be incomplete, and data updates incrementally daily, until all late-arriving events are available.

- Privacy:

  - Includes data from users who have opted to share their data with Apple and developers.

  - Individual rows will only appear if they have a value of 5 or more.

- Data Context: You can analyze your data with additional context by comparing it with the data in the App Sessions Context report, which provides a count of unique devices that use your app on a specific day. For example, if your app performed an action detailed in this report on 10 unique devices on a specific day, and the App Sessions Context report shows there were 100 unique devices running your app that day, then you can approximate that 10% of the devices running your app performed that action.

## Report Fields

| Report Field | Description | Data Type |
|----|----|----|
| Count | Number of times the event occurred | `integer` |
| Territory | Country or region in which the event occurred | `string` |
| Date | Date when the event occurred | `string` |
| Platform | OS version on the device on which the event occurred | `string` |
| Device | Type of device on which the event occurred | `string` |
| Build | Build of device on which event occurred | `string` |
| Unique Devices | The count of unique devices | `integer` |
| Release Type | Type of software release | `string` |
| Time Until Frame Rate Throttling | Time in seconds until ARKit starts to throttle the capture frame rate. | `float` |

## Glossary

| Dimension | Value | Definition |
|----|----|----|
| Time Until Frame Rate Throttling | 0 | Represents range from -Infinity to 0 |
| Time Until Frame Rate Throttling | 1 | Represents range from 0 to 10 |
| Time Until Frame Rate Throttling | 2 | Represents range from 10 to 30 |
| Time Until Frame Rate Throttling | 3 | Represents range from 30 to 60 |
| Time Until Frame Rate Throttling | 4 | Represents range from 60 to 120 |
| Time Until Frame Rate Throttling | 5 | Represents range from 120 to 180 |
| Time Until Frame Rate Throttling | 6 | Represents range from 180 to 240 |
| Time Until Frame Rate Throttling | 7 | Represents range from 240 to 300 |
| Time Until Frame Rate Throttling | 8 | Represents range from 300 to 600 |
| Time Until Frame Rate Throttling | 9 | Represents range from 600 to 900 |
| Time Until Frame Rate Throttling | 10 | Represents range from 900 to 1200 |
| Time Until Frame Rate Throttling | 11 | Represents range from 1200 to +Infinity |

## See Also

### Framework Usage

AccessorySetupKit Accessory Picker Sessions

Analyze how many people use your app to set up accessories by using AccessorySetupKit.

AccessorySetupKit Usage

Analyze how often your app uses AccessorySetupKit.

AirPlay Discovery Sessions

Review information about AirPlay discovery sessions.

Animoji Stickers Sent

Analyze how many times people use Memoji stickers in your app.

App Added to Focus

Review information about your app’s relationship to Focus modes.

App Disk Space Usage

Analyze your app’s disk space use.

App Runtime Usage

Analyze how often your app executes specific symbols of different dynamic libraries.

App Sessions Context

Analyze how many people use your app and for how long.

Application Preferred Language Settings

Review how people use language preference settings in your app.

ARKit ARSession Duration

Review information about ARKit ARSession duration.

ARKit ARSession Failures

Analyze details about ARKit ARSession failures.

ARKit Collaborative Session Features

Review how your app uses ARKit collaborative session features.

ARKit Face Tracking

Analyze how often your app uses ARKit face tracking.

ARKit Video Formats

Review information about ARKit video formats and high-resolution frames.

ARKit World Tracking

Review the configured settings for world tracking in your app.

