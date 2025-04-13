

- Group Activities
- GroupActivityMetadata
- GroupActivityMetadata.LifetimePolicy
-  automatic 

Type Property

# automatic

The default lifetime policy for a group activity.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+

``` source
static let automatic: GroupActivityMetadata.LifetimePolicy
```

## Discussion

Initiators and participants will have the option to leave the activity independently or end it for everyone. When everyone has left the activity, it will end.

This case should be used by most apps and allows activities to continue until all participants leave the activity – regardless of which participant happens to have initiated the activity.

