# AppIntentsTesting  
  
- AppIntentsTesting  
-  App Intents Testing  
  
Framework  
  
# App Intents Testing  
  
iOS 27.0+ iPadOS 27.0+ Mac Catalyst 27.0+ macOS 27.0+ tvOS 27.0+ visionOS 27.0+ watchOS 27.0+  
  
## Overview  
  
The App Intents framework allows you to integrate your app with system features like Siri, Shortcuts, or Spotlight. Use App Intents Testing to run and test your app intents, entities, enums, and query logic out-of-process — the same way Siri or Shortcuts perform them. Additionally, with App Intents Testing you can create tests that verify your app’s integration with system features like Siri or Spotlight. The framework provides type-erased APIs that let you reference intents by name, set their parameters, and run them without linking against your app target.  
  
## Topics  
  
### Essentials  
  
Testing your App Intents code  
  
Evaluate intents, entities, and queries, and verify your integration with system features like Spotlight and Siri.  
  
### Intents, entities, enums, and queries  
  
struct IntentDefinitions  
  
A collection of definitions that catalog your app’s intents, enums, entities, and queries.  
  
### Intent and query result verification  
  
struct ResolvedIntentResult  
  
A type-safe result from performing an app intent.  
  
struct ResolvedValueQueryResult  
  
The result of an intent value query.  
  
### Entity annotation testing  
  
struct ViewAnnotation  
  
The onscreen context you provide to the system by annotating a view with an app entity.  
  
### Intermediate types  
  
struct AnyAppIntent  
  
A type-erased, intermediate representation of an app intent for testing purposes.  
  
struct AnyAppEntity  
  
A type-erased, intermediate representation of your app entity for testing purposes.  
  
struct AnyEntityQuery  
  
A type-erased, intermediate representation of your entity query for testing purposes.  
  
struct AnyAppEnum  
  
A type-erased representation of an app enumeration that provides dynamic enumeration value access.  
  
struct AnyTransientAppEntity  
  
A type-erased representation of a transient app entity that provides dynamic property access.  
  
Supporting types  
  
protocol AppIntentTypeDefinition  
  
A protocol that associates a definition type with its corresponding instance type.  
  
struct DynamicPropertyPath  
  
A type-safe, dynamic path to access nested intent values.  
  
struct DynamicPropertyPathCollection  
  
Indexed result items from an intent value query.  
  
struct IntentValuePropertiesCallable  
  
A callable wrapper that creates app intent instances from keyword arguments.  
