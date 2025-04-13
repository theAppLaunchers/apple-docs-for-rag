

- Core Services
- Apple Events
- Key Form and Descriptor Type Object Specifier Constants
-  typeRangeDescriptor 

Global Variable

# typeRangeDescriptor

Mac Catalyst 13.0+macOS 10.0+

``` source
var typeRangeDescriptor: DescType { get }
```

## Discussion

Specifies a range descriptor that identifies two Apple event objects marking the beginning and end of a range of elements. The data for a range descriptor consists of two keyword-specified descriptors with the keywords `keyAERangeStart` and `keyAERangeStop`, respectively, which specify the first Apple event object in the desired range and the last Apple event object in the desired range.

