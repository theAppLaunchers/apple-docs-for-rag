

- FamilyControls
- FamilyActivityPicker
-  View Modifiers 

API Collection

# View Modifiers

Apply standard modifiers to configure the family activity picker view and the views it contains.

## Overview

Every type that conforms to the View protocol gains access to the set of view modifiers defined by that protocol. For information about using view modifiers, see Configuring views.

## Topics

### Accessibility Labels

func accessibilityLabel&lt;S>(S) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

Adds a label to the view that describes its contents.

func accessibilityLabel(Text) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

Adds a label to the view that describes its contents.

func accessibilityLabel(LocalizedStringKey) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

Adds a label to the view that describes its contents.

func accessibilityInputLabels([LocalizedStringKey]) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

Sets alternate input labels with which users identify a view.

func accessibilityInputLabels([Text]) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

Sets alternate input labels with which users identify a view.

func accessibilityInputLabels&lt;S>([S]) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

Sets alternate input labels with which users identify a view.

func accessibilityLabeledPair&lt;ID>(role: AccessibilityLabeledPairRole, id: ID, in: Namespace.ID) -> some View

Pairs an accessibility element representing a label with the element for the matching content.

### Accessibility Values

func accessibilityValue&lt;S>(S) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

Adds a textual description of the value that the view contains.

func accessibilityValue(LocalizedStringKey) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

Adds a textual description of the value that the view contains.

func accessibilityValue(Text) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

Adds a textual description of the value that the view contains.

### Accessibility Hints

func accessibilityHint(Text) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

Communicates to the user what happens after performing the view’s action.

func accessibilityHint(LocalizedStringKey) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

Communicates to the user what happens after performing the view’s action.

func accessibilityHint&lt;S>(S) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

Communicates to the user what happens after performing the view’s action.

### Accessibility Actions

func accessibilityAction(AccessibilityActionKind, () -> Void) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

Adds an accessibility action to the view. Actions allow assistive technologies, such as the VoiceOver, to interact with the view by invoking the action.

func accessibilityAction&lt;S>(named: S, () -> Void) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

Adds an accessibility action to the view. Actions allow assistive technologies, such as the VoiceOver, to interact with the view by invoking the action.

func accessibilityAction(named: Text, () -> Void) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

Adds an accessibility action to the view. Actions allow assistive technologies, such as the VoiceOver, to interact with the view by invoking the action.

func accessibilityAction(named: LocalizedStringKey, () -> Void) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

Adds an accessibility action to the view. Actions allow assistive technologies, such as the VoiceOver, to interact with the view by invoking the action.

func accessibilityAction&lt;Label>(action: () -> Void, label: () -> Label) -> some View

Adds an accessibility action to the view. Actions allow assistive technologies, such as the VoiceOver, to interact with the view by invoking the action.

func accessibilityAdjustableAction((AccessibilityAdjustmentDirection) -> Void) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

Adds an accessibility adjustable action to the view. Actions allow assistive technologies, such as the VoiceOver, to interact with the view by invoking the action.

func accessibilityScrollAction((Edge) -> Void) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

Adds an accessibility scroll action to the view. Actions allow assistive technologies, such as the VoiceOver, to interact with the view by invoking the action.

### Accessibility Activation Point

func accessibility(activationPoint: CGPoint) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

Specifies the point where activations occur in the view.

func accessibility(activationPoint: UnitPoint) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

Specifies the unit point where activations occur in the view.

func accessibilityActivationPoint(CGPoint) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

The activation point for an element is the location assistive technologies use to initiate gestures.

func accessibilityActivationPoint(UnitPoint) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

The activation point for an element is the location assistive technologies use to initiate gestures.

### Accessibility Elements

func accessibilityElement(children: AccessibilityChildBehavior) -> some View

Creates a new accessibility element, or modifies the `AccessibilityChildBehavior` of the existing accessibility element.

func accessibilityChildren&lt;V>(children: () -> V) -> some View

Replaces the existing accessibility element’s children with one or more new synthetic accessibility elements.

func accessibilityHidden(Bool) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

Specifies whether to hide this view from system accessibility features.

### Accessibility Custom Controls

func accessibilityRepresentation&lt;V>(representation: () -> V) -> some View

Replaces one or more accessibility elements for this view with new accessibility elements.

func accessibilityRespondsToUserInteraction(Bool) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

Explicitly set whether this Accessibility element responds to user interaction and would thus be interacted with by technologies such as Switch Control, Voice Control or Full Keyboard Access.

### Accessibility Custom Content

func accessibilityCustomContent(LocalizedStringKey, Text, importance: AXCustomContent.Importance) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

Add additional accessibility information to the view.

func accessibilityCustomContent(AccessibilityCustomContentKey, Text?, importance: AXCustomContent.Importance) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

Add additional accessibility information to the view.

func accessibilityCustomContent(AccessibilityCustomContentKey, LocalizedStringKey, importance: AXCustomContent.Importance) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

Add additional accessibility information to the view.

func accessibilityCustomContent&lt;V>(AccessibilityCustomContentKey, V, importance: AXCustomContent.Importance) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

Add additional accessibility information to the view.

func accessibilityCustomContent(Text, Text, importance: AXCustomContent.Importance) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

Add additional accessibility information to the view.

func accessibilityCustomContent(LocalizedStringKey, LocalizedStringKey, importance: AXCustomContent.Importance) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

Add additional accessibility information to the view.

func accessibilityCustomContent&lt;V>(LocalizedStringKey, V, importance: AXCustomContent.Importance) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

Add additional accessibility information to the view.

### Accessibility Navigation

func accessibilityRotor&lt;Content>(Text, entries: () -> Content) -> some View

Create an Accessibility Rotor with the specified user-visible label, and entries generated from the content closure.

func accessibilityRotor&lt;L, Content>(L, entries: () -> Content) -> some View

Create an Accessibility Rotor with the specified user-visible label, and entries generated from the content closure.

func accessibilityRotor&lt;Content>(LocalizedStringKey, entries: () -> Content) -> some View

Create an Accessibility Rotor with the specified user-visible label, and entries generated from the content closure.

func accessibilityRotor&lt;Content>(AccessibilitySystemRotor, entries: () -> Content) -> some View

Create an Accessibility Rotor replacing the specified system-provided Rotor.

func accessibilityRotor&lt;L, EntryModel, ID>(L, entries: [EntryModel], entryID: KeyPath&lt;EntryModel, ID>, entryLabel: KeyPath&lt;EntryModel, String>) -> some View

Create an Accessibility Rotor with the specified user-visible label and entries.

func accessibilityRotor&lt;EntryModel, ID>(Text, entries: [EntryModel], entryID: KeyPath&lt;EntryModel, ID>, entryLabel: KeyPath&lt;EntryModel, String>) -> some View

Create an Accessibility Rotor with the specified user-visible label and entries.

func accessibilityRotor&lt;EntryModel, ID>(LocalizedStringKey, entries: [EntryModel], entryID: KeyPath&lt;EntryModel, ID>, entryLabel: KeyPath&lt;EntryModel, String>) -> some View

Create an Accessibility Rotor with the specified user-visible label and entries.

func accessibilityRotor&lt;EntryModel, ID>(AccessibilitySystemRotor, entries: [EntryModel], entryID: KeyPath&lt;EntryModel, ID>, entryLabel: KeyPath&lt;EntryModel, String>) -> some View

Create an Accessibility Rotor replacing the specified system-provided Rotor.

func accessibilityRotor&lt;EntryModel>(Text, entries: [EntryModel], entryLabel: KeyPath&lt;EntryModel, String>) -> some View

Create an Accessibility Rotor with the specified user-visible label and entries.

func accessibilityRotor&lt;EntryModel>(LocalizedStringKey, entries: [EntryModel], entryLabel: KeyPath&lt;EntryModel, String>) -> some View

Create an Accessibility Rotor with the specified user-visible label and entries.

func accessibilityRotor&lt;EntryModel>(AccessibilitySystemRotor, entries: [EntryModel], entryLabel: KeyPath&lt;EntryModel, String>) -> some View

Create an Accessibility Rotor replacing the specified system-provided Rotor.

func accessibilityRotor&lt;L, EntryModel>(L, entries: [EntryModel], entryLabel: KeyPath&lt;EntryModel, String>) -> some View

Create an Accessibility Rotor with the specified user-visible label and entries.

func accessibilityRotor(Text, textRanges: [Range&lt;String.Index>]) -> some View

Create an Accessibility Rotor with the specified user-visible label and entries for each of the specified ranges. The Rotor will be attached to the current Accessibility element, and each entry will go the specified range of that element.

func accessibilityRotor(AccessibilitySystemRotor, textRanges: [Range&lt;String.Index>]) -> some View

Create an Accessibility Rotor replacing the specified system-provided Rotor. The Rotor will be attached to the current Accessibility element, and each entry will go the specified range of that element.

func accessibilityRotor&lt;L>(L, textRanges: [Range&lt;String.Index>]) -> some View

Create an Accessibility Rotor with the specified user-visible label and entries for each of the specified ranges. The Rotor will be attached to the current Accessibility element, and each entry will go the specified range of that element.

func accessibilityRotor(LocalizedStringKey, textRanges: [Range&lt;String.Index>]) -> some View

Create an Accessibility Rotor with the specified user-visible label and entries for each of the specified ranges. The Rotor will be attached to the current Accessibility element, and each entry will go the specified range of that element.

func accessibilityRotorEntry&lt;ID>(id: ID, in: Namespace.ID) -> some View

Defines an explicit identifier tying an Accessibility element for this view to an entry in an Accessibility Rotor.

func accessibilityLinkedGroup&lt;ID>(id: ID, in: Namespace.ID) -> some View

Links multiple accessibility elements so that the user can quickly navigate from one element to another, even when the elements are not near each other in the accessibility hierarchy.

func accessibilitySortPriority(Double) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

Sets the sort priority order for this view’s accessibility element, relative to other elements at the same level.

### Accessibility Focus

func accessibilityFocused(AccessibilityFocusState&lt;Bool>.Binding) -> some View

Modifies this view by binding its accessibility element’s focus state to the given boolean state value.

func accessibilityFocused&lt;Value>(AccessibilityFocusState&lt;Value>.Binding, equals: Value) -> some View

Modifies this view by binding its accessibility element’s focus state to the given state value.

### Accessibility Traits

func accessibilityAddTraits(AccessibilityTraits) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

Adds the given traits to the view.

func accessibilityRemoveTraits(AccessibilityTraits) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

Removes the given traits from this view.

### Accessibility Identity

func accessibilityIdentifier(String) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

Uses the string you specify to identify the view.

### Accessibility Color Inversion

func accessibilityIgnoresInvertColors(Bool) -> some View

Sets whether this view should ignore the system Smart Invert setting.

### Accessibility Content Descriptions

func accessibilityTextContentType(AccessibilityTextContentType) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

Sets an accessibility text content type.

func accessibilityHeading(AccessibilityHeadingLevel) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

Sets the accessibility level of this heading.

### VoiceOver

func speechAdjustedPitch(Double) -> some View

Raises or lowers the pitch of spoken text.

func speechAlwaysIncludesPunctuation(Bool) -> some View

Sets whether VoiceOver should always speak all punctuation in the text view.

func speechAnnouncementsQueued(Bool) -> some View

Controls whether to queue pending announcements behind existing speech rather than interrupting speech in progress.

func speechSpellsOutCharacters(Bool) -> some View

Sets whether VoiceOver should speak the contents of the text view character by character.

### Accessibility Chart Descriptions

func accessibilityChartDescriptor&lt;R>(R) -> some View

Adds a descriptor to a View that represents a chart to make the chart’s contents accessible to all users.

### Tint Color

func tint(Color?) -> some View

Sets the tint color within this view.

func listRowSeparatorTint(Color?, edges: VerticalEdge.Set) -> some View

Sets the tint color associated with a row.

func listSectionSeparatorTint(Color?, edges: VerticalEdge.Set) -> some View

Sets the tint color associated with a section.

func listItemTint(ListItemTint?) -> some View

Sets the tint effect for content in a list.

func listItemTint(Color?) -> some View

Sets a fixed tint color for content in a list.

### Foreground Elements

func foregroundStyle&lt;S>(S) -> some View

Sets a view’s foreground elements to use a given style.

func foregroundStyle&lt;S1, S2>(S1, S2) -> some View

Sets the primary and secondary levels of the foreground style in the child view.

func foregroundStyle&lt;S1, S2, S3>(S1, S2, S3) -> some View

Sets the primary, secondary, and tertiary levels of the foreground style.

func foregroundColor(Color?) -> some View

Sets the color of the foreground elements displayed by this view.

func overlay&lt;S>(S, ignoresSafeAreaEdges: Edge.Set) -> some View

Layers the specified style in front of this view.

func overlay&lt;S, T>(S, in: T, fillStyle: FillStyle) -> some View

Layers a shape that you specify in front of this view.

### Background Elements

func border&lt;S>(S, width: CGFloat) -> some View

Adds a border to this view with the specified style and width.

func background(ignoresSafeAreaEdges: Edge.Set) -> some View

Sets the view’s background to the default background style.

func background&lt;S>(S, ignoresSafeAreaEdges: Edge.Set) -> some View

Sets the view’s background to a style.

func background&lt;S>(in: S, fillStyle: FillStyle) -> some View

Sets the view’s background to a shape filled with the default background style.

func background&lt;S, T>(S, in: T, fillStyle: FillStyle) -> some View

Sets the view’s background to a shape filled with a style.

func background&lt;S>(in: S, fillStyle: FillStyle) -> some View

Sets the view’s background to an insettable shape filled with the default background style.

func background&lt;S, T>(S, in: T, fillStyle: FillStyle) -> some View

Sets the view’s background to an insettable shape filled with a style.

func listRowBackground&lt;V>(V?) -> some View

Places a custom background view behind a list row item.

### Light and Dark Appearance

func preferredColorScheme(ColorScheme?) -> some View

Sets the preferred color scheme for this presentation.

### Prominence

func headerProminence(Prominence) -> some View

Sets the header prominence for this view.

### Control Size and Layout

func controlSize(ControlSize) -> some View

Sets the size for controls within this view.

### Privacy and Redaction

func privacySensitive(Bool) -> some View

Marks the view as containing sensitive, private user data.

func redacted(reason: RedactionReasons) -> some View

Adds a reason to apply a redaction to this view hierarchy.

func unredacted() -> some View

Removes any reason to apply a redaction to this view hierarchy.

### Visibility

func hidden() -> some View

Hides this view unconditionally.

func labelsHidden() -> some View

Hides the labels of any controls contained within this view.

func menuIndicator(Visibility) -> some View

Sets the menu indicator visibility for controls within this view.

func listRowSeparator(Visibility, edges: VerticalEdge.Set) -> some View

Sets the display mode for the separator associated with this specific row.

func listSectionSeparator(Visibility, edges: VerticalEdge.Set) -> some View

Sets whether to hide the separator associated with a list section.

### Fonts

func font(Font?) -> some View

Sets the default font for text in this view.

### Text Style

func monospacedDigit() -> some View

Modifies the fonts of all child views to use fixed-width digits, if possible, while leaving other characters proportionally spaced.

func textCase(Text.Case?) -> some View

Sets a transform for the case of the text contained in this view when displayed.

### Text Layout

func allowsTightening(Bool) -> some View

Sets whether text in this view can compress the space between characters when necessary to fit text in a line.

func minimumScaleFactor(CGFloat) -> some View

Sets the minimum amount that text in this view scales down to fit in the available space.

func truncationMode(Text.TruncationMode) -> some View

Sets the truncation mode for lines of text that are too long to fit in the available space.

func flipsForRightToLeftLayoutDirection(Bool) -> some View

Sets whether this view mirrors its contents horizontally when the layout direction is right-to-left.

### Multiline Text

func lineSpacing(CGFloat) -> some View

Sets the amount of space between lines of text in this view.

func multilineTextAlignment(TextAlignment) -> some View

Sets the alignment of a text view that contains multiple lines of text.

### Text Selection

func textSelection&lt;S>(S) -> some View

Controls whether people can select text within this view.

### Text Entry

func keyboardType(UIKeyboardType) -> some View

Sets the keyboard type for this view.

func disableAutocorrection(Bool?) -> some View

Sets whether to disable autocorrection for this view.

func autocapitalization(UITextAutocapitalizationType) -> some View

Sets whether to apply auto-capitalization to this view.

func textContentType(UITextContentType?) -> some View

Sets the text content type for this view, which the system uses to offer suggestions while the user enters text on an iOS or tvOS device.

### Keyboard Shortcuts

func keyboardShortcut(KeyEquivalent, modifiers: EventModifiers) -> some View

Defines a keyboard shortcut and assigns it to the modified control.

func keyboardShortcut(KeyEquivalent, modifiers: EventModifiers, localization: KeyboardShortcut.Localization) -> some View

Defines a keyboard shortcut and assigns it to the modified control.

### Symbol Appearance

func symbolRenderingMode(SymbolRenderingMode?) -> some View

Sets the rendering mode for symbol images within this view.

func symbolVariant(SymbolVariants) -> some View

Makes symbols within the view show a particular variant.

### Badges

func badge(LocalizedStringKey?) -> some View

Generates a badge for the view from a localized string key.

func badge(Int) -> some View

Generates a badge for the view from an integer value.

func badge&lt;S>(S?) -> some View

Generates a badge for the view from a string.

func badge(Text?) -> some View

Generates a badge for the view from a text view.

### Search

func searchable(text: Binding&lt;String>, placement: SearchFieldPlacement, prompt: LocalizedStringKey) -> some View

Marks this view as searchable, which configures the display of a search field.

func searchable(text: Binding&lt;String>, placement: SearchFieldPlacement, prompt: Text?) -> some View

Marks this view as searchable, which configures the display of a search field.

func searchable&lt;S>(text: Binding&lt;String>, placement: SearchFieldPlacement, prompt: S) -> some View

Marks this view as searchable, which configures the display of a search field.

func searchable&lt;S>(text: Binding&lt;String>, placement: SearchFieldPlacement, prompt: Text?, suggestions: () -> S) -> some View

Marks this view as searchable, which configures the display of a search field.

func searchable&lt;S>(text: Binding&lt;String>, placement: SearchFieldPlacement, prompt: LocalizedStringKey, suggestions: () -> S) -> some View

Marks this view as searchable, which configures the display of a search field.

func searchable&lt;V, S>(text: Binding&lt;String>, placement: SearchFieldPlacement, prompt: S, suggestions: () -> V) -> some View

Marks this view as searchable, which configures the display of a search field.

### Navigation Titles

func navigationTitle&lt;V>(() -> V) -> some View

Configures the view’s title for purposes of navigation, using a custom view.

func navigationTitle(Text) -> some View

Configures the view’s title for purposes of navigation.

func navigationTitle(LocalizedStringKey) -> some View

Configures the view’s title for purposes of navigation, using a localized string.

func navigationTitle&lt;S>(S) -> some View

Configures the view’s title for purposes of navigation, using a string.

### Navigation Bars

func navigationBarHidden(Bool) -> some View

Hides the navigation bar for this view.

func navigationBarBackButtonHidden(Bool) -> some View

Hides the navigation bar back button for the view.

func navigationBarTitleDisplayMode(NavigationBarItem.TitleDisplayMode) -> some View

Configures the title display mode for this view.

### Toolbars

func toolbar&lt;Content>(content: () -> Content) -> some View

Populates the toolbar or navigation bar with the specified items.

func toolbar&lt;Content>(content: () -> Content) -> some View

Populates the toolbar or navigation bar with the views you provide.

func toolbar&lt;Content>(id: String, content: () -> Content) -> some View

Populates the toolbar or navigation bar with the specified items, allowing for user customization.

### Tab Views

func tabItem&lt;V>(() -> V) -> some View

Sets the tab bar item associated with this view.

### Help Text

func help&lt;S>(S) -> some View

Adds help text to a view using a string that you provide.

func help(Text) -> some View

Adds help text to a view using a text view that you provide.

func help(LocalizedStringKey) -> some View

Adds help text to a view using a localized string that you provide.

### Context Menus

func contextMenu&lt;MenuItems>(menuItems: () -> MenuItems) -> some View

Adds a context menu to a view.

### The Status Bar

func statusBar(hidden: Bool) -> some View

Sets the visibility of the status bar.

### Styles

func buttonStyle&lt;S>(S) -> some View

Sets the style for buttons within this view to a button style with a custom appearance and standard interaction behavior.

func buttonStyle&lt;S>(S) -> some View

Sets the style for buttons within this view to a button style with a custom appearance and custom interaction behavior.

func controlGroupStyle&lt;S>(S) -> some View

Sets the style for control groups within this view.

func datePickerStyle&lt;S>(S) -> some View

Sets the style for date pickers within this view.

func groupBoxStyle&lt;S>(S) -> some View

Sets the style for group boxes within this view.

func indexViewStyle&lt;S>(S) -> some View

Sets the style for the index view within the current environment.

func labelStyle&lt;S>(S) -> some View

Sets the style for labels within this view.

func listStyle&lt;S>(S) -> some View

Sets the style for lists within this view.

func menuStyle&lt;S>(S) -> some View

Sets the style for menus within this view.

func navigationViewStyle&lt;S>(S) -> some View

Sets the style for navigation views within this view.

func pickerStyle&lt;S>(S) -> some View

Sets the style for pickers within this view.

func progressViewStyle&lt;S>(S) -> some View

Sets the style for progress views in this view.

func textFieldStyle&lt;S>(S) -> some View

Sets the style for text fields within this view.

func toggleStyle&lt;S>(S) -> some View

Sets the style for toggles in a view hierarchy.

func tabViewStyle&lt;S>(S) -> some View

Sets the style for the tab view within the current environment.

### Size

func frame(width: CGFloat?, height: CGFloat?, alignment: Alignment) -> some View

Positions this view within an invisible frame with the specified size.

func frame(minWidth: CGFloat?, idealWidth: CGFloat?, maxWidth: CGFloat?, minHeight: CGFloat?, idealHeight: CGFloat?, maxHeight: CGFloat?, alignment: Alignment) -> some View

Positions this view within an invisible frame having the specified size constraints.

func fixedSize() -> some View

Fixes this view at its ideal size.

func fixedSize(horizontal: Bool, vertical: Bool) -> some View

Fixes this view at its ideal size in the specified dimensions.

func layoutPriority(Double) -> some View

Sets the priority by which a parent layout should apportion space to this child.

### Position

func position(CGPoint) -> some View

Positions the center of this view at the specified point in its parent’s coordinate space.

func position(x: CGFloat, y: CGFloat) -> some View

Positions the center of this view at the specified coordinates in its parent’s coordinate space.

func offset(CGSize) -> some View

Offset this view by the horizontal and vertical amount specified in the offset parameter.

func offset(x: CGFloat, y: CGFloat) -> some View

Offset this view by the specified horizontal and vertical distances.

func coordinateSpace&lt;T>(name: T) -> some View

Assigns a name to the view’s coordinate space, so other code can operate on dimensions like points and sizes relative to the named space.

### Padding

func padding(EdgeInsets) -> some View

Adds a different padding amount to each edge of this view.

func padding(Edge.Set, CGFloat?) -> some View

Adds an equal padding amount to specific edges of this view.

func scenePadding(Edge.Set) -> some View

Adds padding to the specified edges of this view using an amount that’s appropriate for the current scene.

func ignoresSafeArea(SafeAreaRegions, edges: Edge.Set) -> some View

Expands the safe area of a view.

### Layering

func zIndex(Double) -> some View

Controls the display order of overlapping views.

func background&lt;V>(alignment: Alignment, content: () -> V) -> some View

Layers the views that you specify behind this view.

func listRowInsets(EdgeInsets?) -> some View

Applies an inset to the rows in a list.

func overlay&lt;V>(alignment: Alignment, content: () -> V) -> some View

Layers the views that you specify in front of this view.

### Masks and Clipping

func mask&lt;Mask>(alignment: Alignment, () -> Mask) -> some View

Masks this view using the alpha channel of the given view.

func clipped(antialiased: Bool) -> some View

Clips this view to its bounding rectangular frame.

func clipShape&lt;S>(S, style: FillStyle) -> some View

Sets a clipping shape for this view.

func cornerRadius(CGFloat, antialiased: Bool) -> some View

Clips this view to its bounding frame, with the specified corner radius.

func containerShape&lt;T>(T) -> some View

Sets the container shape to use for any container relative shape within this view.

### Scale

func scaledToFill() -> some View

Scales this view to fill its parent.

func scaledToFit() -> some View

Scales this view to fit its parent.

func scaleEffect(CGSize, anchor: UnitPoint) -> some View

Scales this view’s rendered output by the given vertical and horizontal size amounts, relative to an anchor point.

func scaleEffect(x: CGFloat, y: CGFloat, anchor: UnitPoint) -> some View

Scales this view’s rendered output by the given horizontal and vertical amounts, relative to an anchor point.

func imageScale(Image.Scale) -> some View

Scales images within the view according to one of the relative sizes available including small, medium, and large images sizes.

func aspectRatio(CGSize, contentMode: ContentMode) -> some View

Constrains this view’s dimensions to the aspect ratio of the given size.

### Rotation and Transformation

func rotationEffect(Angle, anchor: UnitPoint) -> some View

Rotates a view’s rendered output in two dimensions around the specified point.

func rotation3DEffect(Angle, axis: (x: CGFloat, y: CGFloat, z: CGFloat), anchor: UnitPoint, anchorZ: CGFloat, perspective: CGFloat) -> some View

Renders a view’s content as if it’s rotated in three dimensions around the specified axis.

func projectionEffect(ProjectionTransform) -> some View

Applies a projection transformation to this view’s rendered output.

func transformEffect(CGAffineTransform) -> some View

Applies an affine transformation to this view’s rendered output.

### Graphical Effects

func blur(radius: CGFloat, opaque: Bool) -> some View

Applies a Gaussian blur to this view.

func opacity(Double) -> some View

Sets the transparency of this view.

func brightness(Double) -> some View

Brightens this view by the specified amount.

func contrast(Double) -> some View

Sets the contrast and separation between similar colors in this view.

func colorInvert() -> some View

Inverts the colors in this view.

func colorMultiply(Color) -> some View

Adds a color multiplication effect to this view.

func saturation(Double) -> some View

Adjusts the color saturation of this view.

func grayscale(Double) -> some View

Adds a grayscale effect to this view.

func hueRotation(Angle) -> some View

Applies a hue rotation effect to this view.

func luminanceToAlpha() -> some View

Adds a luminance to alpha effect to this view.

func shadow(color: Color, radius: CGFloat, x: CGFloat, y: CGFloat) -> some View

Adds a shadow to this view.

### Composites

func blendMode(BlendMode) -> some View

Sets the blend mode for compositing this view with overlapping views.

func compositingGroup() -> some View

Wraps this view in a compositing group.

func drawingGroup(opaque: Bool, colorMode: ColorRenderingMode) -> some View

Composites this view’s contents into an offscreen image before final display.

### Animations

func animation&lt;V>(Animation?, value: V) -> some View

Applies the given animation to this view when the specified value changes.

func transaction((inout Transaction) -> Void) -> some View

Applies the given transaction mutation function to all animations used within the view.

func matchedGeometryEffect&lt;ID>(id: ID, in: Namespace.ID, properties: MatchedGeometryProperties, anchor: UnitPoint, isSource: Bool) -> some View

Defines a group of views with synchronized geometry using an identifier and namespace that you provide.

### Interactivity

func disabled(Bool) -> some View

Adds a condition that controls whether users can interact with this view.

func handlesExternalEvents(preferring: Set&lt;String>, allowing: Set&lt;String>) -> some View

Specifies the external events that the view’s scene handles if the scene is already open.

### Swipe Actions

func swipeActions&lt;T>(edge: HorizontalEdge, allowsFullSwipe: Bool, content: () -> T) -> some View

Adds custom swipe actions to a row in a list.

### Refresh Controls

func refreshable(action: () async -> Void) -> some View

Marks this view as refreshable.

### Taps and Gestures

func onTapGesture(count: Int, perform: () -> Void) -> some View

Adds an action to perform when this view recognizes a tap gesture.

func onLongPressGesture(minimumDuration: Double, maximumDistance: CGFloat, perform: () -> Void, onPressingChanged: ((Bool) -> Void)?) -> some View

Adds an action to perform when this view recognizes a long press gesture.

func onLongPressGesture(minimumDuration: Double, perform: () -> Void, onPressingChanged: ((Bool) -> Void)?) -> some View

Adds an action to perform when this view recognizes a long press gesture.

func gesture&lt;T>(T, including: GestureMask) -> some View

Attaches a gesture to the view with a lower precedence than gestures defined by the view.

func highPriorityGesture&lt;T>(T, including: GestureMask) -> some View

Attaches a gesture to the view with a higher precedence than gestures defined by the view.

func simultaneousGesture&lt;T>(T, including: GestureMask) -> some View

Attaches a gesture to the view to process simultaneously with gestures defined by the view.

### Hover

func onHover(perform: (Bool) -> Void) -> some View

Adds an action to perform when the user moves the pointer over or away from the view’s frame.

func hoverEffect(HoverEffect) -> some View

Applies a hover effect to this view.

### Focus

func focused&lt;Value>(FocusState&lt;Value>.Binding, equals: Value) -> some View

Modifies this view by binding its focus state to the given state value.

func focused(FocusState&lt;Bool>.Binding) -> some View

Modifies this view by binding its focus state to the given Boolean state value.

func focusable(Bool) -> some View

Specifies if the view is focusable.

### Drag and Drop

func onDrag&lt;V>(() -> NSItemProvider, preview: () -> V) -> some View

Activates this view as the source of a drag and drop operation.

func onDrag(() -> NSItemProvider) -> some View

Activates this view as the source of a drag and drop operation.

func itemProvider(Optional&lt;() -> NSItemProvider?>) -> some View

Provides a closure that vends the drag representation to be used for a particular data element.

func onDrop(of: [UTType], delegate: any DropDelegate) -> some View

Defines the destination of a drag and drop operation using behavior controlled by the delegate that you provide.

func onDrop(of: [UTType], isTargeted: Binding&lt;Bool>?, perform: ([NSItemProvider]) -> Bool) -> some View

Defines the destination of a drag-and-drop operation that handles the dropped content with a closure that you specify.

func onDrop(of: [UTType], isTargeted: Binding&lt;Bool>?, perform: ([NSItemProvider], CGPoint) -> Bool) -> some View

Defines the destination of a drag and drop operation that handles the dropped content with a closure that you specify.

### Submission

func onSubmit(of: SubmitTriggers, () -> Void) -> some View

Adds an action to perform when the user submits a value to this view.

func submitScope(Bool) -> some View

Prevents submission triggers originating from this view to invoke a submission action configured by a submission modifier higher up in the view hierarchy.

func submitLabel(SubmitLabel) -> some View

Sets the submit label for this view.

### Movement

func moveDisabled(Bool) -> some View

Adds a condition for whether the view’s view hierarchy is movable.

### Deletion

func deleteDisabled(Bool) -> some View

Adds a condition for whether the view’s view hierarchy is deletable.

### User Activities

func userActivity&lt;P>(String, element: P?, (P, NSUserActivity) -> ()) -> some View

Advertises a user activity type.

func userActivity(String, isActive: Bool, (NSUserActivity) -> ()) -> some View

Advertises a user activity type.

func onContinueUserActivity(String, perform: (NSUserActivity) -> ()) -> some View

Registers a handler to invoke in response to a user activity that your app receives.

### View Life Cycle

func onAppear(perform: (() -> Void)?) -> some View

Adds an action to perform before this view appears.

func onDisappear(perform: (() -> Void)?) -> some View

Adds an action to perform after this view disappears.

func onChange&lt;V>(of: V, perform: (V) -> Void) -> some View

Performs an action when a specified value changes.

Deprecated

### URLs

func onOpenURL(perform: (URL) -> ()) -> some View

Registers a handler to invoke in response to a URL that your app receives.

### Publisher Events

func onReceive&lt;P>(P, perform: (P.Output) -> Void) -> some View

Adds an action to perform when this view detects data emitted by the given publisher.

### Hit Testing

func allowsHitTesting(Bool) -> some View

Configures whether this view participates in hit test operations.

func contentShape&lt;S>(S, eoFill: Bool) -> some View

Defines the content shape for hit testing.

### Alerts

func alert&lt;A>(LocalizedStringKey, isPresented: Binding&lt;Bool>, actions: () -> A) -> some View

Presents an alert when a given condition is true, using a localized string key for the title.

func alert&lt;A>(Text, isPresented: Binding&lt;Bool>, actions: () -> A) -> some View

Presents an alert when a given condition is true, using a text view for the title.

func alert&lt;S, A>(S, isPresented: Binding&lt;Bool>, actions: () -> A) -> some View

Presents an alert when a given condition is true, using a string variable as a title.

func alert&lt;S, A, T>(S, isPresented: Binding&lt;Bool>, presenting: T?, actions: (T) -> A) -> some View

Presents an alert using the given data to produce the alert’s content and a string variable as a title.

func alert&lt;A, T>(Text, isPresented: Binding&lt;Bool>, presenting: T?, actions: (T) -> A) -> some View

Presents an alert using the given data to produce the alert’s content and a text view as a title.

func alert&lt;A, T>(LocalizedStringKey, isPresented: Binding&lt;Bool>, presenting: T?, actions: (T) -> A) -> some View

Presents an alert using the given data to produce the alert’s content and a localized string key for a title.

func alert&lt;E, A>(isPresented: Binding&lt;Bool>, error: E?, actions: () -> A) -> some View

Presents an alert when an error is present.

### Alerts with a Message

func alert&lt;A, M>(Text, isPresented: Binding&lt;Bool>, actions: () -> A, message: () -> M) -> some View

Presents an alert with a message when a given condition is true using a text view as a title.

func alert&lt;S, A, M>(S, isPresented: Binding&lt;Bool>, actions: () -> A, message: () -> M) -> some View

Presents an alert with a message when a given condition is true using a string variable as a title.

func alert&lt;A, M>(LocalizedStringKey, isPresented: Binding&lt;Bool>, actions: () -> A, message: () -> M) -> some View

Presents an alert with a message when a given condition is true, using a localized string key for a title.

func alert&lt;A, M, T>(LocalizedStringKey, isPresented: Binding&lt;Bool>, presenting: T?, actions: (T) -> A, message: (T) -> M) -> some View

Presents an alert with a message using the given data to produce the alert’s content and a localized string key for a title.

func alert&lt;A, M, T>(Text, isPresented: Binding&lt;Bool>, presenting: T?, actions: (T) -> A, message: (T) -> M) -> some View

Presents an alert with a message using the given data to produce the alert’s content and a text view for a title.

func alert&lt;S, A, M, T>(S, isPresented: Binding&lt;Bool>, presenting: T?, actions: (T) -> A, message: (T) -> M) -> some View

Presents an alert with a message using the given data to produce the alert’s content and a string variable as a title.

func alert&lt;E, A, M>(isPresented: Binding&lt;Bool>, error: E?, actions: (E) -> A, message: (E) -> M) -> some View

Presents an alert with a message when an error is present.

### Confirmation Dialogs

func confirmationDialog&lt;A>(Text, isPresented: Binding&lt;Bool>, titleVisibility: Visibility, actions: () -> A) -> some View

Presents a confirmation dialog when a given condition is true, using a text view for the title.

func confirmationDialog&lt;S, A>(S, isPresented: Binding&lt;Bool>, titleVisibility: Visibility, actions: () -> A) -> some View

Presents a confirmation dialog when a given condition is true, using a string variable as a title.

func confirmationDialog&lt;A>(LocalizedStringKey, isPresented: Binding&lt;Bool>, titleVisibility: Visibility, actions: () -> A) -> some View

Presents a confirmation dialog when a given condition is true, using a localized string key for the title.

func confirmationDialog&lt;S, A, T>(S, isPresented: Binding&lt;Bool>, titleVisibility: Visibility, presenting: T?, actions: (T) -> A) -> some View

Presents a confirmation dialog using data to produce the dialog’s content and a string variable for the title.

func confirmationDialog&lt;A, T>(LocalizedStringKey, isPresented: Binding&lt;Bool>, titleVisibility: Visibility, presenting: T?, actions: (T) -> A) -> some View

Presents a confirmation dialog using data to produce the dialog’s content and a localized string key for the title.

func confirmationDialog&lt;A, T>(Text, isPresented: Binding&lt;Bool>, titleVisibility: Visibility, presenting: T?, actions: (T) -> A) -> some View

Presents a confirmation dialog using data to produce the dialog’s content and a text view for the title.

### Confirmation Dialogs with a Message

func confirmationDialog&lt;A, M>(Text, isPresented: Binding&lt;Bool>, titleVisibility: Visibility, actions: () -> A, message: () -> M) -> some View

Presents a confirmation dialog with a message when a given condition is true, using a text view for the title.

func confirmationDialog&lt;S, A, M>(S, isPresented: Binding&lt;Bool>, titleVisibility: Visibility, actions: () -> A, message: () -> M) -> some View

Presents a confirmation dialog with a message when a given condition is true, using a string variable for the title.

func confirmationDialog&lt;A, M>(LocalizedStringKey, isPresented: Binding&lt;Bool>, titleVisibility: Visibility, actions: () -> A, message: () -> M) -> some View

Presents a confirmation dialog with a message when a given condition is true, using a localized string key for the title.

func confirmationDialog&lt;A, M, T>(LocalizedStringKey, isPresented: Binding&lt;Bool>, titleVisibility: Visibility, presenting: T?, actions: (T) -> A, message: (T) -> M) -> some View

Presents a confirmation dialog with a message using data to produce the dialog’s content and a localized string key for the title.

func confirmationDialog&lt;A, M, T>(Text, isPresented: Binding&lt;Bool>, titleVisibility: Visibility, presenting: T?, actions: (T) -> A, message: (T) -> M) -> some View

Presents a confirmation dialog with a message using data to produce the dialog’s content and a text view for the message.

func confirmationDialog&lt;S, A, M, T>(S, isPresented: Binding&lt;Bool>, titleVisibility: Visibility, presenting: T?, actions: (T) -> A, message: (T) -> M) -> some View

Presents a confirmation dialog with a message using data to produce the dialog’s content and a string variable for the title.

### Sheets

func sheet&lt;Content>(isPresented: Binding&lt;Bool>, onDismiss: (() -> Void)?, content: () -> Content) -> some View

Presents a sheet when a binding to a Boolean value that you provide is true.

func sheet&lt;Item, Content>(item: Binding&lt;Item?>, onDismiss: (() -> Void)?, content: (Item) -> Content) -> some View

Presents a sheet using the given item as a data source for the sheet’s content.

func fullScreenCover&lt;Content>(isPresented: Binding&lt;Bool>, onDismiss: (() -> Void)?, content: () -> Content) -> some View

Presents a modal view that covers as much of the screen as possible when binding to a Boolean value you provide is true.

func fullScreenCover&lt;Item, Content>(item: Binding&lt;Item?>, onDismiss: (() -> Void)?, content: (Item) -> Content) -> some View

Presents a modal view that covers as much of the screen as possible using the binding you provide as a data source for the sheet’s content.

### Popovers

func popover&lt;Content>(isPresented: Binding&lt;Bool>, attachmentAnchor: PopoverAttachmentAnchor, arrowEdge: Edge?, content: () -> Content) -> some View

Presents a popover when a given condition is true.

func popover&lt;Item, Content>(item: Binding&lt;Item?>, attachmentAnchor: PopoverAttachmentAnchor, arrowEdge: Edge?, content: (Item) -> Content) -> some View

Presents a popover using the given item as a data source for the popover’s content.

### Sheet and Popover Dismissal

func interactiveDismissDisabled(Bool) -> some View

Conditionally prevents interactive dismissal of presentations like popovers, sheets, and inspectors.

### File Managers

func fileExporter&lt;D>(isPresented: Binding&lt;Bool>, document: D?, contentType: UTType, defaultFilename: String?, onCompletion: (Result&lt;URL, any Error>) -> Void) -> some View

Presents a system interface for exporting a document that’s stored in a value type, like a structure, to a file on disk.

func fileExporter&lt;D>(isPresented: Binding&lt;Bool>, document: D?, contentType: UTType, defaultFilename: String?, onCompletion: (Result&lt;URL, any Error>) -> Void) -> some View

Presents a system interface for exporting a document that’s stored in a reference type, like a class, to a file on disk.

func fileExporter&lt;C>(isPresented: Binding&lt;Bool>, documents: C, contentType: UTType, onCompletion: (Result&lt;[URL], any Error>) -> Void) -> some View

Presents a system interface for exporting a collection of value type documents to files on disk.

func fileExporter&lt;C>(isPresented: Binding&lt;Bool>, documents: C, contentType: UTType, onCompletion: (Result&lt;[URL], any Error>) -> Void) -> some View

Presents a system interface for exporting a collection of reference type documents to files on disk.

func fileImporter(isPresented: Binding&lt;Bool>, allowedContentTypes: [UTType], allowsMultipleSelection: Bool, onCompletion: (Result&lt;[URL], any Error>) -> Void) -> some View

Presents a system interface for allowing the user to import multiple files.

func fileImporter(isPresented: Binding&lt;Bool>, allowedContentTypes: [UTType], onCompletion: (Result&lt;URL, any Error>) -> Void) -> some View

Presents a system interface for allowing the user to import an existing file.

func fileMover(isPresented: Binding&lt;Bool>, file: URL?, onCompletion: (Result&lt;URL, any Error>) -> Void) -> some View

Presents a system interface for allowing the user to move an existing file to a new location.

func fileMover&lt;C>(isPresented: Binding&lt;Bool>, files: C, onCompletion: (Result&lt;[URL], any Error>) -> Void) -> some View

Presents a system interface for allowing the user to move a collection of existing files to a new location.

### Identity

func id&lt;ID>(ID) -> some View

Binds a view’s identity to the given proxy value.

### Default Storage

func defaultAppStorage(UserDefaults) -> some View

The default store used by `AppStorage` contained within the view.

### Preferences

func preference&lt;K>(key: K.Type, value: K.Value) -> some View

Sets a value for the given preference.

func transformPreference&lt;K>(K.Type, (inout K.Value) -> Void) -> some View

Applies a transformation to a preference value.

func anchorPreference&lt;A, K>(key: K.Type, value: Anchor&lt;A>.Source, transform: (Anchor&lt;A>) -> K.Value) -> some View

Sets a value for the specified preference key, the value is a function of a geometry value tied to the current coordinate space, allowing readers of the value to convert the geometry to their local coordinates.

func transformAnchorPreference&lt;A, K>(key: K.Type, value: Anchor&lt;A>.Source, transform: (inout K.Value, Anchor&lt;A>) -> Void) -> some View

Sets a value for the specified preference key, the value is a function of the key’s current value and a geometry value tied to the current coordinate space, allowing readers of the value to convert the geometry to their local coordinates.

func onPreferenceChange&lt;K>(K.Type, perform: (K.Value) -> Void) -> some View

Adds an action to perform when the specified preference key’s value changes.

func backgroundPreferenceValue&lt;Key, T>(Key.Type, (Key.Value) -> T) -> some View

Reads the specified preference value from the view, using it to produce a second view that is applied as the background of the original view.

func overlayPreferenceValue&lt;Key, T>(Key.Type, (Key.Value) -> T) -> some View

Reads the specified preference value from the view, using it to produce a second view that is applied as an overlay to the original view.

### Environment Values

func environmentObject&lt;T>(T) -> some View

Supplies an observable object to a view’s hierarchy.

func transformEnvironment&lt;V>(WritableKeyPath&lt;EnvironmentValues, V>, transform: (inout V) -> Void) -> some View

Transforms the environment value of the specified key path with the given function.

### Configuring View Previews

func previewDevice(PreviewDevice?) -> some View

Overrides the device for a preview.

func previewDisplayName(String?) -> some View

Sets a user visible name to show in the canvas for a preview.

func previewLayout(PreviewLayout) -> some View

Overrides the size of the container for the preview.

func previewInterfaceOrientation(InterfaceOrientation) -> some View

Overrides the orientation of the preview.

func previewContext&lt;C>(C) -> some View

Declares a context for the preview.

### Implementing View Modifiers

func modifier&lt;T>(T) -> ModifiedContent&lt;Self, T>

Applies a modifier to a view and returns a new view.

### Deprecated Accessibility Modifiers

func accessibility(label: Text) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

Adds a label to the view that describes its contents.

func accessibility(value: Text) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

Adds a textual description of the value that the view contains.

func accessibility(hidden: Bool) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

Specifies whether to hide this view from system accessibility features.

func accessibility(identifier: String) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

Uses the specified string to identify the view.

func accessibility(selectionIdentifier: AnyHashable) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

Sets a selection identifier for this view’s accessibility element.

Deprecated

func accessibility(hint: Text) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

Communicates to the user what happens after performing the view’s action.

func accessibility(activationPoint: CGPoint) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

Specifies the point where activations occur in the view.

func accessibility(activationPoint: UnitPoint) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

Specifies the unit point where activations occur in the view.

func accessibility(inputLabels: [Text]) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

Sets alternate input labels with which users identify a view.

func accessibility(addTraits: AccessibilityTraits) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

Adds the given traits to the view.

func accessibility(removeTraits: AccessibilityTraits) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

Removes the given traits from this view.

func accessibility(sortPriority: Double) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

Sets the sort priority order for this view’s accessibility element, relative to other elements at the same level.

func accessibilityCustomContent&lt;L, V>(L, V, importance: AXCustomContent.Importance) -> ModifiedContent&lt;Self, AccessibilityAttachmentModifier>

Add additional accessibility information to the view.

Deprecated

### Deprecated Appearance Modifiers

func colorScheme(ColorScheme) -> some View

Sets this view’s color scheme.

### Deprecated Auxiliary View Modifiers

func navigationBarTitle&lt;S>(S) -> some View

Sets the title of this view’s navigation bar with a string.

func navigationBarTitle(LocalizedStringKey) -> some View

Sets the title of this view’s navigation bar with a localized string.

func navigationBarTitle(Text) -> some View

Sets the title in the navigation bar for this view.

func navigationBarTitle(Text, displayMode: NavigationBarItem.TitleDisplayMode) -> some View

Sets the title and display mode in the navigation bar for this view.

func navigationBarTitle&lt;S>(S, displayMode: NavigationBarItem.TitleDisplayMode) -> some View

Sets the title and display mode in the navigation bar for this view.

func navigationBarTitle(LocalizedStringKey, displayMode: NavigationBarItem.TitleDisplayMode) -> some View

Sets the title and display mode in the navigation bar for this view.

func navigationBarItems&lt;L>(leading: L) -> some View

func navigationBarItems&lt;L, T>(leading: L, trailing: T) -> some View

func navigationBarItems&lt;T>(trailing: T) -> some View

func contextMenu&lt;MenuItems>(ContextMenu&lt;MenuItems>?) -> some View

Adds a context menu to the view.

### Deprecated Layout Modifiers

func frame() -> some View

Positions this view within an invisible frame.

Deprecated

func edgesIgnoringSafeArea(Edge.Set) -> some View

Changes the view’s proposed area to extend outside the screen’s safe areas.

func overlay&lt;Overlay>(Overlay, alignment: Alignment) -> some View

Layers a secondary view in front of this view.

func background&lt;Background>(Background, alignment: Alignment) -> some View

Layers the given view behind this view.

### Deprecated Graphics and Rendering Modifiers

func accentColor(Color?) -> some View

Sets the accent color for this view and the views it contains.

func mask&lt;Mask>(Mask) -> some View

Masks this view using the alpha channel of the given view.

func animation(Animation?) -> some View

Applies the given animation to all animatable values within this view.

Deprecated

### Deprecated Input and Event Modifiers

func onLongPressGesture(minimumDuration: Double, maximumDistance: CGFloat, pressing: ((Bool) -> Void)?, perform: () -> Void) -> some View

Adds an action to perform when this view recognizes a long press gesture.

func onLongPressGesture(minimumDuration: Double, pressing: ((Bool) -> Void)?, perform: () -> Void) -> some View

Adds an action to perform when this view recognizes a long press gesture.

func onDrop(of: [String], delegate: any DropDelegate) -> some View

Defines the destination for a drag and drop operation with the same size and position as this view, with behavior controlled by the given delegate.

func onDrop(of: [String], isTargeted: Binding&lt;Bool>?, perform: ([NSItemProvider], CGPoint) -> Bool) -> some View

Defines the destination for a drag and drop operation with the same size and position as this view, handling dropped content and the drop location with the given closure.

func onDrop(of: [String], isTargeted: Binding&lt;Bool>?, perform: ([NSItemProvider]) -> Bool) -> some View

Defines the destination for a drag and drop operation, using the same size and position as this view, handling dropped content with the given closure.

### Deprecated View Presentation Modifiers

func actionSheet(isPresented: Binding&lt;Bool>, content: () -> ActionSheet) -> some View

Presents an action sheet when a given condition is true.

func actionSheet&lt;T>(item: Binding&lt;T?>, content: (T) -> ActionSheet) -> some View

Presents an action sheet using the given item as a data source for the sheet’s content.

func alert(isPresented: Binding&lt;Bool>, content: () -> Alert) -> some View

Presents an alert to the user.

func alert&lt;Item>(item: Binding&lt;Item?>, content: (Item) -> Alert) -> some View

Presents an alert to the user.

