

- App Intents
- App intent domains
-  Making browser actions available to Siri and Apple Intelligence 

Article

# Making browser actions available to Siri and Apple Intelligence

Create app intents and entities to integrate your app’s web browsing functionality with Siri and Apple Intelligence.

## Overview

To integrate your app’s web browsing functionality with Siri and Apple Intelligence, you use Swift macros that generate additional properties and add protocol conformance for your app intent, app entity, and app enumeration implementation that Apple Intelligence needs. For example, if your app allows a person to open a website in a new tab, use the AssistantIntent(schema:) macro and provide the assistant schema that consists of the `.browser` domain and the createTab schema:

```
@AssistantIntent(schema: .browser.createTab)
struct CreateTabIntent: AppIntent {
    var url: URL?
    var isPrivate: Bool

    // Return a TabEntity instance.
    func perform() async throws -> some ReturnsValue {
       .result(value: TabEntity())
    }
}
```

To learn more about assistant schemas, see Integrating actions with Siri and Apple Intelligence. For a list of available app intents in the `.browser` domain, see AssistantSchemas.BrowserIntent.

### Make sure your entity meets requirements

If you use app entities to describe custom data types, annotate the app entity implementation with the AssistantEntity(schema:) macro. This makes sure Siri and Apple Intelligence can understand your data. For example, the intent in the previous section uses `TabEntity`. The following code snippet shows how the `TabEntity` implementation uses the AssistantEntity(schema:) macro:

```
@AssistantEntity(schema: .browser.tab)
struct TabEntity {
    struct Query: EntityStringQuery {
        func entities(for identifiers: [TabEntity.ID]) async throws -> [TabEntity] { [] }
        func entities(matching string: String) async throws -> [TabEntity] { [] }
    }
    static var defaultQuery = Query()

    var displayRepresentation: AppIntents.DisplayRepresentation { "TabEntity" }

    let id = UUID()

    var url: URL?
    var name: String
    var isPrivate: Bool
}
```

The assistant schema for the `TabEntity` consists of the `.browser` domain and the tab schema.

For a list of available app entity schemas in the `.browser` domain, see AssistantSchemas.BrowserEntity.

### Make sure your enumeration meets requirements

To make sure Siri and Apple Intelligence understand custom static types for your intent parameters, annotate app enumerations with the AssistantEnum(schema:) macro. Then, pass the `.browser` domain and a schema to it. The following example uses the clearHistoryTimeFrame schema:

```
@AssistantEnum(schema: .browser.clearHistoryTimeFrame)
struct ClearHistoryTimeFrameEnum: String, AppEnum {
    case today
    case lastFourHours
    case todayAndYesterday
    case allTime

static var caseDisplayRepresentations: [ClearHistoryTimeFrame: DisplayRepresentation] = [:]
}
```

For a list of available app enumeration schemas in the `.browser` domain, see AssistantSchemas.BrowserEnum.

## See Also

### Browser

protocol BrowserIntent

Assistant schema conformance for app intents that offer web browsing functionality.

protocol BrowserEntity

Assistant schema conformance for app entities that describe data for web browsing functionality.

protocol BrowserEnum

Assistant schema conformance for types you use for web browsing functionality.

