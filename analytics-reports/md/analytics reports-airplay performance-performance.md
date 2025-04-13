

- Analytics Reports
-  AirPlay Performance 

Article

# AirPlay Performance

Review AirPlay performance in your apps.

## Overview

The data in this report contains performance measures for AirPlay usage. The metrics include Video Start Up Time, Activate to Start Time, and Session Duration. The report presents each measure along with a configuration made up of multiple dimensions.

## Report Fields

| Report Field | Description | Data Type |
|----|----|----|
| Average Video Start Up Time | Time spent in milliseconds from end of endpoint activation to the start of playback of the first item | float |
| Average Activate to Start Time | Time spent in milliseconds between the end of endpoint activation and the initiation of the playback session | float |
| Average AirPlay Session Duration | Average duration in seconds that the AirPlay session was active | float |
| Video Session Type | Type of session. Values can be of type: `RC` for `APEndpointPlaybackSessionRemoteControl`, `AP` for `APEndpointPlaybackSessionAirPlay`, or `MC` for `APEndpointPlaybackSessionMC`. | string |
| Media Type | Type of media. Values can be of type: `LocalFileEncrypted`, `LocalFileNonEncrypted`, `RemoteFileEncrypted`, `RemoteFileNonEncrypted`, `HLSEncrypted`, or `HLSNonEncrypted`. | string |
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

Streaming Downloads Performance

Review download performance when using the AVAssetDownloadTask APIs in your apps.

