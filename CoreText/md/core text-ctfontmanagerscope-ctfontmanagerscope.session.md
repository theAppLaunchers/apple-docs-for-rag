

- Core Text
- CTFontManagerScope
-  CTFontManagerScope.session 

Case

# CTFontManagerScope.session

The font is available to the current user session but won’t be available in subsequent sessions.

macOS 10.6+

``` source
case session
```

## See Also

### Constants

case none

No scope is defined.

case process

The font is available to the current process for the duration of the process unless directly unregistered.

case persistent

The font is available to all processes for the current user session and will be available in subsequent sessions unless unregistered.

static var user: CTFontManagerScope

The font is available to all processes for the current user session and will be available in subsequent sessions unless unregistered.

