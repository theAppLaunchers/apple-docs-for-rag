*   [Foundation Models](/documentation/foundationmodels)
*   Generating content and performing tasks with Foundation Models

Article

# Generating content and performing tasks with Foundation Models

Enhance the experience in your app by prompting an on-device large language model.

## [Overview](/documentation/FoundationModels/generating-content-and-performing-tasks-with-foundation-models#overview)

The Foundation Models framework lets you tap into the on-device large models at the core of Apple Intelligence. You can enhance your app by using generative models to create content or perform tasks. The framework supports language understanding and generation based on models capabilities like text extraction and summarization that you can use to:

*   Generate a title, description, or tags for content
    
*   Generate a list of search suggestions relevant to your app
    
*   Transform product reviews into structured data you can visualize
    
*   Invoke your own tools to assist the model with performing app-specific tasks
    

For design guidance, see Human Interface Guidelines > Technologies > [Generative AI](https://developer.apple.com/design/human-interface-guidelines/generative-ai).

## [Check for availability](/documentation/FoundationModels/generating-content-and-performing-tasks-with-foundation-models#Check-for-availability)

Check model availability by creating an instance of [`SystemLanguageModel`](/documentation/foundationmodels/systemlanguagemodel) with the [`default`](/documentation/foundationmodels/systemlanguagemodel/default) property. The [`default`](/documentation/foundationmodels/systemlanguagemodel/default) property provides the same model Apple Intelligence uses, and supports text generation.

Model availability depends on device factors like:

*   The device must support Apple Intelligence.
    
*   The device must have Apple Intelligence turned on in System Settings.
    
*   The device must have sufficient battery and not be in Game Mode.
    

Note

It can take some time for the model to download and become available when a person turns on Apple Intelligence. Models may not be available if the device is in low battery mode or it becomes too warm.

Always verify model availability first, and plan for a fallback experience in case the model is unavailable.

```swift
```swift
```swift
```swift
```swift
```swift
struct GenerativeView: View {
```
```
    // Create a reference to the system language model.
    private var model = SystemLanguageModel.default
    var body: some View {
        switch model.availability {
        case .available:
            // Show your intelligence UI.
        case .unavailable(.deviceNotEligible):
            // Show an alternative UI.
        case .unavailable(.appleIntelligenceNotEnabled):
            // Ask the person to turn on Apple Intelligence.
        case .unavailable(.modelNotReady):
            // The model isn't ready because it's downloading or because of other system reasons.
        case .unavailable(let other):
            // The model is unavailable for an unknown reason.
        }
    }
}
```
```
```
```

## [Create a session](/documentation/FoundationModels/generating-content-and-performing-tasks-with-foundation-models#Create-a-session)

After confirming that the model is available, create a [`LanguageModelSession`](/documentation/foundationmodels/languagemodelsession) object to call the model. For a single-turn interaction, create a new session each time you call the model:

```swift

```swift
// Create a session with the system model.
```swift
```swift
let session = LanguageModelSession()
```
```
```

```

For a multiturn interaction — where the model retains some knowledge of what it produced — reuse the same session each time you call the model.

## [Provide a prompt to the model](/documentation/FoundationModels/generating-content-and-performing-tasks-with-foundation-models#Provide-a-prompt-to-the-model)

A [`Prompt`](/documentation/foundationmodels/prompt) is an input that the model responds to. Prompt engineering is the art of designing high-quality prompts so that the model generates a best possible response for the request you make. A prompt can be as short as “hello”, or as long as multiple paragraphs. The process of designing a prompt involves a lot of exploration to discover the best prompt, and involves optimizing prompt length and writing style.

When thinking about the prompt you want to use in your app, consider using conversational language in the form of a question or command. For example, “What’s a good month to visit Paris?” or “Generate a food truck menu.”

Write prompts that focus on a single and specific task, like “Write a profile for the dog breed Siberian Husky”. When a prompt is long and complicated, the model takes longer to respond, and may respond in unpredictable ways. If you have a complex generation task in mind, break the task down into a series of specific prompts.

You can refine your prompt by telling the model exactly how much content it should generate. A prompt like, “Write a profile for the dog breed Siberian Husky” often takes a long time to process as the model generates a full multi-paragraph essay. If you specify “using three sentences”, it speeds up processing and generates a concise summary. Use phrases like “in a single sentence” or “in a few words” to shorten the generation time and produce shorter text.

```swift

```swift
// Generate a longer response for a specific command.
```swift
```swift
let simple = "Write me a story about pears."
```
```
// Quickly generate a concise response.
```swift
```swift
let quick = "Write the profile for the dog breed Siberian Husky using three sentences."
```
```
```

```

## [Provide instructions to the model](/documentation/FoundationModels/generating-content-and-performing-tasks-with-foundation-models#Provide-instructions-to-the-model)

[`Instructions`](/documentation/foundationmodels/instructions) help steer the model in a way that fits the use case of your app. The model obeys prompts at a lower priority than the instructions you provide. When you provide instructions to the model, consider specifying details like:

*   What the model’s role is; for example, “You are a mentor,” or “You are a movie critic”.
    
*   What the model should do, like “Help the person extract calendar events,” or “Help the person by recommending search suggestions”.
    
*   What the style preferences are, like “Respond as briefly as possible”.
    
*   What the possible safety measures are, like “Respond with ‘I can’t help with that’ if you’re asked to do something dangerous”.
    

Use content you trust in instructions because the model follows them more closely than the prompt itself. When you initialize a session with instructions, it affects all prompts the model responds to in that session. Instructions can also include example responses to help steer the model. When you add examples to your prompt, you provide the model with a template that shows the model what a good response looks like.

## [Generate a response](/documentation/FoundationModels/generating-content-and-performing-tasks-with-foundation-models#Generate-a-response)

To call the model with a prompt, call [`respond(to:options:isolation:)`](/documentation/foundationmodels/languagemodelsession/respond\(to:options:isolation:\)-4z2jz) on your session. The response call is asynchronous because it may take a few seconds for Foundation Models to generate the response.

```swift
```swift
```swift
```swift
```swift
```swift
let instructions = """
```
```
    Suggest five related topics. Keep them concise (three to seven words) and make sure they \
    build naturally from the person's topic.
    """
```swift
```swift
let session = LanguageModelSession(instructions: instructions)
```
```
```swift
```swift
let prompt = "Making homemade bread"
```
```
```swift
```swift
let response = try await session.respond(to: prompt)
```
```
```
```
```
```

Note

A session can only handle a single request at a time, and causes a runtime error if you call it again before the previous request finishes. Check [`isResponding`](/documentation/foundationmodels/languagemodelsession/isresponding) to verify the session is done processing the previous request before sending a new one.

Instead of working with raw string output from the model, the framework offers guided generation to generate a custom Swift data structure you define. For more information about guided generation, see [Generating Swift data structures with guided generation](/documentation/foundationmodels/generating-swift-data-structures-with-guided-generation).

When you make a request to the model, you can provide custom tools to help the model complete the request. If the model determines that a [`Tool`](/documentation/foundationmodels/tool) can assist with the request, the framework calls your [`Tool`](/documentation/foundationmodels/tool) to perform additional actions like retrieving content from your local database. For more information about tool calling, see [Expanding generation with tool calling](/documentation/foundationmodels/expanding-generation-with-tool-calling)

## [Tune generation options and optimize performance](/documentation/FoundationModels/generating-content-and-performing-tasks-with-foundation-models#Tune-generation-options-and-optimize-performance)

To get the best results for your prompt, experiment with different generation options. [`GenerationOptions`](/documentation/foundationmodels/generationoptions) affects the runtime parameters of the model, and you can customize them for every request you make.

```swift

```swift
// Customize the temperature to increase creativity.
```swift
```swift
let options = GenerationOptions(temperature: 2.0)
```
```
```swift
```swift
let session = LanguageModelSession()
```
```
```swift
```swift
let prompt = "Write me a story about coffee."
```
```
```swift
```swift
let response = try await session.respond(
```
```
    to: prompt,
    options: options
)
```

```

When you test apps that use the framework, use Xcode Instruments to understand more about the requests you make, like the time it takes to perform a request. When you make a request, you can access the [`Transcript`](/documentation/foundationmodels/transcript) entries that describe the actions the model takes during your [`LanguageModelSession`](/documentation/foundationmodels/languagemodelsession).

## [See Also](/documentation/FoundationModels/generating-content-and-performing-tasks-with-foundation-models#see-also)

### [Essentials](/documentation/FoundationModels/generating-content-and-performing-tasks-with-foundation-models#Essentials)

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

Beta
```
```swift
```swift
```swift
struct UseCase
```
```

A type that represents the use case for prompting.

Beta
```