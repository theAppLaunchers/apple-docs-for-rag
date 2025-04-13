

- TV Services
- TVTopShelfItem
-  setImageURL(\_:for:) 

Instance Method

# setImageURL(\_:for:)

Associates an image with the current item.

tvOS 13.0+

``` source
func setImageURL(
    _ imageURL: URL?,
    for traits: TVTopShelfItem.ImageTraits
)
```

## Parameters 

`imageURL`  

The URL of the image. Specify `nil` to remove the image with the specified traits from the item.

`traits`  

The traits that describe the image.

## Discussion

Use this method to assign images to a top shelf item. For most items, the system displays only an image. For carousel items, the system initially displays an image, but switches to the preview video when the navigation focus stops on the item.

The system always chooses the image whose traits match the target device.

## See Also

### Providing an Image for the Item

func imageURL(for: TVTopShelfItem.ImageTraits) -> URL?

Returns an image associated with the current item.

struct ImageTraits

Constants describing the image format.

