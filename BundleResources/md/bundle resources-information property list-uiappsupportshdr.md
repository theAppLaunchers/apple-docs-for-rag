

- Bundle Resources
- Information Property List
-  UIAppSupportsHDR 

Property List Key

# UIAppSupportsHDR

A Boolean value that indicates whether the app supports HDR mode on Apple TV 4K.

tvOS 11.2+

## Details 

Name  
Supports HDR color mode

Type  

boolean

## Attributes 

Default: `YES`

## Discussion

If you set this key to `YES`, Apple TV 4K remains in HDR mode when launching the app. If you set this key to `NO`, Apple TV switches to SDR mode before launching the app, and switches back to HDR mode after the app resigns. The default value for this key is `YES`.

On Apple TV 4K, HDR mode uses the GPU to compose the content that appears onscreen. GPU-bound apps, such as games, can access more of the GPU by setting this key to `NO`. When an app switches between HDR and SDR modes, color flashing might appear onscreen, so only opt out when absolutely necessary.

## See Also

### Graphics

NSHighResolutionCapable

A Boolean value indicating whether the Cocoa app supports high-resolution displays.

**Name:** High Resolution Capable

NSSupportsAutomaticGraphicsSwitching

A Boolean value indicating whether an OpenGL app may utilize the integrated GPU.

**Name:** Supports Automatic Graphics Switching

GPUEjectPolicy

The preferred system action when an external GPU is connected from the system.

GPUSelectionPolicy

The app’s preference for whether it wants to use external graphics processors.

