

- ThreadNetwork
- THClient
-  deleteCredentials(forBorderAgent:completion:) 

Instance Method

# deleteCredentials(forBorderAgent:completion:)

Deletes Thread network credentials from the framework database for a Border Agent.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 13.0+visionOS 1.0+

``` source
func deleteCredentials(
    forBorderAgent borderAgentID: Data,
    completion: @escaping ((any Error)?) -> Void
)
```

``` source
func deleteCredentials(forBorderAgent borderAgentID: Data) async throws
```

## Parameters 

`borderAgentID`  

The identifer of a Thread network Border Agent.

`completion`  

The completion handler the framework calls after deleting the credentials.

## Mentioned in 

Managing Thread network credentials

## Discussion

Concurrency note

You can call this method from synchronous code using a completion handler, as shown on this page, or you can call it as an asynchronous method that has the following declaration:

```
func deleteCredentials(forBorderAgent borderAgentID: Data) async throws
```

For information about concurrency and asynchronous code in Swift, see Calling Objective-C APIs Asynchronously.

The Border Agent is the software component running in the Border Router responsible for advertising itself in the Wi-Fi or Ethernet network.

Call the method as follows:

```
func removeCredentials(borderAgentID: Data) async -> (Error?) {
    let client = THClient()
    var err:Error?
    do {
        err = try await client.deleteCredentials(forBorderAgent: borderAgentID) as? Error
    } catch {
        err = error
    }
    return (err)
}
```

## See Also

### Storing and Deleting Credentials

func storeCredentials(forBorderAgent: Data, activeOperationalDataSet: Data, completion: ((any Error)?) -> Void)

Stores Thread network credentials into the framework database that a Border Agent provides.

