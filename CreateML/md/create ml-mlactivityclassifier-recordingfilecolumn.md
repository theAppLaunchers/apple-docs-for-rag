

- Create ML
- MLActivityClassifier
-  recordingFileColumn 

Instance Property

# recordingFileColumn

The name of the column that contains the data files the activity classifier used during its training session.

macOS 10.15+

``` source
var recordingFileColumn: String
```

## Discussion

This property reflects the name of the data table column or annotation file column the training session used to locate each activity’s data files.

Note

The MLActivityClassifier instance provides a default name if you trained it with a data source that’s set to MLActivityClassifier.DataSource.labeledDirectories(at:).

Changing the value of this property doesn’t retrain the model or affect its behavior.

## See Also

### Inspecting an activity classifier model

var model: MLModel

The underlying Core ML model of the activity classifier stored in memory.

let modelParameters: MLActivityClassifier.ModelParameters

The model configuration parameters the activity classifier used during its training session.

var featureColumns: [String]

The names of the feature columns the activity classifier used during its training session.

var labelColumn: String

The name of the label column the activity classifier used during its training session.

