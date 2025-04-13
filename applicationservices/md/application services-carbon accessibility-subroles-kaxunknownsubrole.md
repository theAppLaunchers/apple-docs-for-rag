

- Application Services
- Carbon Accessibility
- Subroles
-  kAXUnknownSubrole 

Global Variable

# kAXUnknownSubrole

macOS 10.2+

``` source
var kAXUnknownSubrole: String { get }
```

## Discussion

A subrole for an unknown type of window. A window should include a subrole to further define its type. If your window does not conform to an existing subrole, you can use the unknown subrole. Alternatively, you can return the `eventNotHandledErr` error when your window is asked for its subrole.

