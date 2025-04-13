

- ClassKit Catalog API
- Context
-  Context.Metadata 

Dictionary

# Context.Metadata

Information that helps the system categorize a context.

ClassKit 1.0+

``` source
object Context.Metadata
```

## Properties

`keywords`

`[string]`

A list of tags that describes your content.

`locale`

`string`

 (Required) 

The locale for which you designed the context. You can upload multiple versions of a context that have the same identifier path but different locales. Use one of the identifiers that the Locale structure supports, like `en-us`.

`minimumBundleVersion`

`string`

The earliest version of your app that supports this context, which is a string of numbers that use periods as delimiters, like *6.3* or *10.5.12*. Delete contexts for versions of your app that you no longer support.

`presentableLocales`

`[string]`

A list of locales — any of the identifiers that the Locale structure supports — for which this context data is suitable. If you don’t set this value, the system sets it to a single-element array containing the value of the `locale` field. Set the value to `mul` to indicate that the content is suitable for any locale.

`standardsAlignments`

`[string]`

A list of standards to which the context adheres.

`presentablePaths`

`[`Context.Metadata.PresentablePaths`]`

A list of identifier paths that act as the context’s parent context. If you don’t set a value for this field, the system adds a path representing the default parent of this context. A context can have a maximum of 2000 child contexts.

## Attributes 

Possible types:

## Mentioned in 

Preparing Context Data

## Discussion

You typically design a context with a specific locale in mind, and use the `locale` field to indicate that locale. However, you may want to make the context available in other locales. For example, a context that you design for the `en-us` locale may be suitable for any English-speaking locale, like `en-gb`, `en-au`, and so on. Use the `presentableLocales` field to indicate all the locales for which you consider the content to be suitable. Use a single-element array with the value `mul` to indicate suitability for any locale.

If you create multiple contexts to represent the same content for different locales, be sure that the set of presentable locales for one context doesn’t overlap the set of presentable locales for others. This might result in teachers seeing multiple versions of the same content. For example, if you use `mul` for one context’s presentable values, and `en-us` for a second, Schoolwork presents an English-speaking teacher in the United States with both contexts, as if they represent different content.

## Topics

### Parent Contexts

object Context.Metadata.PresentablePaths

The identifier path of a context to use as one of the presentable paths in a context’s metadata.

## See Also

### Objects

object Context.Data

The data that makes up a context.

