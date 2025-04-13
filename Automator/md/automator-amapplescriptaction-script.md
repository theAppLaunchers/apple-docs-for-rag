

- Automator
- AMAppleScriptAction
-  script 

Instance Property

# script

An `OSAScript` object representing the receiver’s script containing the `on run` command handler.

Mac Catalyst 14.0+macOS 10.4+

``` source
@NSCopying
var script: OSAScript? { get set }
```

## Discussion

By default, `script` is `main.applescript`, which is stored in the action bundle. You can use `setScript:` to set the receiver’s script to `newScript`, where `newScript` must be an `OSAScript` object that could be instantiated from a script in the action bundle. `script` must contain the `on run` command handler.

