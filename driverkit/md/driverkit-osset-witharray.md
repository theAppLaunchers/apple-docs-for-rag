

- DriverKit
- OSSet
-  withArray 

Static Method

# withArray

Creates and initializes an OSSet populated with the contents of an OSArray.

DriverKitiOSiPadOSmacOS

``` source
static OSSetPtr withArray(const OSArray * array, uint32_t capacity);
```

## Parameters 

`array`  

An array whose objects will be stored in the new OSSet.

`capacity`  

The initial storage capacity of the new set object. If 0, the capacity is set to the number of objects in `array`; otherwise `capacity` must be greater than or equal to the number of objects in `array`.

## Return Value

An instance of OSSet containing the objects of `array`, with a retain count of 1; `NULL` on failure.

## Discussion

Each distinct object in `array` is added to the new set.

`array` must be non-`NULL`. If `capacity` is nonzero, it must be greater than or equal to `count`. The new OSSet will grow as needed to accommodate more key-object pairs (*unlike*CFMutableSet, for which the initial capacity is a hard limit).

The objects in `array` are retained for storage in the new set, not copied.

