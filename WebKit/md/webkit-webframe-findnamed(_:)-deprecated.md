

- WebKit
- WebFrame
-  findNamed(\_:) Deprecated

Instance Method

# findNamed(\_:)

Returns a web frame that matches the given name.

macOS 10.3–10.14Deprecated

``` source
func findNamed(_ name: String!) -> WebFrame!
```

## Parameters 

`name`  

The name of a frame.

## Return Value

For predefined names, returns the receiver if name is “\_self” or “\_current”, returns the receiver’s parent frame if name is “\_parent”, and returns the main frame if name is “\_top”. Also returns the receiver if it is the main frame and name is either “\_parent” or “\_top.” For other names, this method returns the first frame that matches `name`. Returns `nil` if no match is found.

## Discussion

This method searches the receiver and its descendants first, then the receiver’s parent and its children moving up the hierarchy until a match is found. If no match is found in the receivers hierarchy, this method will search for a matching frame in other main frame hierarchies.

## See Also

### Finding Frames

var name: String!

The web frame’s name.

Deprecated

