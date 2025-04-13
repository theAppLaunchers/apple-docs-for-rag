

- ClassKit Catalog API
-  Preparing Context Data 

Article

# Preparing Context Data

Adjust how you manage context data when working with the web API.

## Overview

The Context objects that you send to the ClassKit Catalog API resemble the CLSContext instances that you construct when declaring a context hierarchy in your app. For example, you provide information in the Context.Data object like a title, a type, and a summary, corresponding to the title, type, and summary properties of CLSContext, respectively. However, there are some differences in the way you describe contexts to the ClassKit Catalog API, like how you refer to the main app context and how you manage localization.

For general information about building a context hierarchy, see Advertising your app’s assignable content.

### Access the Main App Context

Every app has a single main app context at the root of its context hierarchy. You access the main app context from inside your app using the mainAppContext property of the ClassKit data store, and can neither create nor destroy the context. ClassKit manages the main app context for you.

When building a context hierarchy in the ClassKit Catalog API, you explicitly create a main app context. Be sure to set the `type` field to `app`, and set the context’s `title` to match the name of the app in the context’s locale. To avoid confusion, it’s a good idea to make these match exactly. The Schoolwork app refers to your app by its name after the teacher installs your app, but by the main context’s title otherwise.

To refer to your main app context in an API call, use a string that contains the bundle identifier for the app as its identifier path. For example, the identifier path of the main app context of the GreatPlays sample app — which you can download from Incorporating ClassKit into an Educational App — is:

```
```

### Provide Localization Data for Contexts

In your app, you describe exactly one version of a given context identified by an identifierPath. You localize user-facing elements, like the title and the summary, by providing localized strings at runtime based on the locale set by the user for the device.

Using the ClassKit Catalog API, on the other hand, you enumerate all of the localized versions of a given context. Use the `locale` field in the Context.Metadata object to indicate the locale to which a context applies. Provide different versions of the same context — uniquely identified by the identifier path — for each of the locales that you support.

## See Also

### Declaring Contexts

Create or Replace Contexts

Store information about the assignable content that your educational app provides.

Get a Context

Fetch information that you previously stored about your app’s assignable activities.

Delete a Context

Remove information that you previously stored about your app’s assignable activities.

object Context

An area of your app that represents an assignable task, like a quiz or a chapter.

object ContextsRequest

A request that you make when modifying context information.

object ContextsResponse

The response you receive after modifying context information.

