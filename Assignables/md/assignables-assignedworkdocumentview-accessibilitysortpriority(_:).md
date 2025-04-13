

- Assignables
- AssignedWorkDocumentView
-  accessibilitySortPriority(\_:) 

Instance Method

# accessibilitySortPriority(\_:)

Sets the sort priority order for this view’s accessibility element, relative to other elements at the same level.

AssignablesSwiftUIiOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 11.0+tvOS 14.0+visionOSwatchOS 7.0+

``` source
nonisolated
func accessibilitySortPriority(_ sortPriority: Double) -> ModifiedContent
```

## Discussion

Higher numbers are sorted first. The default sort priority is zero.

