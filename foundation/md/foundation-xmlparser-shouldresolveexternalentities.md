

- Foundation
- XMLParser
-  shouldResolveExternalEntities 

Instance Property

# shouldResolveExternalEntities

A Boolean value that determines whether the parser reports declarations of external entities.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.0+macOS 10.0+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
var shouldResolveExternalEntities: Bool { get set }
```

## Discussion

true if the parser reports declarations of external entities, false otherwise. The default value is false. If you set this property to true, you may cause other I/O operations, either network-based or disk-based, to load the external DTD.

The parser reports declarations of external entities with the delegate method parser(_:foundExternalEntityDeclarationWithName:publicID:systemID:).

## See Also

### Managing Parser Behavior

var shouldProcessNamespaces: Bool

A Boolean value that determines whether the parser reports the namespaces and qualified names of elements.

var shouldReportNamespacePrefixes: Bool

A Boolean value that determines whether the parser reports the prefixes indicating the scope of namespace declarations.

