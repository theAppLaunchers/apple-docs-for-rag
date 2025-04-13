

- Matter
- MTRBaseClusterThermostat
-  atomicRequest(with:completion:) 

Instance Method

# atomicRequest(with:completion:)

Command AtomicRequest

iOS 18.4+iPadOS 18.4+Mac Catalyst 18.4+macOS 15.4+tvOS 18.4+visionOS 2.4+watchOS 11.4+

``` source
func atomicRequest(
    with params: MTRThermostatClusterAtomicRequestParams,
    completion: @escaping (MTRThermostatClusterAtomicResponseParams?, (any Error)?) -> Void
)
```

``` source
func atomicRequest(with params: MTRThermostatClusterAtomicRequestParams) async throws -> MTRThermostatClusterAtomicResponseParams
```

## Discussion

Begins, Commits or Cancels an atomic write

