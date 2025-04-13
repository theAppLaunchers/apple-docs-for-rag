

- Core Services
- Apple Events
- Key Form and Descriptor Type Object Specifier Constants
-  typeObjectBeingExamined 

Global Variable

# typeObjectBeingExamined

Mac Catalyst 13.0+macOS 10.12+

``` source
var typeObjectBeingExamined: DescType { get }
```

## Discussion

Specifies a descriptor that acts as a placeholder for each of the successive elements in a container when the Apple Event Manager tests those elements one at a time. The descriptor has a null data storage pointer. This descriptor type is used only with `formTest`.

