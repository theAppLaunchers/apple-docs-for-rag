

- Core Foundation
-  CFBagGetValueIfPresent(\_:\_:\_:) 

Function

# CFBagGetValueIfPresent(\_:\_:\_:)

Reports whether or not a value is in a bag, and returns that value indirectly if it exists.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

``` source
func CFBagGetValueIfPresent(
    _ theBag: CFBag!,
    _ candidate: UnsafeRawPointer!,
    _ value: UnsafeMutablePointer!
) -> Bool
```

## Parameters 

`theBag`  

The bag to be searched.

`candidate`  

The value for which to find matches in `theBag`. The equal callback provided when `theBag` was created is used to compare. If the equal callback was `NULL`, pointer equality (in C, ==) is used. If `candidate`, or any other value in `theBag`, is not understood by the equal callback, the behavior is undefined.

`value`  

A pointer to a value object. Set to the matching value if it exists in the bag, otherwise `NULL`. If the value is a Core Foundation object, ownership follows the The Get Rule.

## Return Value

`true` if `value` is present in `theBag`, otherwise `false`.

## Discussion

Depending on the implementation of the equal callback specified when creating `theBag`, the value returned in `value` may not have the same pointer equality as `candidate`.

## See Also

### Examining a Bag

func CFBagContainsValue(CFBag!, UnsafeRawPointer!) -> Bool

Reports whether or not a value is in a bag.

func CFBagGetCount(CFBag!) -> CFIndex

Returns the number of values currently in a bag.

func CFBagGetCountOfValue(CFBag!, UnsafeRawPointer!) -> CFIndex

Returns the number of times a value occurs in a bag.

func CFBagGetValue(CFBag!, UnsafeRawPointer!) -> UnsafeRawPointer!

Returns a requested value from a bag.

func CFBagGetValues(CFBag!, UnsafeMutablePointer&lt;UnsafeRawPointer?>!)

Fills a buffer with values from a bag.

