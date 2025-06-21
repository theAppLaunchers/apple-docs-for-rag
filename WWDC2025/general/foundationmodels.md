Framework

# Foundation Models

Perform tasks with the on-device model that specializes in language understanding, structured output, and tool calling.

iOS 26.0+BetaiPadOS 26.0+BetaMac Catalyst 26.0+BetamacOS 26.0+BetavisionOS 26.0+Beta

## [Overview](/documentation/FoundationModels#overview)

The Foundation Models framework provides access to Apple’s on-device large language model that powers Apple Intelligence to help you perform intelligent tasks specific to your use case. The text-based on-device model identifies patterns that allow for generating new text that’s appropriate for the request you make, and it can make decisions to call code you write to perform specialized tasks.

Generate text content based on requests you make. The on-device model excels at a diverse range of text generation tasks, like summarization, entity extraction, text understanding, refinement, dialog for games, generating creative content, and more.

Generate entire Swift data structures with guided generation. With the `@Generable` macro, you can define custom data structures and the framework provides strong guarantees that the model generates instances of your type.

To expand what the on-device foundation model can do, use [`Tool`](/documentation/foundationmodels/tool) to create custom tools that the model can call to assist with handling your request. For example, the model can call a tool that searches a local or online database for information, or calls a service in your app.

To use the on-device language model, people need to turn on Apple Intelligence on their device. For a list of supported devices, see [Apple Intelligence](https://www.apple.com/apple-intelligence/).

For more information about acceptable usage of the Foundation Models framework, see [Acceptable use requirements for the Foundation Models framework](https://developer.apple.com/apple-intelligence/acceptable-use-requirements-for-the-foundation-models-framework).

## [Topics](/documentation/FoundationModels#topics)

### [Essentials](/documentation/FoundationModels#Essentials)

[

Generating content and performing tasks with Foundation Models](/documentation/foundationmodels/generating-content-and-performing-tasks-with-foundation-models)

Enhance the experience in your app by prompting an on-device large language model.

[

Improving safety from generative model output](/documentation/foundationmodels/improving-safety-from-generative-model-output)

Create generative experiences that appropriately handle sensitive inputs and respect people.

[

Adding intelligent app features with generative models](/documentation/foundationmodels/adding-intelligent-app-features-with-generative-models)

Build robust apps with guided generation and tool calling by adopting the Foundation Models framework.

```swift
```swift
```swift
class SystemLanguageModel
```
```

An on-device large language model capable of text generation tasks.
```
```swift
```swift
```swift
struct UseCase
```
```

A type that represents the use case for prompting.
```

### [Prompting](/documentation/FoundationModels#Prompting)

```swift
```swift
```swift
```swift
class LanguageModelSession
```
```

An object that represents a session that interacts with a large language model.
```
```swift
```swift
```swift
struct Instructions
```
```

Instructions define the model’s intended behavior on prompts.
```
```swift
```swift
```swift
struct Prompt
```
```

A prompt from a person to the model.
```
```swift
```swift
```swift
struct Transcript
```
```

A transcript that documents interactions with a language model.
```
```swift
```swift
```swift
struct GenerationOptions
```
```

Options that control how the model generates its response to a prompt.
```
```

### [Guided generation](/documentation/FoundationModels#Guided-generation)

[

Generating Swift data structures with guided generation](/documentation/foundationmodels/generating-swift-data-structures-with-guided-generation)

Create robust apps by describing output you want programmatically.

```swift
```swift
```swift
protocol Generable
```
```

A type that the model uses when responding to prompts.
```

### [Tool calling](/documentation/FoundationModels#Tool-calling)

[

Expanding generation with tool calling](/documentation/foundationmodels/expanding-generation-with-tool-calling)

Build tools that enable the model to perform tasks that are specific to your use case.

[

Generate dynamic game content with guided generation and tools](/documentation/foundationmodels/generate-dynamic-game-content-with-guided-generation-and-tools)

Make gameplay more lively with AI generated dialog and encounters personalized to the player.

```swift
```swift
```swift
protocol Tool
```
```

A tool that a model can call to gather information at runtime or perform side effects.
```

### [Feedback](/documentation/FoundationModels#Feedback)

```swift
```swift
```swift
```swift
struct LanguageModelFeedbackAttachment
```
```

Feedback appropriate for attaching to Feedback Assistant.
```
```

Beta Software

This documentation contains preliminary information about an API or technology in development. This information is subject to change, and software implemented according to this documentation should be tested with final operating system software.

[Learn more about using Apple's beta software](https://developer.apple.com/support/beta-software/)