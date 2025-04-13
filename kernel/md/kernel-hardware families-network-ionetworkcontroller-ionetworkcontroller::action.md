

- Kernel
- Hardware Families
- Network
- IONetworkController
-  IONetworkController::Action 

# IONetworkController::Action

``` source
typedef IOReturn ( *Action)(
   void *target,
   void *param0,
   void *param1,
   void *param2,
   void *param3);
```

## Parameters 

`target`  

The first argument passed to action.

`param0`  

Action parameter 0.

`param1`  

Action parameter 1.

`param2`  

Action parameter 2.

`param3`  

Action parameter 3.

## Overview

Definition of a C function that can be called through executeCommand().

## See Also

### Callbacks

Action

