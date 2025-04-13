

- Matter
- MTRBaseClusterThreadBorderRouterManagement
-  setPendingDatasetRequestWith(\_:completion:) 

Instance Method

# setPendingDatasetRequestWith(\_:completion:)

Command SetPendingDatasetRequest

iOS 18.4+iPadOS 18.4+Mac Catalyst 18.4+macOS 15.4+tvOS 18.4+visionOS 2.4+watchOS 11.4+

``` source
func setPendingDatasetRequestWith(
    _ params: MTRThreadBorderRouterManagementClusterSetPendingDatasetRequestParams,
    completion: @escaping MTRStatusCompletion
)
```

``` source
func setPendingDatasetRequestWith(_ params: MTRThreadBorderRouterManagementClusterSetPendingDatasetRequestParams) async throws
```

## Discussion

Command set or update the pending Dataset of the Thread network to which the Border Router is connected.

