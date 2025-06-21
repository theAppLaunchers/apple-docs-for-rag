*   [UIKit](/documentation/uikit)
*   [UIImage](/documentation/uikit/uiimage)
*   prepareThumbnail(of:completionHandler:)

Instance Method

# prepareThumbnail(of:completionHandler:)

Creates a thumbnail image at the specified size asynchronously on a background thread.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+tvOS 15.0+visionOS 1.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
func prepareThumbnail(
    of size: [`CGSize`](/documentation/CoreFoundation/CGSize),
    completionHandler: @escaping ([`UIImage`](/documentation/uikit/uiimage)?) -> [`Void`](/documentation/Swift/Void)
)
```
```
```
```
```
```
```swift
```swift
```swift
```swift
```swift
```swift
func byPreparingThumbnail(ofSize size: [`CGSize`](/documentation/CoreFoundation/CGSize)) async -> [`UIImage`](/documentation/uikit/uiimage)?
```
```
```
```
```
```
```
```

## [Parameters](/documentation/UIKit/UIImage/prepareThumbnail\(of:completionHandler:\)#parameters)

`size`

The desired size of the thumbnail.

`completionHandler`

The completion handler to call when the thumbnail is ready. The handler executes on a background thread.

The completion handler takes the following parameters:

`thumbnail`

A new thumbnail image. This parameter is `nil` if the original image isn’t backed by a [`CGImage`](/documentation/CoreGraphics/CGImage) or if the image data is corrupt or malformed.

## [Discussion](/documentation/UIKit/UIImage/prepareThumbnail\(of:completionHandler:\)#Discussion)

When displaying an image in a [`UIImageView`](/documentation/uikit/uiimageview), you can use the view’s [`contentMode`](/documentation/uikit/uiview/contentmode-swift.property) property to clip or scale the image automatically. But when the native image size is much larger than the bounds of the view, decoding the full size image creates unnecessary memory overhead. By creating a thumbnail image at a specified size with this method, you avoid the overhead of decoding the image at its full size.

This method asynchronously creates the thumbnail image on a background thread and calls the completion handler on that thread. If your app updates the UI in the completion handler, schedule the UI update on the main thread.

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
func collectionView(_ collectionView: UICollectionView, cellForItemAt indexPath: IndexPath) -> UICollectionViewCell {
```
```
    guard let cell = collectionView.dequeueReusableCell(withReuseIdentifier: cellIdentifier, for: indexPath) as? ItemCell else {
        fatalError("Unexpected type for cell. Check configuration.")
    }
        
    let item = items[indexPath.item]
    cell.nameLabel?.text = item.name
    item.image.prepareThumbnail(of: thumbnailSize) { thumbnail in
        DispatchQueue.main.async {
            cell.thumbnailImageView?.image = thumbnail
        }
    }
    return cell
}
```
```
```
```
```

```

```
- (UICollectionViewCell *)collectionView:(UICollectionView *)collectionView cellForItemAtIndexPath:(NSIndexPath *)indexPath {
    UICollectionViewCell *cell = [collectionView dequeueReusableCellWithReuseIdentifier:self.cellIdentifier forIndexPath:indexPath];
    NSAssert([cell isKindOfClass:[ItemCell class]], @"Unexpected type for cell. Check configuration.\n");
    
    Item *item = self.items[indexPath.row];
    ItemCell *itemCell = (ItemCell *)cell;
    itemCell.nameLabel.text = item.name;
    [item.image prepareThumbnailOfSize:self.thumbnailSize completionHandler:^(UIImage *thumbnail) {
        dispatch_async(dispatch_get_main_queue(), ^{
            itemCell.thumbnailImageView.image = thumbnail;
        });
    }];
    return cell;
}
```

```
```
```
```
```

## [See Also](/documentation/UIKit/UIImage/prepareThumbnail\(of:completionHandler:\)#see-also)

### [Loading images for display](/documentation/UIKit/UIImage/prepareThumbnail\(of:completionHandler:\)#Loading-images-for-display)

```swift
```swift
```swift
```swift
func preparingForDisplay() -> UIImage?
```
```

Decodes an image synchronously and provides a new one for display in views and animations.
```
```swift
```swift
```swift
func prepareForDisplay(completionHandler: (UIImage?) -> Void)
```
```

Decodes an image asynchronously and provides a new one for display in views and animations.
```
```swift
```swift
```swift
func preparingThumbnail(of: CGSize) -> UIImage?
```
```

Returns a new thumbnail image at the specified size.
```
```