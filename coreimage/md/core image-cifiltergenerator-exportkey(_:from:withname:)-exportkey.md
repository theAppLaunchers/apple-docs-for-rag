

- Core Image
- CIFilterGenerator
-  exportKey(\_:from:withName:) 

Instance Method

# exportKey(\_:from:withName:)

Exports an input or output key of an object in the filter chain.

macOS 10.5+

``` source
func exportKey(
    _ key: String,
    from targetObject: Any,
    withName exportedKeyName: String?
)
```

## Parameters 

`key`  

The key to export from the target object (for example, `inputImage`).

`targetObject`  

The object associated with the key (for example, the filter).

`exportedKeyName`  

A unique name to use for the exported key. Pass `nil` to use the original key name.

## Discussion

When you create a CIFilter object from a `CIFilterGenerator` object, you might want the filter client to be able to set some of the parameters associated with the filter chain. You can make a parameter settable by exporting the key associated with the parameter. If the exported key represents an input parameter of the filter, the key is exported as an input key. If the key represents an output parameter, it is exported as an output key.

## See Also

### Managing Exported Keys

var exportedKeys: [AnyHashable : Any]

Returns an array of the exported keys.

func removeExportedKey(String)

Removes a key that was previously exported.

func setAttributes([AnyHashable : Any], forExportedKey: String)

Sets a dictionary of attributes for an exported key.

