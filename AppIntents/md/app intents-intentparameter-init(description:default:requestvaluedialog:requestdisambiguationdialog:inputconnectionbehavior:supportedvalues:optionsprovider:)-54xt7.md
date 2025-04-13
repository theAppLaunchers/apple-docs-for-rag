

- App Intents
- IntentParameter
-  init(description:default:requestValueDialog:requestDisambiguationDialog:inputConnectionBehavior:supportedValues:optionsProvider:) 

Initializer

# init(description:default:requestValueDialog:requestDisambiguationDialog:inputConnectionBehavior:supportedValues:optionsProvider:)

Creates an app intent parameter with a list of selectable options.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+watchOS 11.0+

``` source
convenience init(
    description: LocalizedStringResource? = nil,
    default defaultValue: Value.UnwrappedType? = nil,
    requestValueDialog: IntentDialog? = nil,
    requestDisambiguationDialog: IntentDialog? = nil,
    inputConnectionBehavior: InputConnectionBehavior = .default,
    supportedValues: [Value.ValueType] = Array(Value.ValueType.allCases),
    optionsProvider: OptionsProvider
) where OptionsProvider : DynamicOptionsProvider, Value.ValueType == OptionsProvider.DefaultValue.ValueType
```

Available when `Value` conforms to `_IntentValue`, `Value` conforms to `Sendable`, `Value.ValueType` conforms to `AppEntity`, and `Value.ValueType` conforms to `AppEnum`.

## Parameters 

`description`  

Additional details about this parameter.

`defaultValue`  

The default value for this parameter. People can specify a different value.

`requestValueDialog`  

A prompt that asks a person to provide the parameter value.

`requestDisambiguationDialog`  

A prompt that asks a person to choose among possible parameter values.

`inputConnectionBehavior`  

An enum that indicates how this parameter receives the output from a preceding app intent.

`supportedValues`  

A list of selectable options for this parameter.

`optionsProvider`  

An object that determines selectable options for this parameter.

