

- Core Services
- Apple Events
- Key Form and Descriptor Type Object Specifier Constants
-  formRelativePosition 

Global Variable

# formRelativePosition

Mac Catalyst 13.0+macOS 10.0+

``` source
var formRelativePosition: Int { get }
```

## Discussion

Specifies an element position either immediately before or immediately after a container, not inside it. The key data is specified by a descriptor of type `typeEnumerated` whose data consists of one of the constants `kAENext` and `kAEPrevious`, which are described in AEDisposeToken(_:).

