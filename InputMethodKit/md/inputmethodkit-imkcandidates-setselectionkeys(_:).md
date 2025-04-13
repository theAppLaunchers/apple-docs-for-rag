

- InputMethodKit
- IMKCandidates
-  setSelectionKeys(\_:) 

Instance Method

# setSelectionKeys(\_:)

Sets the selection keys for the candidates.

macOS 10.5+

``` source
@MainActor
func setSelectionKeys(_ keyCodes: [Any]!)
```

## Parameters 

`keyCodes`  

An array of `NSNumber` objects where each `NSNumber` object represents a virtual key code. The input controller maps these key codes to characters that are displayed either across the top of the candidates, if the candidates are laid out horizontally, or along the left edge of the candidates, if they are aligned vertically.

## Discussion

Selection keys are keys that can be used to select one of the candidates. They are displayed next to the candidate that will be selected when the user types that key.

The number of selection keys determines how many candidates are displayed per page. For example, if you pass an array of four key codes, four candidates are displayed per page. If you pass eleven key codes, eleven candidates are displayed. By default, the key codes are mapped using the keyboard layout whose source id is `com.apple.keylayout.US`. You can replace the default layout by calling setSelectionKeysKeylayout(_:). The default selection keys are the digits 1 through 9 or, in terms of key codes, 18, 19, 20, 21, 23, 22, 26, 28, and 25.

## See Also

### Managing Selection Keys

func selectionKeys() -> [Any]!

Returns an array of `NSNumber` objects where each `NSNumber` object represents a virtual key code.

func setSelectionKeysKeylayout(TISInputSource!)

Sets the key layout that is used to map virtual key codes to characters.

func selectionKeysKeylayout() -> Unmanaged&lt;TISInputSource>!

Returns the key layout that maps virtual key codes to selection keys.

