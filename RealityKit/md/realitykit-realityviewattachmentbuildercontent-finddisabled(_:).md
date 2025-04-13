

- RealityKit
- RealityViewAttachmentBuilderContent
-  findDisabled(\_:) 

Instance Method

# findDisabled(\_:)

Prevents find and replace operations in a text editor.

RealityKitSwiftUIiOS 16.0+iPadOS 16.0+visionOS

``` source
nonisolated
func findDisabled(_ isDisabled: Bool = true) -> some View
```

## Parameters 

`isDisabled`  

A Boolean value that indicates whether to disable the find and replace interface for a text editor.

## Return Value

A view that disables the find and replace interface.

## Discussion

Add this modifier to ensure that people can’t activate the find and replace interface for a `TextEditor`:

```
TextEditor(text: $text)
    .findDisabled()
```

When you disable the find operation, you also implicitly disable the replace operation. If you want to only disable replace, use `View/replaceDisabled(_:)` instead.

Using this modifer also prevents programmatic find and replace interface presentation using the `View/findNavigator(isPresented:)` method. Be sure to place the disabling modifier closer to the text editor for this to work:

```
TextEditor(text: $text)
    .findDisabled(isDisabled)
    .findNavigator(isPresented: $isPresented)
```

If you apply this modifer at multiple levels of a view hierarchy, the call closest to the text editor takes precedence. For example, people can activate find and replace for the first text editor in the following example, but not the second:

```
VStack {
    TextEditor(text: $text1)
        .findDisabled(false)
    TextEditor(text: $text2)
}
.findDisabled(true)
```

