

- Analytics Reports
-  Streaming Downloads Performance 

Article

# Streaming Downloads Performance

Review download performance when using the AVAssetDownloadTask APIs in your apps.

## Overview

You can use the AVAssetDownloadTask API and others in AVFoundation to download the HTTP Live Streaming (HLS) content to disk for offline playback. The data in this report contains aggregate information about download performance.

- Privacy Measures: Data for this report is collected from select 3rd party apps. Each data point in this report comes from at least 200 downloads. Data points with fewer downloads are omitted.

- Data Source: Data in this report only comes from devices that opt in to share data with Apple and developers.

- Historical Data: One-time snapshots for this report are available beginning in February 2024, if there are events for the report.

## Report Fields

| Report Field | Description | Data Type |
|----|----|----|
| Download Count | Total number of downloads | integer |
| Interface Type | Type of network interface for the playback. Values can be of type: `WiFi`, `Cellular`, `Loopback`, `Wired`, `Cache`, or `Unknown`. | string |
| Download Speed Distribution | Distribution of the download speeds, in bits per second. Values are an array of percentiles: 10th, 25th, 50th, 75th, 95th, 99th. | list of float |
| Downloaded Bytes Distribution | Distribution of the total number of bytes downloaded. Values are an array of percentiles: 10th, 25th, 50th, 75th, 95th, 99th. | list of float |
| Download Error Rate | Download failure rate in percentages | float |
| Date | Date when the event occurred | string |
| Territory | Country or region in which the event occurred | string |
| Device | Type of device on which the event occurred | string |
| Platform Version | Operating System (OS) version on the device on which the event occurred | string |
| Build Type | Build type of device on which the event occurred | string |
| Build | Build of device on which the event occurred | string |

## See Also

### Performance

AirPlay Errors

Analyze AirPlay errors in your apps.

AirPlay Performance

Review AirPlay performance in your apps.

App Crashes Expanded

Analyze the rate at which your app crashes.

App Installs Performance

Analyze details about installation success and failure rates for your apps.

App Storage Reads and Writes

Analyze how often your app uses disk reads and writes.

Audio Overloads

Analyze how many audio glitches people experience in your app.

Bluetooth LE Session Duration

Analyze how long your app uses Bluetooth Low Energy (LE) connections.

Bluetooth System Wakes

Analyze details about bluetooth system wakes that your app causes.

CAMetalLayer Performance

Review CAMetalLayer metadata and performance in your app.

Custom Language Model Builds Failed

Analyze how often your app-triggered rebuild of a custom language model failed.

Display Power Information

Review your app’s impact on display pixel attributes.

HTTP Live Streaming Playback Errors

Analyze playback errors that your app receives.

Launch Image Over Memory Limit

Analyze how often your app fails to load because it’s over the memory limit.

Networking Connection Activity

Review how your app uses network connections.

Spotlight Query Performance

Review how your app uses Spotlight queries.

