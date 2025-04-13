

- UIKit
- UIEditMenuInteractionDelegate
-  editMenuInteraction(\_:targetRectFor:) 

Instance Method

# editMenuInteraction(\_:targetRectFor:)

Provides the target rectangle to position the menu relative to when the interaction begins or requires an update.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+visionOS 1.0+

``` source
@MainActor
optional func editMenuInteraction(
    _ interaction: UIEditMenuInteraction,
    targetRectFor configuration: UIEditMenuConfiguration
) -> CGRect
```

## Parameters 

`interaction`  

The interaction object triggering the menu.

`configuration`  

The object containing the configuration details for the menu.

## Return Value

Returns a rectangle relative to the edit menu interaction’s view. Return CGRectNull to use the default rectangle.

## Discussion

UIKit calls this method when the interaction begins or requires an update for the position of the menu when calling updateVisibleMenuPosition(animated:). The menu displays around the target rectangle you provide, space permitting, with the menu pointing in the direction the configuration specifies. When not implemented, the default is an empty rectangle centered at configuration.sourcePoint. Return CGRectNull to use the default rect.

The following example provides the frame of the subview as the target rectangle for the interaction.

```
func editMenuInteraction(_ interaction: UIEditMenuInteraction, targetRectFor configuration: UIEditMenuConfiguration) -> CGRect {
    guard let selectedShapeView = shapeView(at: configuration.sourcePoint) else {
        return .null // Uses the default implementation.
    }

    return selectedShapeView.frame
}
```

## See Also

### Customizing the Menu

func editMenuInteraction(UIEditMenuInteraction, menuFor: UIEditMenuConfiguration, suggestedActions: [UIMenuElement]) -> UIMenu?

Provides the menu to use when the interaction begins or requires an update.

func editMenuInteraction(UIEditMenuInteraction, willPresentMenuFor: UIEditMenuConfiguration, animator: any UIEditMenuInteractionAnimating)

Informs the delegate when the interaction is about to present the menu.

func editMenuInteraction(UIEditMenuInteraction, willDismissMenuFor: UIEditMenuConfiguration, animator: any UIEditMenuInteractionAnimating)

Informs the delegate when the interaction is about to dismiss the menu.

protocol UIEditMenuInteractionAnimating

Methods adopted by system-supplied animator objects when interacting with menus.

