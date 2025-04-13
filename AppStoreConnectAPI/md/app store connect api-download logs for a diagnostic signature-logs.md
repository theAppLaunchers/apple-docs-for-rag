

- App Store Connect API
-  Download Logs for a Diagnostic Signature 

Web Service Endpoint

# Download Logs for a Diagnostic Signature

Get the anonymized backtrace logs associated with a specific diagnostic signature.

App Store Connect API 1.2+

## URL

``` source
GET https://api.appstoreconnect.apple.com/v1/diagnosticSignatures/{id}/logs
```

## Path Parameters

`id`

`string`

 (Required) 

The resource ID that uniquely identifies a diagnostic signature. Obtain the diagnostic signature resource ID from the List All Diagnostic Signatures for a Build response.

## Query Parameters

`limit`

`integer`

The maximum number of diagnostic logs to return.

Maximum: `200`

## Response Codes

` 200 ``OK`

diagnosticLogs

`OK`

Content-Type: application/vnd.apple.diagnostic-logs+json

` 400 ``Bad Request`

ErrorResponse

`Bad Request`

An error occurred with your request.

Content-Type: application/json

` 401 ``Unauthorized`

ErrorResponse

`Unauthorized`

Content-Type: application/json

` 403 ``Forbidden`

ErrorResponse

`Forbidden`

Request not authorized.

Content-Type: application/json

` 404 ``Not Found`

ErrorResponse

`Not Found`

Resource not found.

Content-Type: application/json

## Discussion

The example below requests a single disk write diagnostic log for a specific signature.

### Example Request and Response

- Request
- Response

```
GET https://api.appstoreconnect.apple.com/v1/diagnosticSignatures/012a219872fe2aa3ca056df08dc9161007a26879a1c1475ca2e2712f7d0aefd7b4/logs?limit=1
```

```
{
  "productData": [
    {
      "signatureId": "012a219872fe2aa3ca056df08dc9161007a26879a1c1475ca2e2712f7d0aefd7b4",
      "diagnosticInsights": [
        {
          "insightsURL": "doc://com.apple.documentation/documentation/xcode/reducing-disk-writes#Use-Appropriate-Indices",
          "insightsCategory": "SQLiteSpill",
          "insightsString": "SQLite spill file detected. Add appropriate index to improve performance."
        }
      ],
      "diagnosticLogs": [
        {
          "diagnosticMetaData": {
            "event": "disk writes",
            "osVersion": "iPhone OS 14.6 (18F72)",
            "appVersion": "6.10.1",
            "writesCaused": "1073.76 MB",
            "deviceType": "iPhone13_3",
            "platformArchitecture": "arm64",
            "eventDetail": "Total of 1073.76 MB of disk writes"
          },
          "callStackTree": [
            {
              "callStacks": [
                {
                  "callStackRootFrames": [
                    {
                      "offsetIntoBinaryTextSegment": "",
                      "offsetIntoSymbol": "32",
                      "symbolName": "_dispatch_call_block_and_release",
                      "address": "0x19f7cda84",
                      "binaryUUID": "DAF30062-4C85-3B92-B159-50602A0C9D96",
                      "isBlameFrame": false,
                      "binaryName": "libdispatch.dylib",
                      "lineNumber": "1466",
                      "sampleCount": 51,
                      "fileName": "init.c",
                      "rawFrame": "44 _dispatch_call_block_and_release (in libdispatch.dylib) + 32 (init.c:1466) [0x19f7cda84]",
                      "subFrames": [
                        {
                          "offsetIntoBinaryTextSegment": "",
                          "offsetIntoSymbol": "112",
                          "symbolName": "+[TaskHandler updateNames]",
                          "address": "0x102f48b78",
                          "binaryUUID": "2BE5B0BD-0977-3220-B5CB-EBDB66DC3200",
                          "isBlameFrame": true,
                          "binaryName": "ExampleApp",
                          "lineNumber": "2381",
                          "sampleCount": 51,
                          "fileName": "TaskHandler.m",
                          "rawFrame": "44 +[TaskHandler updateNames] (in ExampleApp) + 112 (TaskHandler.m:2092) [0x102f48b74]",
                          "subFrames": [
                            {
                              "offsetIntoBinaryTextSegment": "",
                              "offsetIntoSymbol": "208",
                              "symbolName": "+[TaskHandler getAllItemsFromDB]",
                              "address": "0x102f3ca74",
                              "binaryUUID": "2BE5B0BD-0977-3220-B5CB-EBDB66DC3200",
                              "isBlameFrame": true,
                              "binaryName": "ExampleApp",
                              "lineNumber": "1369",
                              "sampleCount": 51,
                              "fileName": "TaskHandler.m",
                              "rawFrame": "44 +[TaskHandler getAllItemsFromDB] (in ExampleApp) + 208 (TaskHandler.m:1369) [0x102f3ca74]",
                              "subFrames": [
                                {
                                  "offsetIntoBinaryTextSegment": "",
                                  "offsetIntoSymbol": "144",
                                  "symbolName": "-[DatabaseQueue inDatabase:]",
                                  "address": "0x1034dbf04",
                                  "binaryUUID": "2BE5B0BD-0977-3220-B5CB-EBDB66DC3200",
                                  "isBlameFrame": true,
                                  "binaryName": "ExampleApp",
                                  "lineNumber": "157",
                                  "sampleCount": 51,
                                  "fileName": "DatabaseQueue.m",
                                  "rawFrame": "44 -[DatabaseQueue inDatabase:] (in ExampleApp) + 144 (DatabaseQueue.m:157) [0x1034dbf04]",
                                  "subFrames": [
                                    {
                                      "offsetIntoBinaryTextSegment": "",
                                      "offsetIntoSymbol": "176",
                                      "symbolName": "_dispatch_sync_f_slow",
                                      "address": "0x19f7de7b4",
                                      "binaryUUID": "DAF30062-4C85-3B92-B159-50602A0C9D96",
                                      "isBlameFrame": false,
                                      "binaryName": "libdispatch.dylib",
                                      "lineNumber": "1749",
                                      "sampleCount": 48,
                                      "fileName": "queue.c",
                                      "rawFrame": "44 _dispatch_sync_f_slow (in libdispatch.dylib) + 176 (queue.c:1749) [0x19f7de7b4]",
                                      "subFrames": [
                                        {
                                          "offsetIntoBinaryTextSegment": "",
                                          "offsetIntoSymbol": "68",
                                          "symbolName": "_dispatch_sync_invoke_and_complete_recurse",
                                          "address": "0x19f7ded5c",
                                          "binaryUUID": "DAF30062-4C85-3B92-B159-50602A0C9D96",
                                          "isBlameFrame": false,
                                          "binaryName": "libdispatch.dylib",
                                          "lineNumber": "998",
                                          "sampleCount": 48,
                                          "fileName": "queue.c",
                                          "rawFrame": "44 _dispatch_sync_invoke_and_complete_recurse (in libdispatch.dylib) + 68 (queue.c:998) [0x19f7ded5c]",
                                          "subFrames": [
                                            {
                                              "offsetIntoBinaryTextSegment": "",
                                              "offsetIntoSymbol": "20",
                                              "symbolName": "_dispatch_client_callout",
                                              "address": "0x19f7cf81c",
                                              "binaryUUID": "DAF30062-4C85-3B92-B159-50602A0C9D96",
                                              "isBlameFrame": false,
                                              "binaryName": "libdispatch.dylib",
                                              "lineNumber": "559",
                                              "sampleCount": 48,
                                              "fileName": "object.m",
                                              "rawFrame": "44 _dispatch_client_callout (in libdispatch.dylib) + 20 (object.m:559) [0x19f7cf81c]",
                                              "subFrames": [
                                                {
                                                  "offsetIntoBinaryTextSegment": "",
                                                  "offsetIntoSymbol": "60",
                                                  "symbolName": "__30-[DatabaseQueue inDatabase:]_block_invoke",
                                                  "address": "0x1034dbf70",
                                                  "binaryUUID": "2BE5B0BD-0977-3220-B5CB-EBDB66DC3200",
                                                  "isBlameFrame": true,
                                                  "binaryName": "ExampleApp",
                                                  "lineNumber": "160",
                                                  "sampleCount": 48,
                                                  "fileName": "DatabaseQueue.m",
                                                  "rawFrame": "44 __30-[DatabaseQueue inDatabase:]_block_invoke (in ExampleApp) + 60 (DatabaseQueue.m:160) [0x1034dbf70]",
                                                  "subFrames": [
                                                    {
                                                      "offsetIntoBinaryTextSegment": "",
                                                      "offsetIntoSymbol": "180",
                                                      "symbolName": "__39+[TaskHandler getAllItemsFromDB]_block_invoke",
                                                      "address": "0x102f3cb8c",
                                                      "binaryUUID": "2BE5B0BD-0977-3220-B5CB-EBDB66DC3200",
                                                      "isBlameFrame": true,
                                                      "binaryName": "ExampleApp",
                                                      "lineNumber": "1378",
                                                      "sampleCount": 48,
                                                      "fileName": "TaskHandler.m",
                                                      "rawFrame": "44 __39+[TaskHandler getAllItemsFromDB]_block_invoke (in ExampleApp) + 180 (TaskHandler.m:1378) [0x102f3cb8c]",
                                                      "subFrames": [
                                                        {
                                                          "offsetIntoBinaryTextSegment": "",
                                                          "offsetIntoSymbol": "48",
                                                          "symbolName": "-[ResultSet nextWithError:]",
                                                          "address": "0x1034dcc00",
                                                          "binaryUUID": "2BE5B0BD-0977-3220-B5CB-EBDB66DC3200",
                                                          "isBlameFrame": true,
                                                          "binaryName": "ExampleApp",
                                                          "lineNumber": "161",
                                                          "sampleCount": 48,
                                                          "fileName": "ResultSet.m",
                                                          "rawFrame": "44 -[ResultSet nextWithError:] (in ExampleApp) + 48 (ResultSet.m:161) [0x1034dcc00]",
                                                          "subFrames": [
                                                            {
                                                              "offsetIntoBinaryTextSegment": "",
                                                              "offsetIntoSymbol": "300",
                                                              "symbolName": "sqlite3_step",
                                                              "address": "0x1b9980e9c",
                                                              "binaryUUID": "BFD2376F-2E6E-33FD-A5C2-413484CD6D51",
                                                              "isBlameFrame": false,
                                                              "binaryName": "libsqlite3.dylib",
                                                              "lineNumber": "90617",
                                                              "sampleCount": 48,
                                                              "fileName": "sqlite3.c",
                                                              "rawFrame": "44 sqlite3_step (in libsqlite3.dylib) + 300 (sqlite3.c:90617) [0x1b9980e9c]",
                                                              "subFrames": [
                                                                {
                                                                  "offsetIntoBinaryTextSegment": "",
                                                                  "offsetIntoSymbol": "40188",
                                                                  "symbolName": "sqlite3VdbeExec",
                                                                  "address": "0x1b998c240",
                                                                  "binaryUUID": "BFD2376F-2E6E-33FD-A5C2-413484CD6D51",
                                                                  "isBlameFrame": false,
                                                                  "binaryName": "libsqlite3.dylib",
                                                                  "lineNumber": "102825",
                                                                  "sampleCount": 48,
                                                                  "fileName": "sqlite3.c",
                                                                  "rawFrame": "44 sqlite3VdbeExec (in libsqlite3.dylib) + 40188 (sqlite3.c:102825) [0x1b998c240]",
                                                                  "subFrames": [
                                                                    {
                                                                      "offsetIntoBinaryTextSegment": "",
                                                                      "offsetIntoSymbol": "196",
                                                                      "symbolName": "vdbeSorterListToPMA",
                                                                      "address": "0x1b9a08d3c",
                                                                      "insightsCategory": "SQLiteSpill",
                                                                      "binaryUUID": "BFD2376F-2E6E-33FD-A5C2-413484CD6D51",
                                                                      "isBlameFrame": false,
                                                                      "binaryName": "libsqlite3.dylib",
                                                                      "lineNumber": "23794",
                                                                      "sampleCount": 48,
                                                                      "fileName": "sqlite3.c",
                                                                      "rawFrame": "44 vdbeSorterListToPMA (in libsqlite3.dylib) + 196 (sqlite3.c:23794) [0x1b9a08d3c]",
                                                                      "subFrames": [
                                                                        {
                                                                          "offsetIntoBinaryTextSegment": "",
                                                                          "offsetIntoSymbol": "1832",
                                                                          "symbolName": "unixFileControl",
                                                                          "address": "0x1b99c3860",
                                                                          "binaryUUID": "BFD2376F-2E6E-33FD-A5C2-413484CD6D51",
                                                                          "isBlameFrame": false,
                                                                          "binaryName": "libsqlite3.dylib",
                                                                          "lineNumber": "40185",
                                                                          "sampleCount": 48,
                                                                          "fileName": "sqlite3.c",
                                                                          "rawFrame": "44 unixFileControl (in libsqlite3.dylib) + 1832 (sqlite3.c:40185) [0x1b99c3860]",
                                                                          "subFrames": []
                                                                        }
                                                                      ]
                                                                    }
                                                                  ]
                                                                }
                                                              ]
                                                            }
                                                          ]
                                                        }
                                                      ]
                                                    }
                                                  ]
                                                }
                                              ]
                                            }
                                          ]
                                        }
                                      ]
                                    }
                                  ]
                                }
                              ]
                            }
                          ]
                        }
                      ]
                    }
                  ]
                }
              ],
              "callStackPerThread": false
            }
          ]
        }
      ]
    }
  ],
  "version": "1.0.0"
}
```

## See Also

### Getting Metrics and Diagnostic Logs

Retrieve Power and Performance Metrics and Log Insights

Use the App Store Connect API to collect and parse diagnostic logs and metrics for your apps.

Get Power and Performance Metrics for an App

Get the performance and power metrics data for the most recent version of an app.

Get Power and Performance Metrics for a Build

Get the performance and power metrics data for a specific build.

List All Diagnostic Signatures for a Build

List the aggregate backtrace signatures captured for a specific build.

