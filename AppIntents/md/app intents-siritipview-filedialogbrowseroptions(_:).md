

- App Intents
- SiriTipView
-  fileDialogBrowserOptions(\_:) 

Instance Method

# fileDialogBrowserOptions(\_:)

On macOS, configures the `fileExporter`, `fileImporter`, or `fileMover` to provide a refined URL search experience: include or exclude hidden files, allow searching by tag, etc.

AppIntentsSwiftUIiOS 17.0+iPadOS 17.0+macOS 14.0+visionOS 1.0+

``` source
nonisolated
func fileDialogBrowserOptions(_ options: FileDialogBrowserOptions) -> some View
```

## Parameters 

`options`  

The search options to apply to a given file dialog.

