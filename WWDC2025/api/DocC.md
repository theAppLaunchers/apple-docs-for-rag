Tool

# DocC

Produce rich API reference documentation and interactive tutorials for your Swift framework or package.

## [Overview](/documentation/docc/#Overview)

The DocC documentation compiler converts Markdown-based text into rich documentation for Swift frameworks and packages. You can preview the documentation in its published form as you work on it, and also host it on a website when it’s complete.

DocC syntax — called _documentation markup_ — is a custom variant of Markdown that adds functionality for developer-specific documentation features, like cross-symbol linking, term-definition lists, code listings, and asides. You add documentation markup to your source code, compile it with DocC, and produce reference documentation for your APIs. You can also use documentation markup, along with a set of directives that instruct how DocC generates your content, to offer step-by-step tutorials that teach developers to use your APIs through interactive coding exercises or to craft comprehensive articles that explain specific technologies or topics.

![On the left, a diagram shows a blocked-out example of a compiled tutorial and Markdown. In the middle, a diagram shows a blocked-out example of Markdown. On the right, a diagram shows a blocked-out example of compiled developer documentation.](/images/org.swift.docc/docc-hero@2x.png)

## [Topics](/documentation/docc/#topics)

### [Essentials](/documentation/docc/#Essentials)

[

Documenting a Swift Framework or Package](/documentation/docc/documenting-a-swift-framework-or-package)

Create developer documentation from in-source comments, add articles with code snippets, and add tutorials for a guided learning experience.

### [Documentation Content](/documentation/docc/#Documentation-Content)

[

Writing Symbol Documentation in Your Source Files](/documentation/docc/writing-symbol-documentation-in-your-source-files)

Add reference documentation to your symbols that explains how to use them.

[

Adding Supplemental Content to a Documentation Catalog](/documentation/docc/adding-supplemental-content-to-a-documentation-catalog)

Include articles and extension files to extend your source documentation comments or provide supporting conceptual content.

[

Linking to Symbols and Other Content](/documentation/docc/linking-to-symbols-and-other-content)

Facilitate navigation between pages using links.

[

Documenting API with Different Language Representations](/documentation/docc/documenting-api-with-different-language-representations)

Create documentation for API that’s callable from more than one source language.

### [Structure and Formatting](/documentation/docc/#Structure-and-Formatting)

[

Formatting Your Documentation Content](/documentation/docc/formatting-your-documentation-content)

Enhance your content’s presentation with special formatting and styling for text and lists.

[

Adding Tables of Data](/documentation/docc/adding-tables-of-data)

Arrange information into rows and columns.

[

Other Formatting Options](/documentation/docc/other-formatting-options)

Improve the presentation and structure of your content by incorporating special page elements.

[

Adding Images to Your Content](/documentation/docc/adding-images)

Elevate your content’s visual appeal by adding images.

[

Adding Structure to Your Documentation Pages](/documentation/docc/adding-structure-to-your-documentation-pages)

Make symbols easier to find by arranging them into groups and collections.

[

Customizing the Appearance of Your Documentation Pages](/documentation/docc/customizing-the-appearance-of-your-documentation-pages)

Customize the look and feel of your documentation webpages.

### [Distribution](/documentation/docc/#Distribution)

[

Distributing Documentation to Other Developers](/documentation/docc/distributing-documentation-to-other-developers)

Share your documentation by hosting it on a web server.

### [Documentation Types](/documentation/docc/#Documentation-Types)

[

API Reference

API Documentation](/documentation/docc/api-reference-syntax)

Teach your APIs through reference documentation you create from code comments and extension files, or create detailed articles and conceptual guides.

[

API Reference

Interactive Tutorials](/documentation/docc/tutorial-syntax)

Teach developers your Swift APIs through step-by-step, interactive content.

### [Shared Syntax](/documentation/docc/#Shared-Syntax)

[`@Comment`](/documentation/docc/comment)

Captures a writer comment that’s not visible in the rendered documentation.

*   [DocC](/documentation/docc/#app-top)
*   [Overview](/documentation/docc/#Overview)
*   [Topics](/documentation/docc/#topics)