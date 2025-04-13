

- Paravirtualized Graphics
- PGDisplay
-  modeList 

Instance Property

# modeList

The list of display modes that the virtual display supports.

Mac Catalyst 14.0+macOS 11.0+

``` source
var modeList: [PGDisplayMode] { get set }
```

**Required**

## Discussion

The maximum number of display modes is `128`. Setting this property updates the virtual graphics device’s supported mode list, and potentially forces it to change its current mode. The first time you set this property, the device simulates hot-plugging the display to the graphics device.

