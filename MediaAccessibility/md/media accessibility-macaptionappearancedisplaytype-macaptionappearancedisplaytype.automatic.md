

- Media Accessibility
- MACaptionAppearanceDisplayType
-  MACaptionAppearanceDisplayType.automatic 

Case

# MACaptionAppearanceDisplayType.automatic

If the language of the audio track differs from the system locale, then captions matching the system locale should be displayed (if available). If the language of the audio and the language of the system locale match, no captions are shown.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+macOS 10.9+tvOS 17.0+visionOS 1.0+

``` source
case automatic
```

## See Also

### Constants

case forcedOnly

Do not display captions unless they are forced for translation.

case alwaysOn

The most robust available captioning track should always be displayed, whether subtitles, CC, or SDH. This option is selected by a switch labeled “Closed Captions + SDH” (on the Subtitles & Captioning page of iOS) and “Prefer Closed Captions and SDH” checkbox (on the Captions pane of the Accessibility options in macOS).

