

- Foundation
- XMLElement
-  elements(forName:) 

Instance Method

# elements(forName:)

Returns the child element nodes (as `NSXMLElement` objects) of the receiver that have a specified name.

Mac Catalyst 13.0+macOS 10.0+

``` source
func elements(forName name: String) -> [XMLElement]
```

## Parameters 

`name`  

A string specifying the name of the child element nodes to find and return. If `name` is a qualified name, then this method invokes elements(forLocalName:uri:) with the URI parameter set to the URI associated with the prefix. Otherwise comparison is based on string equality of the qualified or non-qualified name.

## Return Value

An array of of `NSXMLElement` objects or an empty array if no matching children can be found.

## See Also

### Obtaining Child Elements

func elements(forLocalName: String, uri: String?) -> [XMLElement]

Returns the child element nodes (as `NSXMLElement` objects) of the receiver that are matched with the specified local name and URI.

