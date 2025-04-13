

- Create ML
- MLImageClassifier
- MLImageClassifier.DataSource
-  MLImageClassifier.DataSource.labeledDirectories(at:) 

Case

# MLImageClassifier.DataSource.labeledDirectories(at:)

An image classifier data source that uses the directory structure to label images.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 10.14+visionOS 1.0+

``` source
case labeledDirectories(at: URL)
```

## Discussion

Use this case to create a data source based on a directory structure on disk that contains your training images. The associated value is a URL that represents a directory with subdirectories that are named as the labels for your images. Each subdirectory should contain the images associated with the label for which that subdirectory is named.

For example, you might initialize a data source with a file URL that indicates a directory called `Training Data` that contains subdirectories called `Elephant` and `Cheetah`. The subdirectory `Cheetah`, in turn, contains images of cheetahs, with names like `Image001.png`, `Image02.jpg`, and so on, while the subdirectory `Elephant` contains images of elephants, called `Image545.jpg`, `Image657.png`, and so on. The individual image names aren’t important in this case because the directory that an image appears in indicates the image’s label.

If you want to create a data source with labels based on file names, use MLImageClassifier.DataSource.labeledFiles(at:) instead.

## See Also

### Creating a data source

case labeledFiles(at: URL)

An image classifier data source that uses file names to label images.

