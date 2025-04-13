

- Analytics Reports
-  App Sessions 

Article

# App Sessions

Analyze how often people open your App Store apps, and the average session duration.

## Overview

Use these reports to understand how often people open your app, and how long they spend in your app.

- Territories: Worldwide

- Platforms: iOS, iPadOS, macOS, tvOS, visionOS

- Availability:

  - Daily: Every day

  - Weekly: Every Friday for the previous week (Monday to Sunday).

  - Monthly: On the fifth day of the following month.

- Completeness: Within five days. Weekly and monthly reports are complete by default.

- History: On request, data is available beginning from January 1, 2024.

- Privacy:

  - Includes data from users who have opted to share their data with Apple and developers. Data is provided only when events exist from at least five users for the respective report.

  - Data is available in two reports: standard and detailed. *Standard* reports include fields not easily related to uniquely identifiable user data. *Detailed* reports include all fields and also include additional privacy measures for the data, to help protect uniquely identifiable information for individuals. Download the standard report unless you need to analyze the unique fields in the detailed report. To learn more, see Protecting user privacy in report data.

The Analytics Reports framework delivers new portions of report content as instances. Each instance can contain one or more batches of data, to accommodate late-arriving events, or in rare cases, data corrections. To learn more, see Data Completeness and Corrections.

## Report Fields

| Report Field | Description | Data Type | Standard Report | Detailed Report |
|----|----|----|----|----|
| Date | Date on which the event occurred. For weekly and monthly instances, this column represents the first day of the week and month, respectively. | `date` | ✔ | ✔ |
| App Name | The name of the app provided by you during app setup in App Store Connect. | `string` | ✔ | ✔ |
| App Apple Identifier | Your app’s Apple ID. | `integer` | ✔ | ✔ |
| App Version | The version of the app being associated with the session. | `string` | ✔ | ✔ |
| Device | Type of device on which the event occurred | `string` | ✔ | ✔ |
| Platform Version | The OS version on the device associated with the session. | `string` | ✔ | ✔ |
| Source Type | Where the user discovered the app associated with the session. | `string` | ✔ | ✔ |
| Source Info | The app referrer or web referrer that led the user to discover the app. | `string` |  | ✔ |
| Campaign | The Campaign Token of the campaign created in App Analytics. Column available starting November 19, 2024. | `string` |  | ✔ |
| Page Type | The product page type which led the user to download the app associated with the session. | `string` | ✔ | ✔ |
| Page Title | The name of the product page or in-app event page that led the user to download the app associated with the session. | `string` |  | ✔ |
| App Download Date | The date on which the app was downloaded onto the device. This field is only populated if the download occurred in the previous 30 days, otherwise it is null. | `date` | ✔ | ✔ |
| Territory | The App Store country or region in which the session occurred. | `string` | ✔ | ✔ |
| Sessions | The number of sessions. Based on users who have agreed to share their data with Apple and developers. | `integer` | ✔ | ✔ |
| Total Session Duration | The total duration, in seconds, of all sessions being reported. | `integer` | ✔ | ✔ |
| Unique Devices | The number of unique devices contributing to the total number of sessions being reported. | `integer` | ✔ | ✔ |

## Glossary

| Dimension | Value | Definition |
|----|----|----|
| Source Type | App Store search | Your app was viewed in the search tab on the App Store. Includes Search Ads and suggestions in App Store search. |
| Source Type | App Store browse | Your app was viewed while the user was browsing the App Store. Includes all App Store tabs excluding the Search tab. |
| Source Type | App referrer | A link to your app’s product page was presented to the user in another app. |
| Source Type | Web referrer | A link to your app’s product page was presented to the user on a website. |
| Source Type | App Clip | Your app was presented to the user in an App Clip. |
| Source Type | Notification | Your app was presented to the user in an App Store generated notification. |
| Source Type | Unavailable | The source type is unavailable. Includes apps downloaded using App Store gift cards, promotional codes, or Mobile Device Management software. |
| Page Type | Product page | The user downloaded your app from your app’s product page. |
| Page Type | In-app event | The user downloaded your app from an in-app event page. |
| Page Type | Store sheet | The user downloaded the app from a store sheet in the App Store. |
| Page Type | No page | Your app was presented in a list view to the user and there was no page title associated with the download. |
| Page Type | Notification | Your app was presented to the user in an App Store generated notification. |

## See Also

### App Usage

App Clip Usage

Analyze how users engage with your App Clips.

App Crashes

Review crashes for your App Store apps based on app version and device type.

App Store Installations and Deletions

Analyze details on the number of times users install and delete your apps.

CarPlay App Usage

Review how people use CarPlay in your app.

