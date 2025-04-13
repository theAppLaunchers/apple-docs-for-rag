

- VisionKit
- ImageAnalysisInteraction
- ImageAnalysisInteraction.InteractionTypes
-  visualLookUp 

Type Property

# visualLookUp

An option that presents a button for more information on any subjects the framework recognizes in the image.

iOS 16.0+iPadOS 16.0+Mac Catalyst 17.0+visionOS 1.0+

``` source
static let visualLookUp: ImageAnalysisInteraction.InteractionTypes
```

## Discussion

When the framework identifies something familiar in an image that it can provide more information about (see ImageAnalysisInteraction.Subject), it offers a button in the bottom-right corner of the view. When people tap the button, a modal sheet appears that offers info about the subject. For example, if the image contains a dog, the modal sheet describes the dog’s breed and provides a relevant web URL where people can read more about the breed.

VisionKit supports Visual Look Up when it recognizes the following subjects:

- Plants and flowers

- Animals, such as cats, dogs, birds, reptiles, and insects

- Places, such as constructed landmarks, sculptures, and natural landmarks

- Art and media, such as paintings, books, and album covers

- Food, such as prepared dishes and desserts

- Symbols, such as laundry care labels and vehicle dashboard indicators

## See Also

### Specifying types of interactions

static let automatic: ImageAnalysisInteraction.InteractionTypes

An option that enables interaction with any type of text, symbols, or subjects that the framework recognizes.

static let textSelection: ImageAnalysisInteraction.InteractionTypes

An option that enables text selection, copying, and translating.

static let dataDetectors: ImageAnalysisInteraction.InteractionTypes

An option that enables interaction with text of certain formats, such as URLs, email addresses, and physical addresses.

static let imageSubject: ImageAnalysisInteraction.InteractionTypes

An option that enables people to use a long-press gesture on a subject in an image to separate it from the background.

static let automaticTextOnly: ImageAnalysisInteraction.InteractionTypes

An option that enables all interaction types except image subjects and Visual Look Up.

