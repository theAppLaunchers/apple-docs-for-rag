

- SwiftUI
- SectionConfiguration
-  containerValues 

Instance Property

# containerValues

The container values associated with the given section.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+watchOS 11.0+

``` source
var containerValues: ContainerValues { get }
```

## Discussion

Only explicitly created sections are able to have container values, meaning this container values will be empty if the section is implicit.

