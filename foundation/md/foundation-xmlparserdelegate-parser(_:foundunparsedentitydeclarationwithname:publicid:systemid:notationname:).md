

- Foundation
- XMLParserDelegate
-  parser(\_:foundUnparsedEntityDeclarationWithName:publicID:systemID:notationName:) 

Instance Method

# parser(\_:foundUnparsedEntityDeclarationWithName:publicID:systemID:notationName:)

Sent by a parser object to its delegate when it encounters an unparsed entity declaration.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.0+macOS 10.0+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
optional func parser(
    _ parser: XMLParser,
    foundUnparsedEntityDeclarationWithName name: String,
    publicID: String?,
    systemID: String?,
    notationName: String?
)
```

## Parameters 

`parser`  

An `NSXMLParser` object parsing XML.

`name`  

A string that is the name of the unparsed entity in the declaration.

`publicID`  

A string specifying the public ID associated with the entity `name`.

`systemID`  

A string specifying the system ID associated with the entity `name`.

`notationName`  

A string specifying a notation of the declaration of entity `name`.

## See Also

### Related Documentation

func parser(XMLParser, resolveExternalEntityName: String, systemID: String?) -> Data?

Sent by a parser object to its delegate when it encounters a given external entity with a specific system ID.

### Handling the DTD

func parser(XMLParser, foundAttributeDeclarationWithName: String, forElement: String, type: String?, defaultValue: String?)

Sent by a parser object to its delegate when it encounters a declaration of an attribute that is associated with a specific element.

func parser(XMLParser, foundElementDeclarationWithName: String, model: String)

Sent by a parser object to its delegate when it encounters a declaration of an element with a given model.

func parser(XMLParser, foundExternalEntityDeclarationWithName: String, publicID: String?, systemID: String?)

Sent by a parser object to its delegate when it encounters an external entity declaration.

func parser(XMLParser, foundInternalEntityDeclarationWithName: String, value: String?)

Sent by a parser object to the delegate when it encounters an internal entity declaration.

func parser(XMLParser, foundNotationDeclarationWithName: String, publicID: String?, systemID: String?)

Sent by a parser object to its delegate when it encounters a notation declaration.

