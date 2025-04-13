

- ClassKit Catalog API
- Context
- Context.Metadata
-  Context.Metadata.PresentablePaths 

Dictionary

# Context.Metadata.PresentablePaths

The identifier path of a context to use as one of the presentable paths in a context’s metadata.

ClassKit 1.0+

``` source
object Context.Metadata.PresentablePaths
```

## Properties

`path`

`[string]`

An array of strings that locates a context within a context hierarchy. Each string in the array represents a context, starting from the main app context, through any ancestor contexts, down to the child context. Use the identified context as a presentable path.

## Attributes 

Possible types:

## Discussion

Use one or more presentable paths in a context’s Context.Metadata to supplement your app’s native context hierarchy and affect the way the catalog displays your content. For example, your app might define four contexts as children of the main app context:

- `[“com.example.Quizzer”, “Algebra Quiz”]`

- `[“com.example.Quizzer”, “Fractions Quiz”]`

- `[“com.example.Quizzer”, “Spelling Quiz”]`

- `[“com.example.Quizzer”, “Grammar Quiz”]`

You can organize these items in your catalog by using Create or Replace Contexts to create new contexts that don’t exist in your app:

- `[“com.example.Quizzer”, “Math Quizzes”]`

- `[“com.example.Quizzer”, “Language Quizzes”]`

Then, by setting the new Math Quizzes context as a presentable path for the algebra and fractions quizzes, and the Language Quizzes context as a presentable path for the spelling and grammar quizzes, you help teachers to more easily understand the organization of your content.

The same rules that exist for contexts in your app apply to contexts that you create for use as presentable paths. For example, the system limits all contexts to a maximum of 2000 child contexts.

