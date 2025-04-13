

- Xcode
- Testing
-  Updating your existing codebase to accommodate unit tests 

Article

# Updating your existing codebase to accommodate unit tests

Remove coupling between components to increase test coverage and reliability.

## Overview

Adding unit tests to existing projects can be difficult, because design choices made without considering testability can couple together distinct classes or subsystems, making it impossible to test them in isolation. When two components in your software are tightly coupled, you can only use one of them correctly when it’s integrated with the other in a specific way. Sometimes, this coupling means your tests attempt network connections or interact with the filesystem, which makes the tests slow and their results non-deterministic. Removing the coupling makes it possible to introduce unit tests, but requires code changes in places where you don’t already have test coverage, which is risky.

To improve the test coverage of your project by identifying a component you’d like to test, write a test case that covers the behavior you want to assert. Use a risk-focused approach to prioritization that covers logic in features which have received a high number of user bug reports, or where a regression would have the highest impact.

When the code you’re testing is coupled to another part of your project or a framework class, make the smallest possible change to the code so you can isolate the component without changing its behavior. Improve the ability to use the class in a test context with reduced coupling, and keep the changes small to reduce the risk associated with each change.

The following sections propose changes that remove couplings in situations where coupling between the code under consideration and another component blocks testing. Each solution demonstrates how a test function works with the changed code to assert its behavior.

### Replace a concrete type with a protocol

When your code relies on a specific type whose behavior makes testing difficult, create a protocol that lists the methods and properties used by your code. You can use this approach when interacting with components in your own codebase or with APIs from other sources outside of your control, including platform SDKs and Swift packages. Examples of such problematic dependencies include those that access external state, including user documents or databases, or those that don’t have deterministic results, including network connections or random value generators.

The following shows a class in an app that uses an opaque service to open a file which represents an attachment handled by external dependancies. The outcome of the `openAttachment(file:with:)` method depends on whether the opaque service can handle files of the requested type, and whether the application successfully opens the file. All of these variables could introduce test failures, which would slow down development as you investigate “errors” that turn out to be transient problems unrelated to your code.

```
private enum AttachmentOpeningError: Error {
    case unableToOpenAttachment
}

struct AttachmentOpener {
  func openAttachment(file location: URL, with service: OpaqueService) throws {
    if (!service.open(location)) {
      throw AttachmentOpeningError.unableToOpenAttachment
    }
  }
}
```

To test code with this coupling, introduce a protocol that describes how your code interacts with the problematic dependency. Use that protocol in your code, so the class depends on the existence of the methods in the protocol, but not their specific implementation. Write an alternative implementation of the protocol that doesn’t perform the stateful or nondeterministic tasks, and use that implementation to write tests with controlled behavior.

In this listing, a protocol that includes the `open` method is defined, along with an extension to opaque class that makes it conform to the protocol.

```
protocol URLOpener {
    func open(_ file: URL) -> Bool
}

extension OpaqueService : URLOpener {}

struct AttachmentOpener {
    func openAttachment(file location: URL, with service: URLOpener) throws {
        if (!service.open(location)) {
            throw AttachmentOpeningError.unableToOpenAttachment
        }
    }
}

class StubService: URLOpener {
    var isSuccessful = true

    func open(_ file: URL) -> Bool {
        return isSuccessful
    }
}
```

In tests, write a different implementation of the `URLOpener` protocol that doesn’t depend on the apps installed on the user’s computer.

- Swift Testing
- XCTest

```
@Suite struct AttachmentOpenerTests {
    var service = StubService()
    var attachmentOpener = AttachmentOpener()
    let location = URL(fileURLWithPath: "/tmp/a_file.txt")

    @Test("throws no error when open succeeds")
    func serviceCanOpenAttachment() {
        service.isSuccessful = true
        #expect(throws: Never.self) {
            try attachmentOpener.openAttachment(file: location, with: service)
        }
    }

    @Test("throws unableToOpenAttachment when open fails")
    func throwsIfServiceCannotOpenAttachment() {
        service.isSuccessful = false
        #expect(throws: AttachmentOpeningError.unableToOpenAttachment) {
            try attachmentOpener.openAttachment(file: location, with: service)
        }
    }
}
```

```
class AttachmentOpenerTests: XCTestCase {
    var service: StubService! = nil
    var attachmentOpener: AttachmentOpener! = nil
    let location = URL(fileURLWithPath: "/tmp/a_file.txt")

    override func setUp() {
        service = StubService()
        attachmentOpener = AttachmentOpener()
    }

    override func tearDown() {
        service = nil
        attachmentOpener = nil
    }

    func testServiceCanOpenAttachment() {
        service.isSuccessful = true
        XCTAssertNoThrow(try attachmentOpener.openAttachment(file: location, with: service))
    }

    func testThrowIfServiceCannotOpenAttachment() {
        service.isSuccessful = false
        XCTAssertThrowsError(try attachmentOpener.openAttachment(file: location, with: service))
    }
}
```

### Replace named type with metatype value

When one class in your app creates and uses instances of another class, and the created objects introduce testing difficulties, it can be hard to test the class where they’re created. Parameterize the type of the created object and use a required initializer to create an instance. Examples of this difficult testing situation include a controller that creates a new document on the filesystem in response to a person’s action, or a method that interprets JSON received from a web service and creates new Core Data managed objects that represent the received data.

In each of these cases, because the objects are created by the code you want to test, you can’t pass in a different object as a parameter to the method. The object doesn’t exist until it’s created by your code, at which point it’s of the type that has the untestable behavior.

The listing below shows a `DocumentLoader` class that creates and loads a `Document`, for example, in response to a UI action. The document object it creates reads and writes data to the file system, so its behavior isn’t easy to control in a unit test.

```
enum DocumentError : Error {
    case cannotLoadContent
    case cannotSaveContent
}

class Document {
    private var location: URL
    private var titleContent: String?
    var title : String {
        get {
            return titleContent ?? "Untitled"
        }
        set {
            titleContent = newValue
        }
    }

    required init(fileURL: URL) {
        location = fileURL
    }

    func load() throws {
        do {
            let myString = try String(contentsOf: location, encoding: .utf8)
        }
        catch {
            throw DocumentError.cannotLoadContent
        }
    }

    func save() throws {
        do {
            try titleContent?.write(to: location, atomically: true, encoding: .utf8)
        }
        catch {
            throw DocumentError.cannotSaveContent
        }
    }
}

class DocumentLoader {
    func loadDocument(at location: URL) -> Bool {
        do {
            var document = Document(fileURL: location)
            try document.load()
            // Do something with the document, for example, present it in the app's UI.
            return true
        } catch {
            return false
        }
    }
}
```

To remove the coupling between the code you’re trying to test and the objects it creates, define a variable on the class under test that represents the *type* of object it should construct. Such a variable is called a *metatype value*. Set the default value to the type the class already uses. You’ll need to ensure that the initializer used to construct instances is marked `required`. This listing shows the document browser view controller delegate with that variable introduced. The delegate creates documents with the type defined by the metatype value.

```
class DocumentLoader {
    var DocumentClass = Document.self

    func loadDocument(at location: URL) -> Bool {
        do {
            var document = DocumentClass.init(fileURL: location)
            try document.load()
            // Do something with the document, for example, present it in the app's UI.
            return true
        } catch {
            return false
        }
    }
}
```

Set a different value for the metatype in tests, so your code constructs an object that doesn’t have the same untestable behavior. In tests, create a “sample” version of the document class: a class with the same interface, but which doesn’t implement the behavior that makes it hard to test. In this case, a sample document class should not interact with the file system.

```
class SampleDocument : Document {
    static var loadsSuccessfully : Bool = true
    static var savesSuccessfully : Bool = true

    override func load() throws {
        guard SampleDocument.loadsSuccessfully else {
            throw DocumentError.cannotLoadContent
        }
    }

    override func save() throws {
        guard SampleDocument.savesSuccessfully else {
            throw DocumentError.cannotSaveContent
        }
    }
}
```

Replace the document type with the sample type in your test case’s `setUp()` method, so the document loader you test creates instances of the stub document type. Sample documents behave deterministically in the tests.

- Swift Testing
- XCTest

```
@Suite final class DocumentLoaderTests {
    let loader = DocumentLoader()

    init() {
        loader.DocumentClass = SampleDocument.self
    }

    @Test @MainActor func documentLoaderReturnsFalseWhenDocumentCannotLoad() {
        SampleDocument.loadsSuccessfully = false
        #expect(loader.loadDocument(at: URL(filePath: "/Users/example/Documents/document.txt")) == false)
    }

    @Test @MainActor func documentLoaderReturnsTrueWhenDocumentLoads() {
        SampleDocument.loadsSuccessfully = true
        #expect(loader.loadDocument(at: URL(filePath: "/Users/example/Documents/document.txt")) == true)
    }
}
```

Note

As these tests rely on the shared `SampleDocument.loadsSuccessfully` state, they can’t run concurrently. The tests are annotated with `@MainActor` to ensure they run in series.

```
class DocumentLoaderTests: XCTestCase {
    var loader: DocumentLoader! = nil

    override func setUp() {
        loader = DocumentLoader()
        loader.DocumentClass = SampleDocument.self
    }

    override func tearDown() {}

    func testDocumentLoaderReturnsFalseWhenDocumentCannotLoad() {
        SampleDocument.loadsSuccessfully = false
        XCTAssertFalse(loader.loadDocument(at: URL(filePath: "/Users/example/Documents/document.txt")))
    }

    func testDocumentLoaderReturnsTrueWhenDocumentLoads() {
        SampleDocument.loadsSuccessfully = true
        XCTAssertTrue(loader.loadDocument(at: URL(filePath: "/Users/example/Documents/document.txt")))
    }
}
```

### Subclass and override untestable methods

When a class combines custom logic with interactions or behavior that make the class hard to test, introduce a subclass that overrides some of the class’s methods to make the others easier to test. It’s common to design classes that contain both app-specific logic, and interactions with the environment or frameworks that render behavior difficult to control in tests. A common example is a UIViewController subclass, which has app-specific code in its action methods and also loads views or presents other view controllers.

Introducing tests for the custom app logic is desirable, to ensure that this logic works as expected and to protect against regressions. The complexity of controlling or working around the interactions between the class and the environment make testing the logic difficult.

As an example, the following account object provides a method to calculate someone’s birthday. It does the calculation by finding the number of years between the account’s recorded date of birth and today’s date.

```
import Foundation

enum AccountError : Error {
    case cannotCalculateAge
}

class Account {
    let name: String
    let email: String
    let userId: String
    let dateOfBirth: Date

    init(name: String, email: String, userId: String, dateOfBirth: Date) {
        self.name = name
        self.email = email
        self.userId = userId
        self.dateOfBirth = dateOfBirth
    }

    var now : Date {
        get {
            return Date()
        }
    }

    func age() throws -> Int {
        let calendar = Calendar.current
        let birthday = calendar.startOfDay(for: dateOfBirth)
        let today = calendar.startOfDay(for: now)
        guard let years =  calendar.dateComponents([.year], from: birthday, to: today).year else {
            throw AccountError.cannotCalculateAge
        }
        return years
    }
}
```

Testing this object’s behavior is difficult because the `now` field gets its value from the system’s clock. If the clock isn’t set correctly then the test might fail, and as time passes the value returned from `now` changes so a test’s expectation of the computed age would become out of date.

To overcome this complexity, subclass the `Account` and “stub out” methods that produce complex, untestable interactions, by overriding them with simpler methods. Use the subclass in your tests to verify the behavior of the custom logic, which you don’t override. You may also need to introduce a metatype value, if the code under test creates an instance of the target type.

The following listing introduces a subclass, `StubAccount`, which doesn’t rely on the system’s clock. Instead, it uses a fixed date that’s configured by the caller. Tests using this subclass provide fixed values for both the account’s date of birth and the date that represents the current date, to ensure that the calculation the `Account` object performs is correct.

```
class StubAccount : Account {
    private var overrideNow : Date

    init(name: String, email: String, userId: String, dateOfBirth: Date, overrideNow: Date) {
        self.overrideNow = overrideNow
        super.init(name: name, email: email, userId: userId, dateOfBirth: dateOfBirth)
    }

    override var now : Date {
        overrideNow
    }
}
```

In testing types, create instances of `StubAccount` and test the date-calculation logic inherited from `Account`. Because `StubAccount` lets the test code control the date that represents the current date, the test behavior doesn’t depend on the system’s clock.

- Swift Testing
- XCTest

```
@Suite struct AccountTests {
    @Test func accountCalculatesAgeCorrectly() throws {
        let dateOfBirth = Calendar.current.date(from: DateComponents(
            timeZone: TimeZone(identifier: "Europe/London"),
            year: 1970,
            month: 1,
            day: 1
        ))!
        let fixedDateForToday = Calendar.current.date(from: DateComponents(
            timeZone: TimeZone(identifier: "Europe/London"),
            year: 2024,
            month: 12,
            day: 31
        ))!
        let account = StubAccount(name: "Example Account", email: "account@example.com", userId: "example", dateOfBirth: dateOfBirth, overrideNow: fixedDateForToday)
        #expect(try account.age() == 54)
    }
}
```

```
class AccountTests : XCTestCase {
    private var account: StubAccount! = nil

    override func setUp() {
        let dateOfBirth = Calendar.current.date(from: DateComponents(
            timeZone: TimeZone(identifier: "Europe/London"),
            year: 1970,
            month: 1,
            day: 1
        ))!
        let fixedDateForToday = Calendar.current.date(from: DateComponents(
            timeZone: TimeZone(identifier: "Europe/London"),
            year: 2024,
            month: 12,
            day: 31
        ))!
        account = StubAccount(name: "Example Account", email: "account@example.com", userId: "example", dateOfBirth: dateOfBirth, overrideNow: fixedDateForToday)
    }

    override func tearDown() { }

    func testAccountCalculatesAgeCorrectly() throws {
        XCTAssertEqual(try account.age(), 54)
    }
}
```

Sometimes this pattern can help you test existing classes that combine multiple responsibilities, but only if those classes and the methods aren’t marked as `final` and it isn’t a good practice to follow in designing testable code from scratch. Separate code that handles different concerns into different classes, for example:

- Controller classes that implement your app’s custom behavior.

- View controllers that manage your view hierarchy and respond to UI actions.

- View models that prepare and update data you present in your app’s views.

Add UI tests to verify the behavior of the real class in an end-to-end workflow covering the logic you stubbed out in the unit tests.

Subclassing and overriding untestable methods is the first step in redesigning existing code so app logic and integration with frameworks or external data are separated. Dividing the code this way makes it easier to understand which parts of your project implement the app’s features and which integrate with the rest of the system, and it also reduces the chance of introducing logic bugs when you change your code to take advantage of new APIs or adopt different technologies.

### Inject a singleton

If your code uses a singleton object to gain access to globally-available state or behavior, turn the singleton into a parameter that you can replace to support isolation for testing. Singleton use can be spread throughout a codebase, which makes it hard to know the singleton’s state when it’s used by the component you’re trying to test. Running tests in different orders may produce different outcomes.

Note

Commonly-used singletons, including NSApplication and the default FileManager, have behavior that’s dependent on external state. Components that use these singletons directly introduce more complications for reliable testing.

In this example, a `LoginHandler` object participates in authenticating someone to a network service. Part of its capability is retrieving a username that the app previously used for the service, which it gets from the standard user defaults object:

```
class LoginHandler {

    var previousUsername: String? {
        get {
            UserDefaults.standard.string(forKey: "ExampleAccountUsername")
        }
    }

}
```

UserDefaults relies on shared state that’s stored in the file system and might be modified by other code in the app or by someone editing files on their Mac. Replace direct access to the singleton object with a parameter or property that can be controlled from outside the component under test. In the app, continue to use the singleton as the collaborator for the component. In tests, supply an alternative object that’s easier to control.

The following listing shows the result of applying this change to the `LoginHandler` class listed above. The login handler gets the stored username from its `storage` object, which defaults to the user defaults singleton. An extension conforms `UserDefaults` to the `LoginStorage` protocol, so that tests can supply alternative implementations of the protocol.

```
protocol LoginStorage {
    func string(forKey: String) -> String?
}

extension UserDefaults : LoginStorage { }

class LoginHandler {
    private var storage: LoginStorage

    init(storage: LoginStorage = UserDefaults.standard) {
        self.storage = storage
    }

    var previousUsername: String? {
        get {
            storage.string(forKey: "ExampleAccountUsername")
        }
    }

}
```

In a test case you can substitute a different storage object, which isn’t used elsewhere in the test suite or the app, and therefore is isolated from the behavior of other tests and modules.

- Swift Testing
- XCTest

```
struct StubLoginStorage : LoginStorage {
    let value: String?

    init(value: String?) {
        self.value = value
    }

    func string(forKey: String) -> String? {
        value
    }
}

@Suite struct LoginHandlerTests {
    let handler: LoginHandler = LoginHandler(storage: StubLoginStorage(value: "example-username"))

    @Test func handlerGetsUsernameFromStorage() {
        #expect(handler.previousUsername == "example-username")
    }
}
```

```
struct StubLoginStorage : LoginStorage {
    let value: String?

    init(value: String?) {
        self.value = value
    }

    func string(forKey: String) -> String? {
        value
    }
}

class XCLoginHandlerTests : XCTestCase {
    var handler: LoginHandler! = nil

    override func setUp() {
        handler = LoginHandler(storage: StubLoginStorage(value: "example-username"))
    }

    func testHandlerGetsUsernameFromStorage() {
        XCTAssertEqual(handler.previousUsername, "example-username")
    }
}
```

You may need to combine this change with those described in the article sections (Replace a concrete type with a protocol and Subclass and override untestable methods) to create the alternative object you use in the test in place of the singleton. You’ll need to do this where the singleton supplies behavior that’s difficult to control in a test, like FileManager or NSApplication.

## See Also

### Test development

Adding tests to your Xcode project

Include test targets that build code to test the logic in your functions, check for integration issues, automate UI workflows, and measure performance.

Determining how much code your tests cover

Use code coverage to focus new test development on areas that lack adequate testing.

Improving code assessment by organizing tests into test plans

Control the information you receive from your tests at different stages in the software engineering process by creating and configuring test plans.

