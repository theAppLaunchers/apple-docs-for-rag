

- SwiftUI
- DocumentGroup
-  init(editing:contentType:editor:prepareDocument:) 

Initializer

# init(editing:contentType:editor:prepareDocument:)

Instantiates a document group for creating and editing documents that store a specific model type.

SwiftDataSwiftUIiOS 17.0+iPadOS 17.0+macOS 14.0+

``` source
init(
    editing modelType: any PersistentModel.Type,
    contentType: UTType,
    editor: @escaping () -> Content,
    prepareDocument: @escaping (ModelContext) -> Void = { _ in }
)
```

Available when `Document` is `ModelDocument` and `Content` conforms to `View`.

Show all declarations

## Parameters 

`modelType`  

The model type defining the schema used for each document.

`contentType`  

The content type of the document. It should conform to `UTType.package`.

`editor`  

The editing UI for the provided document.

`prepareDocument`  

The optional closure that accepts `ModelContext` associated with the new document. Use this closure to set the document’s initial contents before it is displayed: insert preconfigured models in the provided `ModelContext`.

## Discussion

```
 @main
 struct Todo: App {
     var body: some Scene {
         DocumentGroup(editing: TodoItem.self, contentType: .todoItem) {
             ContentView()
         }
     }
 }

 struct ContentView: View {
     @Query var items: [TodoItem]

         var body: some View {
             List {
                 ForEach(items) { item in
                     @Bindable var item = item
                     Toggle(item.text, isOn: $item.isDone)
                 }
              }
         }
 }

 @Model
 final class TodoItem {
     var created: Date
     var text: String
     var isDone = false
 }

 extension UTType {
     static var todoItem = UTType(exportedAs: "com.myApp.todoItem")
 }
```

Important

If your app declares custom uniform type identifiers, include corresponding entries in the app’s `Info.plist`. For more information, see Defining file and data types for your app. Also, remember to specify the supported Document types in the Info.plist as well.

## See Also

### Editing a document backed by a persistent store

init(editing: UTType, migrationPlan: any SchemaMigrationPlan.Type, editor: () -> Content, prepareDocument: (ModelContext) -> Void)

Instantiates a document group for creating and editing documents described by the last `Schema` in the migration plan.

