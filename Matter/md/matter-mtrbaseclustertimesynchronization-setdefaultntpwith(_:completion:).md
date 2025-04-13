

- Matter
- MTRBaseClusterTimeSynchronization
-  setDefaultNTPWith(\_:completion:) 

Instance Method

# setDefaultNTPWith(\_:completion:)

Command SetDefaultNTP

iOS 18.4+iPadOS 18.4+Mac Catalyst 18.4+macOS 15.4+tvOS 18.4+visionOS 2.4+watchOS 11.4+

``` source
func setDefaultNTPWith(
    _ params: MTRTimeSynchronizationClusterSetDefaultNTPParams,
    completion: @escaping MTRStatusCompletion
)
```

``` source
func setDefaultNTPWith(_ params: MTRTimeSynchronizationClusterSetDefaultNTPParams) async throws
```

## Discussion

This command is used to set DefaultNTP.

