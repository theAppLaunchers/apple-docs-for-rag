

- Foundation
- Bundle
-  loadNibNamed(\_:owner:options:) 

Instance Method

# loadNibNamed(\_:owner:options:)

Unarchives the contents of a nib file located in the receiver’s bundle.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.0+tvOS 9.0+visionOS 1.0–1.0Deprecated

``` source
func loadNibNamed(
    _ name: String,
    owner: Any?,
    options: [UINib.OptionsKey : Any]? = nil
) -> [Any]?
```

## Parameters 

`name`  

The name of the nib file, which need not include the `.nib` extension.

`owner`  

The object to assign as the nib’s File’s Owner object.

`options`  

A dictionary containing the options to use when opening the nib file. For a list of available keys for this dictionary, see `UIKit Nib Loading Options`.

## Return Value

An array containing the top-level objects in the nib file. The array does not contain references to the File’s Owner or any proxy objects; it contains only those objects that were instantiated when the nib file was unarchived. You should retain either the returned array or the objects it contains manually to prevent the nib file objects from being released prematurely.

## Discussion

You can use this method to load user interfaces and make the objects available to your code. During the loading process, this method unarchives each object, initializes it, sets its properties to their configured values, and reestablishes any connections to other objects. (To establish outlet connections, this method uses the `setValue:forKey:` method, which may cause the object in the outlet to be retained automatically.) For detailed information about the nib-loading process, see Resource Programming Guide.

If the nib file contains any proxy objects beyond just the File’s Owner proxy object, you can specify the runtime replacement objects for those proxies using the options dictionary. In that dictionary, add the `UINibExternalObjects` key and set its value to a dictionary containing the names of any proxy objects (the keys) and the real objects to use in their place. The proxy object’s name is the string you assign to it in the Identifier field of the Interface Builder inspector window.

## See Also

### Loading Nib Files

func loadNibNamed(NSNib.Name, owner: Any?, topLevelObjects: AutoreleasingUnsafeMutablePointer&lt;NSArray?>?) -> Bool

Loads a nib from the bundle with the specified file name and owner.

