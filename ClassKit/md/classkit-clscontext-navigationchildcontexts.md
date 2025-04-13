

- ClassKit
- CLSContext
-  navigationChildContexts 

Instance Property

# navigationChildContexts

The child contexts that a user can navigate to from this context in the Schoolwork app.

iOS 14.5+iPadOS 14.5+Mac Catalyst 14.5+macOS 11.3+visionOS 1.0+

``` source
var navigationChildContexts: [CLSContext] { get }
```

## Discussion

A given context exists at exactly one place in your app’s context hierarchy. However, you might want to provide multiple ways to navigate to a context. For example, you might define a set of quiz contexts as children of your app’s main context:

- Algebra quiz

- Fractions quiz

- Spelling quiz

- Grammar quiz

In addition to providing a flat list, you might want to group these tasks according one or more criteria. For example, you can group by subject:

- Math quizzes — Contains algebra and fractions quizzes.

- Language quizzes — Contains spelling and grammar quizzes.

You can also group by difficulty level:

- Beginner Quizzes — Contains fractions and spelling quizzes.

- Advanced quizzes — Contains algebra and grammar quizzes.

If you create contexts for the math and language, and beginner and advanced groups, and then add child quizzes to each by defining unique identifierPath values, you’ll create new contexts inside each group. This results in three distinct contexts — the original from the flat list, plus one for each group — to represent each individual quiz.

After creating the grouping contexts, you need to define only one context for each quiz. To do this, update each group’s navigationChildContexts collection to indicate all the children that you can navigate to from that group. Use addNavigationChildContext(_:) to add contexts and removeNavigationChildContext(_:) to remove them.

```
// Group by subject.
mathQuizzes.addNavigationChildContext(algebraQuiz)
mathQuizzes.addNavigationChildContext(fractionsQuiz)
languageQuizzes.addNavigationChildContext(spellingQuiz)
languageQuizzes.addNavigationChildContext(grammarQuiz)

// Group the same set of original quizzes by difficulty.
beginnerQuizzes.addNavigationChildContext(fractionsQuiz)
beginnerQuizzes.addNavigationChildContext(spellingQuiz)
advancedQuizzes.addNavigationChildContext(algebraQuiz)
advancedQuizzes.addNavigationChildContext(grammarQuiz)

```

## See Also

### Creating a context presentation hierarchy

func addNavigationChildContext(CLSContext)

Adds a child context that users can navigate to from this context.

func removeNavigationChildContext(CLSContext)

Removes the specified context as a presentable child of this context.

