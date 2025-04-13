

- Local Authentication
- LARightStore
-  saveRight(\_:identifier:completion:) 

Instance Method

# saveRight(\_:identifier:completion:)

Saves a right to a persistent right store.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+visionOS 1.0+

``` source
func saveRight(
    _ right: LARight,
    identifier: String,
    completion handler: @escaping (LAPersistedRight?, (any Error)?) -> Void
)
```

``` source
func saveRight(
    _ right: LARight,
    identifier: String
) async throws -> LAPersistedRight
```

## Parameters 

`right`  

The right to store.

`identifier`  

A unique identifier for the right.

`handler`  

A completion handler to call when the save operation completes.

`right`  
The persisted form of the right that the save operation stores.

`error`  
An error object that indicates why the `right` parameter is `nil`, or `nil` if the right parameter is non-`nil`.

## Discussion

Important

You can call this method from synchronous code using a completion handler, as shown on this page, or you can call it as an asynchronous method that has the following declaration:

```
func saveRight(_ right: LARight, identifier: String) async throws -> LAPersistedRight
```

For information about concurrency and asynchronous code in Swift, see Calling Objective-C APIs Asynchronously.

## See Also

### Storing rights

func saveRight(LARight, identifier: String, secret: Data, completion: (LAPersistedRight?, (any Error)?) -> Void)

Saves a right to a persistent store along with secret data you supply.

