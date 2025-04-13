

- FSKit
- FSVolume
- FSVolume.ItemDeactivation
-  itemDeactivationPolicy 

Instance Property

# itemDeactivationPolicy

A property that tells FSKit to which types of items the deactivation applies, if any.

macOS 15.4+

``` source
var itemDeactivationPolicy: FSVolume.ItemDeactivationOptions { get }
```

**Required**

## Discussion

FSKit reads this value after the file system replies to the `loadResource` message. Changing the returned value during the runtime of the volume has no effect.

## See Also

### Setting deactivation policy

struct ItemDeactivationOptions

Options to specify the item deactivation policy.

