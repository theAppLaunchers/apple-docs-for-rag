

- PackageDescription
- CSetting
-  headerSearchPath(\_:\_:) 

Type Method

# headerSearchPath(\_:\_:)

Provides a header search path relative to the target’s directory.

SwiftPM 5.0+

``` source
static func headerSearchPath(
    _ path: String,
    _ condition: BuildSettingCondition? = nil
) -> CSetting
```

## Parameters 

`path`  

The path of the directory that contains the headers. The path is relative to the target’s directory.

`condition`  

A condition that restricts the use of the build setting.

## Discussion

Use this setting to add a search path for headers within your target. You can’t use absolute paths and you can’t use this setting to provide headers that are visible to other targets.

The path must be a directory inside the package.

Since

First available in PackageDescription 5.0.

## See Also

### Configuring C Settings

static func define(String, to: String?, BuildSettingCondition?) -> CSetting

Defines a value for a macro.

static func unsafeFlags([String], BuildSettingCondition?) -> CSetting

Sets unsafe flags to pass arbitrary command-line flags to the corresponding build tool.

