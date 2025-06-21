*   [SwiftUI](/documentation/swiftui)
*   [Landmarks: Building an app with Liquid Glass](/documentation/swiftui/landmarks-building-an-app-with-liquid-glass)
*   Landmarks: Displaying custom activity badges Beta

Sample Code

# Landmarks: Displaying custom activity badges

Provide people with a way to mark their adventures by displaying animated custom activity badges.

[Download](https://docs-assets.developer.apple.com/published/10d19597bd72/LandmarksBuildingAnAppWithLiquidGlass.zip)

iOS 26.0+BetaiPadOS 26.0+BetamacOS 26.0+BetaXcode 26.0+Beta

## [Overview](/documentation/SwiftUI/Landmarks-Displaying-custom-activity-badges#Overview)

The Landmarks app lets people track their adventures as they explore sites around the world. Whether it’s a national park near their home or a far-flung location on a different continent, the app provides a way for people to mark their adventures and receive custom activity badges along the way.

![An image of the landmarks view on an iPhone, with the badges view visible over some landmarks.](https://docs-assets.developer.apple.com/published/ca44bff06ffc2b55dd82e9778ef5c3b6/Landmarks-Building-an-app-with-Liquid-Glass-5%402x.png)

This sample displays the badges in a vertical view that includes a toggle button for showing or hiding the badges. The Landmarks app includes a custom modifier that makes it easier for other views to adopt the badge view. By configuring the badges to use Liquid Glass, the badges gain the advantage of using the morphing animation when you show or hide the badges.

## [Add a modifier to show badges in other views](/documentation/SwiftUI/Landmarks-Displaying-custom-activity-badges#Add-a-modifier-to-show-badges-in-other-views)

To make the badges available in other views, like `CollectionsView`, the sample uses a custom modifier, `ShowBadgesViewModifier`, as a [`ViewModifier`](/documentation/swiftui/viewmodifier). The sample layers the badges over another view using a [`ZStack`](/documentation/swiftui/zstack), and positions the badge view in the lower trailing corner:

```swift

```swift
private struct ShowsBadgesViewModifier: ViewModifier {
    func body(content: Content) -> some View {
        ZStack {
            content
            HStack {
                Spacer()
                VStack {
                    Spacer()
                    BadgesView()
                        .padding()
                }
            }
        }
    }
}
```

```

The sample extends [`View`](/documentation/swiftui/view) by adding the `showBadges` modifier:

```swift

```swift
extension View {
    func showsBadges() -> some View {
        modifier(ShowsBadgesViewModifier())
    }
}
```

```

## [Apply Liquid Glass to the toggle button](/documentation/SwiftUI/Landmarks-Displaying-custom-activity-badges#Apply-Liquid-Glass-to-the-toggle-button)

To create the toggle button, the sample configures a [`Button`](/documentation/swiftui/button) using `ToggleBadgesLabel` which has different system images for the Show and Hide toggle states. To apply Liquid Glass, style the button with the [`glass`](/documentation/swiftui/primitivebuttonstyle/glass) modifier:

```

```
Button {
    //...
} label: {
    //...
}
.buttonStyle(.glass)
```

```

## [Add Liquid Glass to the badges](/documentation/SwiftUI/Landmarks-Displaying-custom-activity-badges#Add-Liquid-Glass-to-the-badges)

To add Liquid Glass to each badge, the sample uses the [`glassEffect(_:in:isEnabled:)`](/documentation/swiftui/view/glasseffect\(_:in:isenabled:\)) modifier. To make a custom glass view appearance, the sample specifies a rectangular option with a corner radius:

```

```
BadgeLabel(badge: $0)
    .glassEffect(.regular, in: .rect(cornerRadius: Constants.badgeCornerRadius))
```

```

## [Animate the badges using the morph effect](/documentation/SwiftUI/Landmarks-Displaying-custom-activity-badges#Animate-the-badges-using-the-morph-effect)

The morph effect is an animation for Liquid Glass views. During this animation, the toggle button and each badge start as a combined view. Then, the button and badges change shape like a liquid as they separate and move from one location to another. In reverse, the toggle button and badges change shape and combine back into one view.

To achieve the Liquid Glass morph effect, the app:

*   organizes the badges and toggle button into a [`GlassEffectContainer`](/documentation/swiftui/glasseffectcontainer)
    
*   adds [`glassEffectID(_:in:)`](/documentation/swiftui/view/glasseffectid\(_:in:\)) to each badge
    
*   adds [`glassEffectID(_:in:)`](/documentation/swiftui/view/glasseffectid\(_:in:\)) to the toggle button
    
*   wraps the command that toggles the `isExpanded` property in [`withAnimation(_:_:)`](/documentation/swiftui/withanimation\(_:_:\))
    

```

```
// Organizes the badges and toggle button to animate together.
GlassEffectContainer(spacing: Constants.badgeGlassSpacing) {
    VStack(alignment: .center, spacing: Constants.badgeButtonTopSpacing) {
        if isExpanded {
            VStack(spacing: Constants.badgeSpacing) {
                ForEach(modelData.earnedBadges) {
                    BadgeLabel(badge: $0)
                        // Adds Liquid Glass to the badge.
                        .glassEffect(.regular, in: .rect(cornerRadius: Constants.badgeCornerRadius))
                        // Adds an identifier to the badge for animation.
                        .glassEffectID($0.id, in: namespace)
                }
            }
        }
        Button {
            // Animates this button and badges when `isExpanded` changes values.
            withAnimation {
                isExpanded.toggle()
            }
        } label: {
            ToggleBadgesLabel(isExpanded: isExpanded)
                .frame(width: Constants.badgeShowHideButtonWidth,
                       height: Constants.badgeShowHideButtonHeight)
        }
        // Adds Liquid Glass to the button.
        .buttonStyle(.glass)
        #if os(macOS)
        .tint(.clear)
        #endif
        // Adds an identifier to the button for animation.
        .glassEffectID("togglebutton", in: namespace)
    }
    .frame(width: Constants.badgeFrameWidth)
}
```

```

## [See Also](/documentation/SwiftUI/Landmarks-Displaying-custom-activity-badges#see-also)

### [App features](/documentation/SwiftUI/Landmarks-Displaying-custom-activity-badges#App-features)

[

Landmarks: Applying a background extension effect](/documentation/swiftui/landmarks-applying-a-background-extension-effect)

Configure an image to blur and extend under a sidebar or inspector panel.

[

Landmarks: Extending horizontal scrolling under a sidebar or inspector](/documentation/swiftui/landmarks-extending-horizontal-scrolling-under-a-sidebar-or-inspector)

Improve your horizontal scrollbar’s appearance by extending it under a sidebar or inspector.

[

Landmarks: Refining the system provided Liquid Glass effect in toolbars](/documentation/swiftui/landmarks-refining-the-system-provided-glass-effect-in-toolbars)

Organize toolbars into related groupings to improve their appearance and utility.

Beta Software

This documentation contains preliminary information about an API or technology in development. This information is subject to change, and software implemented according to this documentation should be tested with final operating system software.

[Learn more about using Apple's beta software](https://developer.apple.com/support/beta-software/)