

- AVFoundation
- Media reading and writing
-  Exporting video to alternative formats 

Article

# Exporting video to alternative formats

Convert an existing movie file to a different format.

## Overview

To convert an existing movie file to a format that makes it compatible with other devices, you need to generate a new movie file based on the contents of the existing file. Though you can’t change the format of the saved video, you can create a new file in the desired format by following the steps outlined in this article.

Tip

If your app can save a movie directly from video capture, it’s more efficient to change the default format during capture by following the steps in Recording movies in alternative formats.

### Export a new video to the desired format

To export a video to a different format, begin with an AVAsset movie file and perform these steps:

1.  Choose an export preset from the list of Export Presets.

2.  Choose an export file type from the list of AVFileType presets.

3.  Verify that AVAssetExportSession can convert the movie from the input format to the output format you want.

4.  Create and configure an AVAssetExportSession instance, and then use it to perform the export.

The following example defines a method and then uses it to perform these steps:

```
func export(video: AVAsset,
            withPreset preset: String = AVAssetExportPresetHighestQuality,
            toFileType outputFileType: AVFileType = .mov,
            atURL outputURL: URL) async {

    // Check the compatibility of the preset to export the video to the output file type.
    guard await AVAssetExportSession.compatibility(ofExportPreset: preset,
                                                   with: video,
                                                   outputFileType: outputFileType) else {
        print("The preset can't export the video to the output file type.")
        return
    }

    // Create and configure the export session.
    guard let exportSession = AVAssetExportSession(asset: video,
                                                   presetName: preset) else {
        print("Failed to create export session.")
        return
    }
    exportSession.outputFileType = outputFileType
    exportSession.outputURL = outputURL

    // Convert the video to the output file type and export it to the output URL.
    await exportSession.export()
}

let video = // Your source AVAsset video. //
let outputURL = // The destination URL for your exported video. //

// Use a preset that encodes to H.264 to convert a video to the .mov file type,
// and asynchronously perform the export.
Task {
    await export(video: video,
                 withPreset: AVAssetExportPresetHighestQuality,
                 toFileType: .mov,
                 atURL: outputURL)
}
```

## See Also

### Media export

class AVAssetExportSession

An object that exports assets in a format that you specify using an export preset.

