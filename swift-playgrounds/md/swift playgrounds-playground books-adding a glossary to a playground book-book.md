

- Swift Playgrounds
- Playground Books
-  Adding a Glossary to a Playground Book 

Article

# Adding a Glossary to a Playground Book

Define terms in the glossary property list and reference them on playground pages.

## Overview

You can create a glossary for your playground book if its material introduces vocabulary that might be new to your audience.

Glossary entries appear in two places:

- The Tools (…) menu’s Glossary entry, which shows a list of all terms and descriptions.

- Individual popovers for terms that you reference from within the prose of a playground page.

### Assemble Terms into a Glossary

Add a glossary by placing a property list containing the terms and definitions at the following path inside your playground book:

```
.playgroundbook/Contents/PrivateResources/Glossary.plist
```

Note

Xcode includes a property list editor you can use to create property lists. For more information, see Edit property lists in Xcode Help.

The top-level key in a glossary’s property list is a dictionary named `Terms`. Inside that dictionary, nest a single dictionary for each term you want to define. The key for each nested dictionary is the name of the term you’re defining.

### Add Detail Keys to a Term’s Definition

The dictionary you use to define a term has three parts. Each part requires a specifically named key:

`Definition`  
**Required.** A string that defines the term. Definitions are displayed both in the full glossary and in the popovers that appear when the term is tapped in prose.

`FirstUse`  
A dictionary you use to point to the first time a term is used in a book. This dictionary has two required keys: `PageReference`, which is a link to the chapter and page where the term is first used; and `Title`, which you use to name the link to the chapter and page.

Spaces and other special characters in `PageReference` must be encoded according to the URI rules in RFC 3986. For example, a reference to the “Commands” chapter’s “Issuing Commands” page is specified by using the `Commands/Issuing%20Commands` URI.

`Title`  
A string you use to customize the term’s title. Use this key to localize terms. If you omit this key, the term is used as its own title.

The following image shows the parts of a glossary as they appear in Swift Playgrounds.

### Add Links to the Terms in Your Prose

Link appropriately to your glossary terms throughout your playground book’s pages. Link to a term on its first use, as well as any subsequent uses on later pages where you think learners might need to check the definition again.

Use markup to add term links. An example of link markup for the term `command` is `[commands](glossary://command)`. Include this markup in the flow of the prose you write for the learning material in your playground book. The example below shows a term link in context.

```
/*:
In this challenge, you'll practice your [bug](glossary://bug)-finding skills by
finding and rearranging the [commands](glossary://command) that are out of
order in the code below.
*/
```

When you tap the rendered link on a page, a popover appears with the definition of the term.

## See Also

### Related Documentation

Markup Formatting Reference

