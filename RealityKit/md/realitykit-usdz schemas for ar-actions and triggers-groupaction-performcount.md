

- RealityKit
- USD Assets
- 
  - USD Assets
- USDZ schemas for AR
- Actions and triggers
- GroupAction
-  performCount 

Article

# performCount

A value that specifies the number of times the group’s actions repeat.

## Overview

The default value is `1`, which execute the actions only once. If the value is `0` and `loops` is set to `true`, the actions execute infinitely. If the value is a number (*n*) and the type is `serial`, the actions execute *n* times in sequence. And if the value is set to a number (*n*) and the type is `parallel`, the actions execute *n* times independently.

### Declaration

```
uniform uint performCount = 1
```

## See Also

### Properties

info:id

The action’s unique identifier.

type

An option that controls the order in which the actions execute.

loops

A Boolean value indicating whether the group loops.

actions

A list of actions that make up the group.

