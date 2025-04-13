

- System
- FilePath
-  removingLastComponent() 

Instance Method

# removingLastComponent()

Creates a new path with everything up to but not including `lastComponent`.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

``` source
func removingLastComponent() -> FilePath
```

## Discussion

If the path only contains a root, returns `self`. If the path has no root and only includes a single component, returns an empty FilePath.

Examples:

- Unix:

  - `/usr/bin/ls => /usr/bin`

  - `/foo => /`

  - `/ => /`

  - `foo => ""`

- Windows:

  - `C:\foo\bar.exe => C:\foo`

  - `C:\ => C:\`

  - `\\server\share\folder\file.txt => \\server\share\folder`

  - `\\server\share\ => \\server\share\`

