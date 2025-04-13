

- RealityKit
- ObjectCapturePointCloudView
-  searchCompletion(\_:) 

Instance Method

# searchCompletion(\_:)

Associates a search token with the value of this view when used as a search suggestion.

RealityKitSwiftUIiOS 16.0+iPadOS 16.0+macOS 13.0+

``` source
nonisolated
func searchCompletion(_ token: T) -> some View where T : Identifiable
```

## Parameters 

`token`  

Data to use as the view’s completion.

## Discussion

Use this method to associate a search token with a view that is within a search suggestion list context. The system uses this value when the view is selected to replace the partial text being currently edited of the associated search field.

```
enum FruitToken: Hashable, Identifiable, CaseIterable {
    case apple
    case pear
    case banana

    var id: Self { self }
}

@State private var text = ""
@State private var tokens: [FruitToken] = []

SearchPlaceholderView()
    .searchable(text: $text, tokens: $tokens) { token in
        switch token {
        case .apple: Text("Apple")
        case .pear: Text("Pear")
        case .banana: Text("Banana")
        }
    }
    .searchSuggestions {
        Text("🍎").searchCompletion(FruitToken.apple)
        Text("🍐").searchCompletion(FruitToken.pear)
        Text("🍌").searchCompletion(FruitToken.banana)
    }
```

