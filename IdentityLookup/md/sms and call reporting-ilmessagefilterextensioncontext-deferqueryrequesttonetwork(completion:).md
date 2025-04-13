

- SMS and Call Reporting
- ILMessageFilterExtensionContext
-  deferQueryRequestToNetwork(completion:) 

Instance Method

# deferQueryRequestToNetwork(completion:)

Tells the system to pass the current query request to the app extension’s associated network service.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.0+visionOS 1.0+

``` source
func deferQueryRequestToNetwork(completion: @escaping (ILNetworkResponse?, (any Error)?) -> Void)
```

``` source
func deferQueryRequestToNetwork() async throws -> ILNetworkResponse
```

## Parameters 

`completion`  

A completion block that contains either the network response to the HTTPS request or an error.

## Discussion

When your Message Filter app extension calls this method to defer a query to its associated server, the system performs an HTTPS network request to a URL specified in the app extension’s `Info.plist` file. The system returns the response to that request (or an error) asynchronously in an ILNetworkResponse object.

To make a network request on behalf of a Message Filter app extension, the system uses an HTTP `POST` request formatted in JSON, similar to the request shown below.

```
POST /server-endpoint HTTP/1.1
Accept: */*
Content-Type: application/json; charset=utf-8
Content-Length: 148
```

Payload:

```
```

