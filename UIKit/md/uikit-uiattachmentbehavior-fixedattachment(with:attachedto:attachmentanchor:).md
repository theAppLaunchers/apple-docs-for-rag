

- UIKit
- UIAttachmentBehavior
-  fixedAttachment(with:attachedTo:attachmentAnchor:) 

Type Method

# fixedAttachment(with:attachedTo:attachmentAnchor:)

Creates and returns an attachment behavior where the two items are fixed together through the specified anchor point.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+tvOS 9.0+visionOS 1.0+

``` source
@MainActor
class func fixedAttachment(
    with item1: any UIDynamicItem,
    attachedTo item2: any UIDynamicItem,
    attachmentAnchor point: CGPoint
) -> Self
```

## Parameters 

`item1`  

The first of two dynamic items connected by the attachment behavior.

`item2`  

The second of two dynamic items connected by the attachment behavior.

`point`  

The anchor point for both items. Specify this point in the coordinate system of the dynamic animator’s reference view. For more information about coordinate systems, see UIDynamicAnimator.

## Return Value

A new attachment object or `nil` if the object could not be created.

## Discussion

The behavior created by this method acts like a solid rod connecting each item to the specified anchor point. The position of the items relative to each other does not change. Forces acting on the items move them together as if they were a single unit.

## See Also

### Creating and initializing attachment behavior objects

class func slidingAttachment(with: any UIDynamicItem, attachmentAnchor: CGPoint, axisOfTranslation: CGVector) -> Self

Creates and returns an attachment behavior where one item slides along the specified axis.

class func slidingAttachment(with: any UIDynamicItem, attachedTo: any UIDynamicItem, attachmentAnchor: CGPoint, axisOfTranslation: CGVector) -> Self

Creates and returns an attachment behavior where two items are fixed to points that slide along the specified axis.

class func limitAttachment(with: any UIDynamicItem, offsetFromCenter: UIOffset, attachedTo: any UIDynamicItem, offsetFromCenter: UIOffset) -> Self

Creates and returns an attachment behavior object where two items are constrained by a maximum distance from one another.

class func pinAttachment(with: any UIDynamicItem, attachedTo: any UIDynamicItem, attachmentAnchor: CGPoint) -> Self

Creates and returns an attachment behavior where the two items are pinned to, and move around, an anchor point

convenience init(item: any UIDynamicItem, attachedToAnchor: CGPoint)

Initializes a behavior where the center of a dynamic item is attached to the specified anchor point.

convenience init(item: any UIDynamicItem, attachedTo: any UIDynamicItem)

Initializes a behavior where the centers of two dynamic items are attached to each other.

init(item: any UIDynamicItem, offsetFromCenter: UIOffset, attachedToAnchor: CGPoint)

Initializes a behavior where the specified point in a dynamic item is attached to an anchor point.

init(item: any UIDynamicItem, offsetFromCenter: UIOffset, attachedTo: any UIDynamicItem, offsetFromCenter: UIOffset)

Initializes an attachment behavior that connects a specified point in one dynamic item to a specified point in another dynamic item.

