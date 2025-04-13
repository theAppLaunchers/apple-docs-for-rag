

- Xcode
- Performance and metrics
- Reducing your app’s size
-  Doing basic optimization to reduce your app’s size 

Article

# Doing basic optimization to reduce your app’s size

Adjust your project’s build settings, and use technologies like asset catalogs early in your app’s development life cycle.

## Overview

After you’ve measured your app’s size, you can do some basic optimizations to make it smaller. If you’re starting a new app project, create a solid foundation for your app by adopting technologies like asset catalogs. By adopting these technologies early, you may reduce the possibility of needing costly optimizations later.

### Check your target’s build settings for release builds

After you’ve measured your app’s size, you may discover that it’s larger than you expected. This can happen if you’ve unintentionally changed the project’s settings. The default optimization level for the `Release` configuration is `Fastest, Smallest [-Os]`, which can make your compiled binary very small. Check your target’s build settings, and be sure you’re using this optimization level.

### Identify and remove unused assets

Next, look inside your app’s IPA file to find out if your app contains unused assets or unnecessary files. First follow the steps described in Reducing your app’s size to create a *thinned* IPA file for each of your app’s variants. Then do the following:

1.  Open Finder and navigate to the IPA file that you want to inspect.

2.  Change the extension of the IPA file to ZIP. (An IPA file is just a ZIP archive that has a particular structure when unzipped.)

3.  Unzip the file to show the app bundle inside the Payloads directory. You can either open the ZIP file in Finder, or run `unzip -lv /path/to/your/app.zip` in the Terminal app.

4.  Right-click the app bundle, and choose Show Package Contents.

Where appropriate, remove any unused files from your Xcode project or targets. For example, make sure you’re not adding your app’s `README` file to a target, remove any unused image assets and header files, and so on.

### Adopt asset catalogs for your app’s resources

Asset catalogs allow Xcode and the App Store to optimize your app’s assets, which can significantly reduce the size of your app. Use asset catalogs instead of putting your assets in your app bundle directly; then do the following:

- Tag each asset—for example images, textures, or data assets—with relevant metadata to indicate which devices the asset is for. Doing so maximizes the size reduction that app thinning provides, which can be significant for apps with assets that aren’t required by every device.

- Define a resizable center area of an image with optional end caps to reduce its size. To learn more, see Add a resizable area to an image.

- Set the level of compression for each asset type. In particular, for apps using wide color images or textures with Metal, consider the `ASTC` compression options. For more information on compressing wide color images or textures, see Working With Wide Color.

To learn more about asset catalogs, see Adding images to your Xcode project and Managing assets with asset catalogs, and watch App Thinning in Xcode.

### Use asset files for data that ships with your app

As you inspect your app’s IPA file, you may find that your app’s binaries take up a lot of space. If you ship your app with data, consider using asset files instead of putting the data into your code. For example, use a property list for bundling any data with your app instead of using strings in code. Also, some developers use source code to ship other resources; for example, images. Consider using asset files instead, and put them in an asset catalog. Moving data and assets out of your source code and into asset files significantly reduces the size of your app’s binary. It also allows App Store Connect to more efficiently compress your app.

## See Also

### Size optimization

Doing advanced optimization to further reduce your app’s size

Optimize your app’s asset files, adopt on-demand resources, and reduce the size of app updates.

