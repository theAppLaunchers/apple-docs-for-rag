

- AppKit
- NSNib
-  init(nibNamed:bundle:) 

Initializer

# init(nibNamed:bundle:)

Returns an `NSNib` object initialized to the nib file in the specified bundle.

macOS

``` source
init?(
    nibNamed nibName: NSNib.Name,
    bundle: Bundle?
)
```

## Parameters 

`nibName`  

The name of the nib file, without any leading path information. Inclusion of the `.nib` extension on the nib file name is optional.

`bundle`  

The bundle in which to search for the nib file. If you specify `nil`, this method looks for the nib file in the main bundle.

## Return Value

The initialized `NSNib` object or `nil` if there were errors during initialization or the nib file could not be located.

## Discussion

The `NSNib` object looks for the nib file in the bundle’s language-specific project directories first, followed by the `Resources` directory.

After the nib file has been loaded, the `NSNib` object uses the bundle’s resource map to locate additional resources referenced by the nib. If you specified `nil` for the `bundle` parameter, the `NSNib` object looks for those resources in the bundle associated with the class of the nib file’s owner instead. If the nib file does not have an owner, the `NSNib` object looks for additional resources in the application’s main bundle.

## See Also

### Initializing a Nib

init(nibData: Data, bundle: Bundle?)

Initializes an instance with nib data and specified bundle for locating resources.

typealias Name

