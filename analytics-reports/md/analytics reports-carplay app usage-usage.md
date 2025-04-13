

- Analytics Reports
-  CarPlay App Usage 

Article

# CarPlay App Usage

Review how people use CarPlay in your app.

## Overview

This data details how your application is used in CarPlay.

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
| Category | Category of the app | `string` |
| Dashboard Visible Time | The amount of time (in seconds) that the app was visible on the CarPlay dashboard | `float` |
| Playback Time | For audio apps, the amount of time (in seconds) that the app was playing audio during this CarPlay session. | `integer` |
| Siri Presentation Count | The number of times an app was interacted with via Siri | `integer` |
| visibleTime | The amount of time (in seconds) that the app was visible on-screen in the CarPlay session. | `integer` |

## Glossary

| Dimension | Value          | Definition               |
|-----------|----------------|--------------------------|
| Category  | Audio          | Audio apps               |
| Category  | Navigation     | Navigation apps          |
| Category  | Communications | Communications apps      |
| Category  | Automaker      | Automaker apps           |
| Category  | Quick Ordering | Quick food ordering apps |
| Category  | Charging       | Charging apps            |
| Category  | Parking        | Parking apps             |
| Category  | Fueling        | Fueling apps             |
| Category  | Driving Task   | Driving task apps        |

## See Also

### App Usage

App Clip Usage

Analyze how users engage with your App Clips.

App Crashes

Review crashes for your App Store apps based on app version and device type.

App Store Installations and Deletions

Analyze details on the number of times users install and delete your apps.

App Sessions

Analyze how often people open your App Store apps, and the average session duration.

