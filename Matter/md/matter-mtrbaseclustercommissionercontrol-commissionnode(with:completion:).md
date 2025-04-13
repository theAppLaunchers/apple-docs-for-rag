

- Matter
- MTRBaseClusterCommissionerControl
-  commissionNode(with:completion:) 

Instance Method

# commissionNode(with:completion:)

Command CommissionNode

iOS 18.4+iPadOS 18.4+Mac Catalyst 18.4+macOS 15.4+tvOS 18.4+visionOS 2.4+watchOS 11.4+

``` source
func commissionNode(
    with params: MTRCommissionerControlClusterCommissionNodeParams,
    completion: @escaping (MTRCommissionerControlClusterReverseOpenCommissioningWindowParams?, (any Error)?) -> Void
)
```

``` source
func commissionNode(with params: MTRCommissionerControlClusterCommissionNodeParams) async throws -> MTRCommissionerControlClusterReverseOpenCommissioningWindowParams
```

## Discussion

This command is sent by a client to request that the server begins commissioning a previously approved request.

