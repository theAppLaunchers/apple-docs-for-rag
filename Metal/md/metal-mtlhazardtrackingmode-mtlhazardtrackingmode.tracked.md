

- Metal
- MTLHazardTrackingMode
-  MTLHazardTrackingMode.tracked 

Case

# MTLHazardTrackingMode.tracked

An option specifying that Metal prevents hazards when modifying this object’s contents.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.1+macOS 10.15+tvOS 13.0+visionOS 1.0+

``` source
case tracked
```

## Discussion

For a resource, Metal tracks dependencies on any accesses to the resource. If you submit a command that modifies the resource, Metal delays that command from executing until prior commands accessing that resource are complete, and prevents future commands from executing until the modifications are complete.

For a heap, Metal tracks dependencies on accesses to *any* resources on the heap. If you submit a command that modifies a resource on a heap, Metal delays that command from executing until prior commands accessing the heap’s resources are complete, and prevents future commands accessing the heap’s resources from executing until the modifications are complete. For better performance, use untracked resources and synchronize access yourself.

## See Also

### Specifying the Tracking Mode

case `default`

An option specifying that the default tracking mode should be used.

case untracked

An option specifying that the app must prevent hazards when modifying this object’s contents.

