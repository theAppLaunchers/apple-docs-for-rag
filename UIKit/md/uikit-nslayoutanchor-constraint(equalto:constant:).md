

- UIKit
- NSLayoutAnchor
-  constraint(equalTo:constant:) 

Instance Method

# constraint(equalTo:constant:)

Returns a constraint that defines one item’s attribute as equal to another item’s attribute plus a constant offset.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+tvOS 9.0+visionOS 1.0+

``` source
@MainActor
func constraint(
    equalTo anchor: NSLayoutAnchor,
    constant c: CGFloat
) -> NSLayoutConstraint
```

## Parameters 

`anchor`  

A layout anchor from a UIView, NSView, or UILayoutGuide object. You must use a subclass of NSLayoutAnchor that matches the current anchor. For example, if you call this method on an NSLayoutXAxisAnchor object, this parameter must be another NSLayoutXAxisAnchor.

`c`  

The constant offset for the constraint.

## Return Value

An NSLayoutConstraint object that defines an equal relationship between the attributes represented by the two layout anchors plus a constant offset.

## Discussion

This method defines the relationship `first attribute = second attribute + c`. Where `first attribute` is the layout attribute represented by the anchor receiving this method call, and `second attribute` is the layout attribute represented by the `anchor` parameter. The value `c`, represents a constant offset. All values are measured in points; however, these values can be interpreted in different ways, depending on the type of layout anchor.

- For NSLayoutXAxisAnchor objects, the first attribute is positioned `c` points after the second attribute. When using leading or trailing attributes, values increase as you move in the language’s reading direction. In English, for example, values increase as you move to the right. For left and right attributes, values always increase as you move right.

- For NSLayoutYAxisAnchor objects, the first attribute is positioned `c` points below the second attribute. Values increase as you move down.

- For NSLayoutDimension objects, the size of the first attribute is `c` points larger than the size of the second attribute. Values increase as items increase in size.

The constraints produced by the following two examples are identical.

- Swift
- Objective-C

```
// Creating a constraint using NSLayoutConstraint

NSLayoutConstraint(item: textField,
                   attribute: .Leading,
                   relatedBy: .Equal,
                   toItem: label,
                   attribute: .Trailing,
                   multiplier: 1.0,
                   constant: 8.0).isActive = true

// Creating the same constraint using constraintEqualToAnchor:constant:
textField.leadingAnchor.constraintEqualToAnchor(label.trailingAnchor, constant: 8.0).isActive = true
```

```
// Creating a constraint using NSLayoutConstraint

[NSLayoutConstraint constraintWithItem:self.textField
                             attribute:NSLayoutAttributeLeading
                             relatedBy:NSLayoutRelationEqual
                                toItem:self.label
                             attribute:NSLayoutAttributeTrailing
                            multiplier:1.0
                              constant:8.0].active = YES;

// Creating the same constraint using constraintEqualToAnchor:constant:
[self.textField.leadingAnchor constraintEqualToAnchor:self.label.trailingAnchor constant:8.0].active = YES;
```

## See Also

### Building constraints

func constraint(equalTo: NSLayoutAnchor&lt;AnchorType>) -> NSLayoutConstraint

Returns a constraint that defines one item’s attribute as equal to another.

func constraint(greaterThanOrEqualTo: NSLayoutAnchor&lt;AnchorType>) -> NSLayoutConstraint

Returns a constraint that defines one item’s attribute as greater than or equal to another.

func constraint(greaterThanOrEqualTo: NSLayoutAnchor&lt;AnchorType>, constant: CGFloat) -> NSLayoutConstraint

Returns a constraint that defines one item’s attribute as greater than or equal to another item’s attribute plus a constant offset.

func constraint(lessThanOrEqualTo: NSLayoutAnchor&lt;AnchorType>) -> NSLayoutConstraint

Returns a constraint that defines one item’s attribute as less than or equal to another.

func constraint(lessThanOrEqualTo: NSLayoutAnchor&lt;AnchorType>, constant: CGFloat) -> NSLayoutConstraint

Returns a constraint that defines one item’s attribute as less than or equal to another item’s attribute plus a constant offset.

