

- Automator
- AMAction
-  selectedInputType 

Instance Property

# selectedInputType

The type of input, in UTI format, of the input received by the action.

Mac Catalyst 14.0+macOS 10.6+

``` source
var selectedInputType: String? { get set }
```

## Discussion

Getting this value provides the type of input the action is configured to accept. For example, your action may have the ability to accept files and folders, or documents, depending on how it’s configured and what action precedes it in the workflow.

The input types the action supports are specified in the action’s `Info.plist` file. By default, this property defaults to first input type in the `Info.plist` file.

Through its interface, the action can could be configured to allow the user to specify the type of input the action should accept. For example, a Contacts action may allow the user to configure whether the action accepts people or groups. In cases like this, set this property value to explicitly indicate the input type the action accepts. Setting this value to accurately reflect the appropriate type of input helps Automator determine whether the input the action receives is compatible, or can be made compatible, with the action.

## See Also

### Getting Action Information

var name: String

The name of the action.

var progressValue: CGFloat

A float value between 0 and 1, which indicates how far along the action is while processing.

var ignoresInput: Bool

A Boolean value that indicates whether the action acts upon its input or the input is ignored.

var output: Any?

The action’s output.

var selectedOutputType: String?

The type of output, in UTI format, of the output to be produced by the action.

var isStopped: Bool

A Boolean value that indicates whether the user clicked the stop button on the parent workflow.

