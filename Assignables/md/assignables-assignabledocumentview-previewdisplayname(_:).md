

- Assignables
- AssignableDocumentView
-  previewDisplayName(\_:) 

Instance Method

# previewDisplayName(\_:)

Sets a user visible name to show in the canvas for a preview.

AssignablesSwiftUIiOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOSwatchOS 6.0+

``` source
nonisolated
func previewDisplayName(_ value: String?) -> some View
```

## Parameters 

`value`  

A name for the preview.

## Return Value

A preview that uses the given name.

## Discussion

Apply this modifier to a view inside your `PreviewProvider` implementation to associate a display name with that view’s preview:

```
struct CircleImage_Previews: PreviewProvider {
    static var previews: some View {
        CircleImage()
            .previewDisplayName("Circle")
    }
}
```

Add a name when you have multiple previews together in the canvas that you need to tell apart. The default value is `nil`, in which case Xcode displays a default string.

