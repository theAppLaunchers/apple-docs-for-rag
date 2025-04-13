

- Core Services
- Apple Events
-  AECreateList(\_:\_:\_:\_:) 

Function

# AECreateList(\_:\_:\_:\_:)

Creates an empty descriptor list or Apple event record.

macOS 10.0+

``` source
func AECreateList(
    _ factoringPtr: UnsafeRawPointer!,
    _ factoredSize: Size,
    _ isRecord: Bool,
    _ resultList: UnsafeMutablePointer!
) -> OSErr
```

## Parameters 

`factoringPtr`  

A pointer to the data at the beginning of each descriptor that is the same for all descriptors in the list. If there is no common data, or if you decide not to isolate the common data, pass `NULL` as the value of this parameter.

`factoredSize`  

The size of the common data. If there is no common data, or if you decide not to isolate the common data, pass 0 as the value of this parameter. (See the Discussion section for more information.)

`isRecord`  

A Boolean value that specifies the kind of list to create. Pass a value of `TRUE` to create an Apple event record (a data structure of type AERecord) or `FALSE` to create a descriptor list.

`resultList`  

A pointer to a descriptor list variable. On successful return, the descriptor list or Apple event record that the `AECreateList` function creates. On error, a null descriptor. See AEDescList.

## Return Value

A result code. See Result Codes.

## Discussion

The `AECreateList` function creates an empty descriptor list or Apple event record. You can use the functions described in “Adding Items to Descriptor Lists” to populate the list as part of creating an Apple event. After sending the Apple event with the `AESend(_:_:_:_:_:_:_:)` function, you should dispose of the descriptor list with the AEDisposeDesc(_:) function when you no longer need it.

If you intend to use a descriptor list for a factored Apple event array, you must provide, in the `factoringPtr` parameter, a pointer to the data shared by all items in the array and, in the `factoredSize` parameter, the size of the common data. The common data must be 4, 8, or more than 8 bytes in length because it always consists of (a) the descriptor type (4 bytes) (b) the descriptor type (4 bytes) and the size of each item’s data (4 bytes) or (c) the descriptor type (4 bytes), the size of each item’s data (4 bytes), and some portion of the data itself (1 or more bytes).

For information about data types used with Apple event arrays, see Data Types.

### Version-Notes

The `factoringPtr` and `factoredSize` parameters are not supported in macOS 10.2 and later. You should pass `NULL` and zero, respectively, for these parameters.

Thread safe starting in OS X v10.2.

