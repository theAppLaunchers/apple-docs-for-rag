

- MusicKit
- ArtworkImage
-  exportsItemProviders(\_:onExport:onEdit:) 

Instance Method

# exportsItemProviders(\_:onExport:onEdit:)

Exports a read-write item provider for consumption by shortcuts, quick actions, and services.

MusicKitSwiftUImacOS 12.0+

``` source
nonisolated
func exportsItemProviders(
    _ contentTypes: [UTType],
    onExport: @escaping () -> [NSItemProvider],
    onEdit: @escaping ([NSItemProvider]) -> Bool
) -> some View
```

## Parameters 

`contentTypes`  

The types of content that the view supports exporting and importing. An empty array means the view does not currently support exporting.

`onExport`  

A closure that will be called on request of the items by the shortcut or service.

`onEdit`  

A closure that will be called after the shortcut or service completes with its output data. This should replace the selected subpart that was exported with `onExport`. Return `false` to indicate that there was a failure to receive the items.

## Discussion

If the associated view supports selection, the exported item should reflect that selected subpart.

