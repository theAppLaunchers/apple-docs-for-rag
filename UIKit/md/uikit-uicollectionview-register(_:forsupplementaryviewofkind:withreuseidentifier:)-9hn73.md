

- UIKit
- UICollectionView
-  register(\_:forSupplementaryViewOfKind:withReuseIdentifier:) 

Instance Method

# register(\_:forSupplementaryViewOfKind:withReuseIdentifier:)

Registers a nib file for use in creating supplementary views for the collection view.

iOS 6.0+iPadOS 6.0+Mac Catalyst 13.1+tvOSvisionOS 1.0–1.0Deprecated

``` source
@MainActor
func register(
    _ nib: UINib?,
    forSupplementaryViewOfKind kind: String,
    withReuseIdentifier identifier: String
)
```

## Parameters 

`nib`  

The nib object containing the view object. The nib file must contain only one top-level object and that object must be of the type UICollectionReusableView.

`kind`  

The kind of supplementary view to create. The layout defines the types of supplementary views it supports. The value of this string may correspond to one of the predefined kind strings or to a custom string that the layout added to support a new type of supplementary view. This parameter must not be `nil`.

`identifier`  

The reuse identifier to associate with the specified nib file. This parameter must not be `nil` and must not be an empty string.

## Discussion

Prior to calling the dequeueReusableSupplementaryView(ofKind:withReuseIdentifier:for:) method of the collection view, you must use this method or the register(_:forSupplementaryViewOfKind:withReuseIdentifier:) method to tell the collection view how to create a supplementary view of the given type. If a view of the specified type isn’t currently in a reuse queue, the collection view uses the provided information to create a view object automatically.

If you previously registered a class or nib file with the same element kind and reuse identifier, the class you specify in the `viewClass` parameter replaces the old entry. You may specify `nil` for `nib` if you want to unregister the class from the specified element kind and reuse identifier.

## See Also

### Creating headers and footers

struct SupplementaryRegistration

A registration for the collection view’s supplementary views.

func dequeueConfiguredReusableSupplementary&lt;Supplementary>(using: UICollectionView.SupplementaryRegistration&lt;Supplementary>, for: IndexPath) -> Supplementary

Dequeues a configured reusable supplementary view object.

func register(AnyClass?, forSupplementaryViewOfKind: String, withReuseIdentifier: String)

Registers a class for use in creating supplementary views for the collection view.

func dequeueReusableSupplementaryView(ofKind: String, withReuseIdentifier: String, for: IndexPath) -> UICollectionReusableView

Dequeues a reusable supplementary view located by its identifier and kind.

