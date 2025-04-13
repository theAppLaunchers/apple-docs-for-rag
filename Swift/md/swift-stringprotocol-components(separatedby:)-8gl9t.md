

- Swift
- StringProtocol
-  components(separatedBy:) 

Instance Method

# components(separatedBy:)

Returns an array containing substrings from the string that have been divided by the given separator.

iOS 8.0+iPadOS 8.0+Mac Catalyst 8.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func components(separatedBy separator: T) -> [String] where T : StringProtocol
```

## Parameters 

`separator`  

The separator string.

## Return Value

An array containing substrings that have been divided from the string using `separator`.

## Discussion

The substrings in the resulting array appear in the same order as the original string. Adjacent occurrences of the separator string produce empty strings in the result. Similarly, if the string begins or ends with the separator, the first or last substring, respectively, is empty. The following example shows this behavior:

```
let list1 = "Karin, Carrie, David"
let items1 = list1.components(separatedBy: ", ")
// ["Karin", "Carrie", "David"]

// Beginning with the separator:
let list2 = ", Norman, Stanley, Fletcher"
let items2 = list2.components(separatedBy: ", ")
// ["", "Norman", "Stanley", "Fletcher"
```

If the list has no separators, the array contains only the original string itself.

```
let name = "Karin"
let list = name.components(separatedBy: ", ")
// ["Karin"]
```

