

- AppKit
- NSLayoutDimension
-  constraint(equalToConstant:) 

Instance Method

# constraint(equalToConstant:)

Returns a constraint that defines a constant size for the anchor’s size attribute.

macOS 10.11+

``` source
func constraint(equalToConstant c: CGFloat) -> NSLayoutConstraint
```

## Parameters 

`c`  

A constant representing the size of the attribute associated with this dimension anchor.

## Return Value

An NSLayoutConstraint object that defines a constant size for the attribute associated with this dimension anchor.

## Discussion

This method defines the relationship `first attribute = c`. Where `first attribute` is the layout attribute represented by the anchor receiving this method call.

The constraints produced by the following two examples are identical.

- Swift
- Objective-C

```
// Creating a constraint using NSLayoutConstraint
NSLayoutConstraint(item: button,
                   attribute: .Width,
                   relatedBy: .Equal,
                   toItem: nil,
                   attribute: .NotAnAttribute,
                   multiplier: 1.0,
                   constant: 40.0).isActive = true

// Creating the same constraint using constraintEqualToConstant:
button.widthAnchor.constraintEqualToConstant(40.0).isActive = true
```

```
// Creating a constraint using NSLayoutConstraint
[NSLayoutConstraint
 constraintWithItem:self.button
 attribute:NSLayoutAttributeWidth
 relatedBy:NSLayoutRelationEqual
 toItem:nil
 attribute:NSLayoutAttributeNotAnAttribute
 multiplier:1.0
 constant:40.0].active = YES;

// Creating the same constraint using constraintEqualToConstant:
[self.button.widthAnchor constraintEqualToConstant: 40.0].active = YES;
```

## See Also

### Building constraints

func constraint(equalTo: NSLayoutDimension, multiplier: CGFloat) -> NSLayoutConstraint

Returns a constraint that defines the anchor’s size attribute as equal to the specified anchor multiplied by the constant.

func constraint(equalTo: NSLayoutDimension, multiplier: CGFloat, constant: CGFloat) -> NSLayoutConstraint

Returns a constraint that defines the anchor’s size attribute as equal to the specified size attribute multiplied by a constant plus an offset.

func constraint(greaterThanOrEqualTo: NSLayoutDimension, multiplier: CGFloat) -> NSLayoutConstraint

Returns a constraint that defines the anchor’s size attribute as greater than or equal to the specified anchor multiplied by the constant.

func constraint(greaterThanOrEqualTo: NSLayoutDimension, multiplier: CGFloat, constant: CGFloat) -> NSLayoutConstraint

Returns a constraint that defines the anchor’s size attribute as greater than or equal to the specified anchor multiplied by the constant plus an offset.

func constraint(greaterThanOrEqualToConstant: CGFloat) -> NSLayoutConstraint

Returns a constraint that defines the minimum size for the anchor’s size attribute.

func constraint(lessThanOrEqualTo: NSLayoutDimension, multiplier: CGFloat) -> NSLayoutConstraint

Returns a constraint that defines the anchor’s size attribute as less than or equal to the specified anchor multiplied by the constant.

func constraint(lessThanOrEqualTo: NSLayoutDimension, multiplier: CGFloat, constant: CGFloat) -> NSLayoutConstraint

Returns a constraint that defines the anchor’s size attribute as greater than or equal to the specified anchor multiplied by the constant plus an offset.

func constraint(lessThanOrEqualToConstant: CGFloat) -> NSLayoutConstraint

Returns a constraint that defines the maximum size for the anchor’s size attribute.

