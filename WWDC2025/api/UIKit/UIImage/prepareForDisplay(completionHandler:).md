*   [UIKit](/documentation/uikit)
*   [UIImage](/documentation/uikit/uiimage)
*   prepareForDisplay(completionHandler:)

Instance Method

# prepareForDisplay(completionHandler:)

Decodes an image asynchronously and provides a new one for display in views and animations.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+tvOS 15.0+visionOS 1.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
func prepareForDisplay(completionHandler: @escaping ([`UIImage`](/documentation/uikit/uiimage)?) -> [`Void`](/documentation/Swift/Void))
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
func byPreparingForDisplay() async -> [`UIImage`](/documentation/uikit/uiimage)?
```
```
```
```
```
```
```
```

## [Parameters](/documentation/UIKit/UIImage/prepareForDisplay\(completionHandler:\)#parameters)

`completionHandler`

The closure to call when the function finishes preparing the image.

This completion handler takes one parameter:

`image`

A new version of the image object for display. If the system can’t decode the image, the parameter value is `nil.`

## [Discussion](/documentation/UIKit/UIImage/prepareForDisplay\(completionHandler:\)#Discussion)

The Animation Hitches [instrument](https://help.apple.com/instruments/mac/current/) measures system performance for multiple stages of preparing views for display. It can show you the exact cause of an animation hitch, which appears to the user as an interruption or jump in an animation that should be smooth. If Animation Hitches indicates that decoding an image takes too long and causes hitches, use this method to move the decoding work to the background.

This method creates a new image object and passes it to the completion handler. The new image is ready for efficient display by an image view. Assign the image this method creates to the [`image`](/documentation/uikit/uilistcontentconfiguration-swift.struct/image) property of an image view. If [`UIImageView`](/documentation/uikit/uiimageview) can render the image without decoding, this method passes the completion handler a valid image without further processing. If the system can’t decode the image, such as an image created from a [`CIImage`](/documentation/CoreImage/CIImage), the method passes `nil` to the completion handler`.`

UIKit doesn’t associate the prepared image with the original, or with any related variants from an asset catalog. If your app environment dynamically changes display traits, listen for changes in the trait environment and prepare new images when the environment changes.

```swift
```swift
```swift
```swift
```swift
```swift
func collectionView(_ collectionView: UICollectionView, prefetchItemsAt indexPaths: [IndexPath]) {
```
```
    for path in indexPaths {
        let item = models[path.item]
        if preparedImageCache.object(forKey: item.id) == nil {
            item.loadAsset()
            item.image.prepareForDisplay { [weak preparedImageCache] preparedImage in
                if let preparedImage = preparedImage {
                    preparedImageCache?.setObject(preparedImage, forKey: item.id)
                }
            }
        }
    }
}
```
```
```
```

## [See Also](/documentation/UIKit/UIImage/prepareForDisplay\(completionHandler:\)#see-also)

### [Loading images for display](/documentation/UIKit/UIImage/prepareForDisplay\(completionHandler:\)#Loading-images-for-display)

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
func preparingThumbnail(of: CGSize) -> UIImage?
```
```

Returns a new thumbnail image at the specified size.
```
```swift
```swift
```swift
func prepareThumbnail(of: CGSize, completionHandler: (UIImage?) -> Void)
```
```

Creates a thumbnail image at the specified size asynchronously on a background thread.
```
```