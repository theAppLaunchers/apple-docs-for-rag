

- Objective-C Runtime
- NSObject
-  willChange(\_:valuesAt:forKey:) 

Instance Method

# willChange(\_:valuesAt:forKey:)

Informs the observed object that the specified change is about to be executed at given indexes for a specified ordered to-many relationship.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

``` source
func willChange(
    _ changeKind: NSKeyValueChange,
    valuesAt indexes: IndexSet,
    forKey key: String
)
```

## Parameters 

`changeKind`  

The type of change that is about to be made.

`indexes`  

The indexes of the to-many relationship that will be affected by the change.

`key`  

The name of a property that is an ordered to-many relationship.

## Discussion

Use this method when implementing key-value-observing compliance manually.

Important

After the values have been changed, a corresponding didChange(_:valuesAt:forKey:) must be invoked with the same parameters.

### Special Considerations

You rarely need to override this method in subclasses, but if you do, be sure to call `super`.

## See Also

### Notifying Observers of Changes

func willChangeValue(forKey: String)

Informs the observed object that the value of a given property is about to change.

func didChangeValue(forKey: String)

Informs the observed object that the value of a given property has changed.

func didChange(NSKeyValueChange, valuesAt: IndexSet, forKey: String)

Informs the observed object that the specified change has occurred on the indexes for a specified ordered to-many relationship.

func willChangeValue(forKey: String, withSetMutation: NSKeyValueSetMutationKind, using: Set&lt;AnyHashable>)

Informs the observed object that the specified change is about to be made to a specified unordered to-many relationship.

func didChangeValue(forKey: String, withSetMutation: NSKeyValueSetMutationKind, using: Set&lt;AnyHashable>)

Informs the observed object that the specified change was made to a specified unordered to-many relationship.

