

- ManagedAppDistribution
- ManagedContentView
-  typeSelectEquivalent(\_:) 

Instance Method

# typeSelectEquivalent(\_:)

Sets an explicit type select equivalent text in a collection, such as a list or table.

ManagedAppDistributionSwiftUIiOS 16.0+iPadOS 16.0+macOS 13.0+tvOS 16.0+watchOS 9.0+

``` source
nonisolated
func typeSelectEquivalent(_ text: Text?) -> some View
```

## Parameters 

`text`  

The explicit text value to use as a type select equivalent for a view in a collection.

## Discussion

By default, a type select equivalent is automatically derived from any `Text` or `TextField` content in a list or table. In the below example, type select can be used to select a person, even though no explicit value has been set.

```
List(people, selection: $selectedPersonID) { person in
    Label {
        Text(person.name)
    } icon: {
        person.avatar
    }
}
```

An explicit type select value should be set when there is no textual content or when a different value is desired compared to what’s displayed in the view. Explicit values also provide a more performant for complex view types. In the below example, type select is explicitly set to allow selection of views that otherwise only display an image.

```
List(people, selection: $selectedPersonID) { person in
    person.avatar
        .accessibilityLabel(person.name)
        .typeSelectEquivalent(person.name)
}
```

Setting an empty string value disables text selection for the view, and a value of `nil` results in the view using its default value.

