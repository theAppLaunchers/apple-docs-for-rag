

- App Clips
-  Preparing multiple App Clip Codes for production 

Article

# Preparing multiple App Clip Codes for production

Prepare your App Clip Codes to send to a professional printing service.

## Overview

After you create your App Clip Codes, you can print them yourself, or work with a professional printing service — for example, RR Donnelley. However, if you have a lot of App Clip Codes, printing them yourself doesn’t scale well, and you’ll have more success working with a professional printing service.

Because you can’t see which invocation URL your App Clip Code contains just by looking at it, you need to keep track of your SVG files and their corresponding URLs. Careful file management, versioning, and change tracking are key to avoiding faulty print runs.

For additional information, see Human Interface Guidelines > App Clips > Printing Guidelines.

### Map SVG filenames to invocation URLs

In general, it’s up to you to decide how to keep track of changes and which SVG files map to which invocation URLs. In most cases, a *mapping file* that uses the comma-separated values (CSV) file format is the preferred option.

To reduce the risk of human error and simplify change tracking, consider using a single mapping file to create your SVG files before sending them to a printing service.

If you’re working with RR Donnelley to produce App Clip Codes:

- Create a ZIP file that contains the SVG files for your App Clip Codes and the mapping file in its root folder.

- The mapping file must be a CSV file with one field named `SVG File Name` and another named `URL`, with each row representing one App Clip Code.

- The ZIP file may contain up to 10,000 SVG files, and the mapping file may contain up to 10,000 corresponding entries.

- The maximum length for any filename (ZIP file, SVG files, or mapping file) is 188 characters.

The following code shows the contents of a mapping file with entries for two App Clip Codes:

```
SVG File Name, URL
AppClipCode1.svg, https://example.com
AppClipCode2.svg, https://appclip.example.com/
```

## See Also

### App Clip Codes

Creating App Clip Codes

Help users discover your App Clip by using an NFC-integrated or scan-only App Clip Code.

Interacting with App Clip Codes in AR

Display content and provide services in an AR experience with App Clip Codes.

