

- UIKit
- UISearchTextFieldDelegate
-  searchTextField(\_:itemProviderForCopying:) 

Instance Method

# searchTextField(\_:itemProviderForCopying:)

Asks the delegate for an object that can provide a token when the copied token is pasted.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.1+visionOS 1.0+

``` source
@MainActor
optional func searchTextField(
    _ searchTextField: UISearchTextField,
    itemProviderForCopying token: UISearchToken
) -> NSItemProvider
```

## Parameters 

`searchTextField`  

The search field that contains the token the user is copying or dragging.

`token`  

The token the user is copying or dragging.

## Return Value

An item provider that provides a token if the user pastes or drops the token.

## Discussion

To support drag and drop and the Cut and Copy commands, your delegate must implement this method and return an NSItemProvider for the requested token. Your delegate can provide a plain text representation for pasting in other contexts, but should register a custom type identifier so it can recognize and reconstruct the token when pasted into the same field.

The system only calls this delegate method if either allowsCopyingTokens or allowsDeletingTokens is true.

