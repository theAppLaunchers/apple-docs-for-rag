

- Foundation
- NSCharacterSet
-  urlPathAllowed 

Type Property

# urlPathAllowed

Returns the character set for characters allowed in a path URL component.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+macOS 10.9+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
class var urlPathAllowed: CharacterSet { get }
```

## Discussion

The path component of a URL is the component immediately following the host component (if present). It ends wherever the query or fragment component begins. For example, in the URL `http://www.example.com/index.php?key1=value1`, the path component is `/index.php`.

## See Also

### Getting Character Sets for URL Encoding

class var urlFragmentAllowed: CharacterSet

Returns the character set for characters allowed in a fragment URL component.

class var urlHostAllowed: CharacterSet

Returns the character set for characters allowed in a host URL subcomponent.

class var urlPasswordAllowed: CharacterSet

Returns the character set for characters allowed in a password URL subcomponent.

class var urlQueryAllowed: CharacterSet

Returns the character set for characters allowed in a query URL component.

class var urlUserAllowed: CharacterSet

Returns the character set for characters allowed in a user URL subcomponent.

