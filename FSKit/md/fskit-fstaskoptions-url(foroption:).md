

- FSKit
- FSTaskOptions
-  url(forOption:) 

Instance Method

# url(forOption:)

Retrieves a URL for a given option.

macOS 15.4+

``` source
func url(forOption option: String) -> URL?
```

## Parameters 

`option`  

The option for which to retrieve the URL. This value doesn’t include leading dashes.

## Discussion

Some command-line options refer to paths that indicate a location in which the module needs access to a file outside of its container. FSKit passes these paths as a URL tagged by the option name.

For example, `"-B" "./someFile"` returns the URL for `./someFile` when passed an option `"B"`. To indicate that your module treats a given option as a path, include it in the `pathOptions` dictionary within a command options dictionary (`FSActivatOptionSyntax`, `FSCheckOptionSyntax`, or `FSFormatOptionSyntax`). This dictionary uses the command option name as a key, and each entry has a value indicating what kind of entry to create.

