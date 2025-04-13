

- Foundation
- NSCoder
-  decodeCGRect(forKey:) 

Instance Method

# decodeCGRect(forKey:)

Decodes and returns the Core Graphics rectangle structure associated with the specified key in the coder’s archive.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.0+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func decodeCGRect(forKey key: String) -> CGRect
```

## Parameters 

`key`  

The key that identifies the rectangle.

## Return Value

The `CGRect` structure.

## Discussion

Use this method to decode a rectangle that was previously encoded using the encode(_:forKey:) method.

## See Also

### Related Documentation

func encode(CGRect, forKey: String)

Encodes a rectangle and associates it with the specified key in the receiver’s archive.

### Decoding Geometry-Based Data

func decodeCGAffineTransform(forKey: String) -> CGAffineTransform

Decodes and returns the Core Graphics affine transform structure associated with the specified key in the coder’s archive.

func decodeCGPoint(forKey: String) -> CGPoint

Decodes and returns the Core Graphics point structure associated with the specified key in the coder’s archive.

func decodeCGSize(forKey: String) -> CGSize

Decodes and returns the Core Graphics size structure associated with the specified key in the coder’s archive.

func decodeCGVector(forKey: String) -> CGVector

Decodes and returns the Core Graphics vector data associated with the specified key in the coder’s archive.

func decodeDirectionalEdgeInsets(forKey: String) -> NSDirectionalEdgeInsets

Decodes and returns the UIKit directional edge insets structure associated with the specified key in the coder’s archive.

func decodeUIEdgeInsets(forKey: String) -> UIEdgeInsets

Decodes and returns the UIKit edge insets structure associated with the specified key in the coder’s archive.

func decodeUIOffset(forKey: String) -> UIOffset

Decodes and returns the UIKit offset structure associated with the specified key in the coder’s archive.

