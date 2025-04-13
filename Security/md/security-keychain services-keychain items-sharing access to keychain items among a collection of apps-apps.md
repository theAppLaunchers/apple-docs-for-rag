

- Security
- Keychain services
- Keychain items
-  Sharing access to keychain items among a collection of apps 

Article

# Sharing access to keychain items among a collection of apps

Enable apps to share keychain items with each other by adding the apps to an access group.

## Overview

If you develop a family of apps, all of which rely on the same password or cryptographic key, you can use access groups to securely share that password or key among those apps. For example, you can share credentials, so that logging into one of your apps automatically grants the user access to all of your apps. This kind of sharing doesn’t require interaction with or permission from the user, but limits sharing to apps that are delivered by a single development team.

An access group is a logical collection of apps tagged with a particular group name string. Any app in a given group can share keychain items with all the other apps in the same group. You can add an app to any number of groups, but the app is always part of at least one group that contains only itself. That is, an app can always store and retrieve private keychain items, regardless of whether it also participates in any other groups. Keychain items, on the other hand, are always part of exactly one group.

Important

This form of keychain item sharing applies to all iOS keychain items, and to macOS keychain items when you query with the kSecUseDataProtectionKeychain key, set the item’s kSecAttrSynchronizable attribute, or both.

### Set your app’s access groups

You control the groups that your app belongs to by manipulating its entitlements. In particular, an app belongs to all the groups named in a virtual array of strings that the system forms for each app as the concatenation of the following items, evaluated in this order:

Keychain access groups  
The optional Keychain Access Groups Entitlement holds an array of strings, each of which names an access group.

Application identifier  
Xcode automatically adds the `application-identifier` entitlement (or the `com.apple.application-identifier` entitlement in macOS) to every app during code signing, formed as the team identifier (team ID) plus the bundle identifier (bundle ID).

Application groups  
When you collect related apps in an application group using the App Groups Entitlement, they share access to a group container, and gain the ability to message each other in certain ways. You can use app group names as keychain access group names, without adding them to the Keychain access groups entitlement.

Xcode handles the application identifier (app ID) for you when you set the bundle ID. You set the others by manipulating capabilities in Xcode.

#### Establish your app’s private access group

When you create a new app you assign it a bundle ID, typically using reverse DNS notation, with a string like `com.example.AppOne`. When code signing your app, Xcode automatically prefixes the bundle ID with your team ID — the unique character sequence issued by Apple to each development team — and stores the combined string as the app ID. The system recognizes this app ID as the name of your app’s default keychain access group by including it in your access group array:

```
[$(teamID).com.example.AppOne]
```

Because app IDs are unique across all apps, and because the app ID is stored in an entitlement protected by code signing, no other app can use it, therefore no other app is in this group. Any keychain items stored with this access group are private to App One. Similarly, if you have a second app with a bundle ID of `com.example.AppTwo`, it automatically belongs to its own group:

```
[$(teamID).com.example.AppTwo]
```

As a result, by default, each app’s keychain items remains isolated from all other apps, although you can add another app signed by the same Apple Developer team to the app’s default keychain access group, using the Keychain Access Groups Entitlement.

#### Add apps to one or more keychain access groups

When you want two apps to be able to share keychain items, you can add both to the same keychain access group. Do this by enabling the Keychain Sharing capability in Xcode for each app, and adding a common string to the list of keychain groups in each case. Typically, you use the same kind of reverse DNS naming for a keychain group that you use for a bundle ID, so you might choose `com.example.SharedItems`:

As with forming the app ID from the bundle ID, Xcode automatically prefixes keychain groups with your team ID. This ensures that your groups are specific to your development team. When you enable the capability for App One as shown above, its logical list of app groups becomes:

```
[$(teamID).com.example.SharedItems,
 $(teamID).com.example.AppOne]
```

If you also add the same keychain group to App Two, its logical list of app groups becomes:

```
[$(teamID).com.example.SharedItems,
 $(teamID).com.example.AppTwo]
```

In effect, the two apps gain a region of overlap to share items.

Notice that the distinct areas represented by the app IDs are still present, allowing each app to continue to access its own, private items. But both apps now also belong to the shared items group, enabling them to share keychain items. In this way, you can add an app to as many different groups as you like.

#### Use app groups to expand sharing of keychain and non-keychain data

When your app belongs to an app group, it can share certain kinds of non-keychain data with other apps in the same group. For example, you can use the init(suiteName:) method to create a new UserDefaults instance that shares the preferences you set among all the apps in the app group. Like keychain access groups, you enable app groups with a capability in Xcode.

Starting in iOS 8, when an app belongs to an app group, it can also use this mechanism to share keychain items. In this example, add App One to the `group.com.example.AppSuite` app group:

App One’s list of access groups expands to include the app group:

```
[$(teamID).com.example.SharedItems,
 $(teamID).com.example.AppOne,
 group.com.example.AppSuite]
```

This allows it to share keychain items with any app in the App Suite group (distinct from any sharing it’s already doing with apps in the shared items keychain access group).

Xcode doesn’t prepend the app group with the team identifier. Instead, it guards against the reuse of app group names across teams when you try to add an app group to a provisioning profile.

#### Know the difference between app groups and keychain access groups

App groups and keychain access groups aren’t mutually exclusive—you can use both in the same app—but they do differ in several important ways that may help you decide which to use for a given situation.

First, as described above, using an app group enables additional data sharing beyond keychain items. You might want this extra sharing, or might already be using an app group for this purpose, and thus not need to add keychain access groups. On the other hand, you might not want to enable this additional sharing at all, and prefer keychain access groups instead.

Second, order matters. The system considers the first item in the list of access groups to be the app’s default access group. This is the access group that keychain services assumes if you don’t otherwise specify one when adding keychain items. An app group can’t ever be the default, because the app ID is always present and appears earlier in the list. However, a keychain access group can be the default, because it appears before the app ID. In particular, the first keychain access group, if any, that you specify in the corresponding capability becomes the app’s default access group. If you don’t specify any keychain access groups, then the app ID is the default.

### Set a keychain item’s access group

Unlike apps, which can belong to many access groups, keychain items belong to a single group, identified by the kSecAttrAccessGroup attribute. From the item’s point of view, the world is a collection of disjoint groups, and the item belongs to exactly one of them.

When you create a new item with the SecItemAdd(_:_:) method, you can specify a group in the add attributes using the kSecAttrAccessGroup key. For example, you can create a new generic password item in the Shared Items group defined above:

```
let accessGroup = ".com.example.SharedItems"
let attributes = [kSecClass: kSecClassGenericPassword,
                  kSecAttrService: service,
                  kSecAttrAccount: username,
                  kSecAttrAccessGroup: accessGroup,
                  kSecValueData: password] as [String: Any]
let addStatus = SecItemAdd(attributes as CFDictionary, nil)
```

Use any of the groups to which your app belongs. If you try to use an access group to which your app doesn’t belong, the operation fails and returns the errSecMissingEntitlement status. This includes attempts to “prime” an entry using a zero-length string as the value for the kSecAttrAccessGroup key, because the empty string represents an invalid group.

If you don’t specify any access group when adding an item, keychain services applies your app’s default access group, which is the first group named in the concatenated list of groups described in Set your app’s access groups.

When you search for keychain items with the SecItemCopyMatching(_:_:) method, you can likewise specify an access group in the search query to limit your search to a particular access group:

```
let query = [kSecClass: kSecClassGenericPassword,
             kSecAttrService: service,
             kSecAttrAccount: username,
             kSecReturnAttributes: true,
             kSecAttrAccessGroup: accessGroup,
             kSecReturnData: true] as [String: Any]
var item: CFTypeRef?
let readStatus = SecItemCopyMatching(query as CFDictionary, &item)
```

If you specify a group to which your app doesn’t belong, no items match and the query returns the errSecItemNotFound status. If you don’t specify an access group in the query, the search matches any of your app’s groups.

