

- AppKit
- NSSearchFieldCell
-  recentSearches 

Instance Property

# recentSearches

An array of the recent search strings to display in the pop-up icon menu of the search field.

macOS

``` source
@MainActor
var recentSearches: [String]! { get set }
```

## Discussion

This property contains an array of NSString objects, each of which contains a search string either displayed in the search menu or from a recent autosave archive. If there have been no recent searches and no prior searches saved under an autosave name, this array may be empty. When loading your interface, you might set the value of this property to a set of saved search strings.

## See Also

### Managing recent search strings

var maximumRecents: Int

The maximum number of search strings that can appear in the search menu.

var recentsAutosaveName: NSSearchField.RecentsAutosaveName?

The autosave name under which the search field automatically saves the list of recent search strings.

