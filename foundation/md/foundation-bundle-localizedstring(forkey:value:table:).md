

- Foundation
- Bundle
-  localizedString(forKey:value:table:) 

Instance Method

# localizedString(forKey:value:table:)

Returns a localized version of the string designated by the specified key and residing in the specified table.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.0+macOS 10.0+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func localizedString(
    forKey key: String,
    value: String?,
    table tableName: String?
) -> String
```

## Parameters 

`key`  

The key for a string in the table identified by `tableName`.

`value`  

The value to return if `key` is `nil` or if a localized string for `key` can’t be found in the table.

`tableName`  

The receiver’s string table to search. If `tableName` is `nil` or is an empty string, the method attempts to use the table in `Localizable.strings`.

## Return Value

A localized version of the string designated by `key` in table `tableName`. This method returns the following when key is `nil` or not found in table:

- If `key` is `nil` and `value` is `nil`, returns an empty string.

- If `key` is `nil` and `value` is non-`nil`, returns value.

- If `key` is not found and `value` is `nil` or an empty string, returns `key`.

- If `key` is not found and `value` is non-`nil` and not empty, return `value`.

## Discussion

For more details about string localization and the specification of a `.strings` file, see “String Resources.”

Using the user default `NSShowNonLocalizedStrings`, you can alter the behavior of localizedString(forKey:value:table:) to log a message when the method can’t find a localized string. If you set this default to true (in the global domain or in the application’s domain), then when the method can’t find a localized string in the table, it logs a message to the console and capitalizes `key` before returning it.

The following example cycles through a static array of keys when a button is clicked, gets the value for each key from a strings table named `Buttons.strings`, and sets the button title with the returned value:

```
- (void)changeTitle:(id)sender
{
    static int keyIndex = 0;
    NSBundle *thisBundle = [NSBundle bundleForClass:[self class]];

    NSString *locString = [thisBundle
        localizedStringForKey:assortedKeys[keyIndex++]
        value:@"No translation" table:@"Buttons"];
    [sender setTitle:locString];
    if (keyIndex == MAXSTRINGS) keyIndex=0;
}
```

## See Also

### Related Documentation

class func path(forResource: String?, ofType: String?, inDirectory: String) -> String?

Returns the full pathname for the resource file identified by the specified name and extension and residing in a given bundle directory.

class func paths(forResourcesOfType: String?, inDirectory: String) -> [String]

Returns an array containing the pathnames for all bundle resources having the specified extension and residing in the bundle directory at the specified path.

func paths(forResourcesOfType: String?, inDirectory: String?) -> [String]

Returns an array containing the pathnames for all bundle resources having the specified filename extension and residing in the resource subdirectory.

func path(forResource: String?, ofType: String?, inDirectory: String?) -> String?

Returns the full pathname for the resource identified by the specified name and file extension and located in the specified bundle subdirectory.

func path(forResource: String?, ofType: String?) -> String?

Returns the full pathname for the resource identified by the specified name and file extension.

