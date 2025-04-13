

- AVFoundation
- Media reading and writing
- AVAssetExportSession
-  Export Presets 

API Collection

# Export Presets

Configure an export session to output media in standard sizes and formats.

## Overview

Use the preset name constants to initialize an instance of AVAssetExportSession.

## Topics

### Quality Presets

let AVAssetExportPresetLowQuality: String

A preset to export a low-quality movie file.

let AVAssetExportPresetMediumQuality: String

A preset to export a medium-quality movie file.

let AVAssetExportPresetHighestQuality: String

A preset to export a high-quality movie file.

let AVAssetExportPresetHEVCHighestQuality: String

A preset to export the highest available video quality and HEVC video compression.

let AVAssetExportPresetHEVCHighestQualityWithAlpha: String

A preset to export the highest available video quality and HEVC video compression with alpha.

### Size Presets

let AVAssetExportPreset640x480: String

A preset to export a 640 by 480 movie that contains H.264 video and AAC audio.

let AVAssetExportPreset960x540: String

A preset to export a 960 by 540 movie that contains H.264 video and AAC audio.

let AVAssetExportPreset1280x720: String

A preset to export a 1280 by 720 movie that contains H.264 video and AAC audio.

let AVAssetExportPreset1920x1080: String

A preset to export a 1920 by 1080 movie that contains H.264 video and AAC audio.

let AVAssetExportPreset3840x2160: String

A preset to export a 3840 by 2160 movie that contains H.264 video and AAC audio.

### HEVC Size Presets

let AVAssetExportPresetHEVC1920x1080: String

A preset to export a 1920 by 1080 movie that contains HEVC video and AAC audio.

let AVAssetExportPresetHEVC3840x2160: String

A preset to export a 3840 by 2160 movie that contains HEVC video and AAC audio.

let AVAssetExportPresetHEVC1920x1080WithAlpha: String

A preset to export a 1920 by 1080 movie that contains HEVC video with alpha and AAC audio.

let AVAssetExportPresetHEVC3840x2160WithAlpha: String

A preset to export a 3840 by 2160 movie that contains HEVC video with alpha and AAC audio.

let AVAssetExportPresetHEVC7680x4320: String

A preset to export a 7680 by 4320 movie that contains HEVC video and AAC audio.

### MV-HEVC Presets

let AVAssetExportPresetMVHEVC960x960: String

A preset to export a 960 by 960 movie that contains MV-HEVC video and AAC audio.

let AVAssetExportPresetMVHEVC1440x1440: String

A preset to export a 1440 by 1440 movie that contains MV-HEVC video and AAC audio.

### M4V Presets

let AVAssetExportPresetAppleM4V480pSD: String

A preset to export a 480p Standard Definition format suitable for playing on Apple devices.

let AVAssetExportPresetAppleM4V720pHD: String

A preset to export a 720p High Definition format suitable for playing on Apple devices.

let AVAssetExportPresetAppleM4V1080pHD: String

A preset to export a 1080p High Definition format suitable for playing on Apple devices.

let AVAssetExportPresetAppleM4ViPod: String

A preset to export a format suitable for playing on an iPod.

let AVAssetExportPresetAppleM4VAppleTV: String

A preset to export a format suitable for playing on Apple TV.

let AVAssetExportPresetAppleM4VCellular: String

A preset to export a format suitable for playing on Apple devices when it streams over a cellular network.

let AVAssetExportPresetAppleM4VWiFi: String

A preset to export a format suitable for playing on Apple devices it streams over a WiFi network.

### Apple ProRes Presets

let AVAssetExportPresetAppleProRes422LPCM: String

A preset to export a QuickTime movie with Apple ProRes 422 video and LPCM audio.

let AVAssetExportPresetAppleProRes4444LPCM: String

A preset to export a QuickTime movie with Apple ProRes 4444 video and LPCM audio.

### Passthrough Presets

let AVAssetExportPresetPassthrough: String

A preset to export the asset in its current format, unless otherwise prohibited.

### Audio-only Presets

let AVAssetExportPresetAppleM4A: String

A preset to export an audio-only MPEG 4 Audio file with appropriate iTunes gapless playback data.

## See Also

### Creating an Export Session

init?(asset: AVAsset, presetName: String)

Creates an export session with a preset configuration.

