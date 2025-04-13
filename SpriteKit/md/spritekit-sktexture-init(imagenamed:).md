

- SpriteKit
- SKTexture
-  init(imageNamed:) 

Initializer

# init(imageNamed:)

Create a new texture object from an image file stored in the app bundle.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

``` source
convenience init(imageNamed name: String)
```

## Parameters 

`name`  

The name of the image file.

## Return Value

A new texture object.

## Mentioned in 

Loading and Using Textures

About Texture Atlases

## Discussion

The new texture object is initialized with the name of the image file and then control returns immediately to your game. Sprite Kit loads and prepares the texture data when it is needed by your game.

When loading the texture data, Sprite Kit searches the app bundle for an image file with the specified filename. If a matching image file cannot be found, Sprite Kit searches for the texture in any texture atlases stored in the app bundle. If the specified image does not exist anywhere in the bundle, Sprite Kit creates a placeholder texture image.

