

- SMS and Call Reporting
- LiveCallerIDLookupManager
-  status(forExtensionWithIdentifier:) 

Instance Method

# status(forExtensionWithIdentifier:)

Queries the system to check the status of the app extension.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+visionOS 2.0+watchOS 11.0+

``` source
func status(forExtensionWithIdentifier identifier: String) -> CallLookupExtensionStatus
```

## Parameters 

`identifier`  

The identifier for the app extension.

## Mentioned in 

Getting up-to-date calling and blocking information for your app

## See Also

### Checking status and fetching data

let extensionPointName: String

The name of the extension point.

func openSettings() async throws

Navigates to Settings so a person can configure the Live Caller ID Lookup app extension.

func refreshPIRParameters(forExtensionWithIdentifier: String) async throws

Communicates with the system to refetch Private Information Retrieval (PIR) parameters from the server.

func reset(forExtensionWithIdentifier: String) async throws

Resets the cache associated with the app extension.

