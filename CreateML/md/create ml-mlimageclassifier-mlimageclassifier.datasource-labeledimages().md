

- Create ML
- MLImageClassifier
- MLImageClassifier.DataSource
-  labeledImages() 

Instance Method

# labeledImages()

Returns the labeled images represented by the data source.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 10.14+visionOS 1.0+

``` source
func labeledImages() throws -> [String : [URL]]
```

## Return Value

The labeled images that the data source represents, as a dictionary. The dictionary keys are the labels, while the dictionary values are arrays of images, represented as URLs, that correspond to the label.

## See Also

### Retrieving the data

case filesByLabel([String : [URL]])

Dictionary of labels to file URLs.

