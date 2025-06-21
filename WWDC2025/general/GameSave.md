Framework

# GameSave

Store and sync your application’s save files in iCloud.

iOS 26.0+BetaiPadOS 26.0+BetaMac Catalyst 26.0+BetamacOS 26.0+BetavisionOS 26.0+Beta

## [Overview](/documentation/GameSave#Overview)

GameSave uses iCloud Drive to synchronize your application’s save data across devices. The framework provides a set of APIs for reading and writing one or more files to a directory, while abstracting away iCloud concepts. It handles common save syncing scenarios like conflict resolution and offline play. Additionally, it provides a set of convenience UI alerts for these typical scenarios. GameSave also supports local saving for when the device isn’t signed into iCloud Drive.

Important

For GameSave to store the game data in the player’s iCloud account, you need to provide an identifier for the iCloud container that stores the data. Add the iCloud capability to your project and select the iCloud Documents checkbox. For more information, see [Configuring iCloud services](/documentation/Xcode/configuring-icloud-services).

## [Topics](/documentation/GameSave#topics)

### [Synced directory](/documentation/GameSave#Synced-directory)

```swift
```swift
```swift
```swift
class GameSyncedDirectory
```
```

A cloud-synced directory for game-save data.
```
```

### [Synced directory (Objective-C)](/documentation/GameSave#Synced-directory-Objective-C)

```swift
```swift
```swift
```swift
class GSSyncedDirectory
```
```

A cloud-synced directory for game-save data.
```
```

### [Variables](/documentation/GameSave#Variables)

```swift
```swift
```swift
```swift
let GameSaveErrorDomain: String
```
```
```
```

Beta Software

This documentation contains preliminary information about an API or technology in development. This information is subject to change, and software implemented according to this documentation should be tested with final operating system software.

[Learn more about using Apple's beta software](https://developer.apple.com/support/beta-software/)