

- Core Services
- File Metadata
- MDItem
-  Common Metadata Attribute Keys 

API Collection

# Common Metadata Attribute Keys

Metadata attribute keys that are common to many file types.

## Topics

### Constants

let kMDItemAttributeChangeDate: CFString!

The date and time of the last change made to a metadata attribute. A CFDate.

let kMDItemAudiences: CFString!

The audience for which the file is intended. The audience may be determined by the creator or the publisher or by a third party. A CFArray of CFStrings.

let kMDItemAuthors: CFString!

The author, or authors, of the contents of the file. A CFArray of CFStrings.

let kMDItemAuthorAddresses: CFString!

This attribute indicates the author addresses of the document. A CFArray of CFStrings.

let kMDItemCity: CFString!

Identifies city of origin according to guidelines established by the provider. A CFString.

let kMDItemComment: CFString!

A comment related to the file. This differs from the Finder comment, `kMDItemFinderComment`. A CFString.

let kMDItemContactKeywords: CFString!

A list of contacts that are associated with this document, not including the authors. A CFArray of CFStrings.

let kMDItemContentCreationDate: CFString!

The creation date of an edited or optimized version of the song or composition.

let kMDItemContentModificationDate: CFString!

The date and time that the contents of the file were last modified. A CFDate.

let kMDItemContentType: CFString!

The UTI pedigree of a file. A CFString.

let kMDItemContributors: CFString!

The entities responsible for making contributions to the content of the resource. A CFArray of CFStrings.

let kMDItemCopyright: CFString!

The copyright owner of the file contents. A CFString.

let kMDItemCountry: CFString!

The full, publishable name of the country or region where the intellectual property of the item was created, according to guidelines of the provider.

let kMDItemCoverage: CFString!

The extent or scope of the content of the resource. A CFString.

let kMDItemCreator: CFString!

Application used to create the document content (for example “Word”, “Pages”, and so on). A CFString.

let kMDItemDescription: CFString!

A description of the content of the resource. The description may include an abstract, table of contents, reference to a graphical representation of content or a free-text account of the content. A CFString.

let kMDItemDueDate: CFString!

Date this item is due. A CFDate.

let kMDItemDurationSeconds: CFString!

The duration, in seconds, of the content of file. A value of 10.5 represents media that is 10 and 1/2 seconds long. A CFNumber.

let kMDItemEmailAddresses: CFString!

Email addresses related to this item. A CFArray of CFStrings.

let kMDItemEncodingApplications: CFString!

Application used to convert the original content into it's current form. For example, a PDF file might have an encoding application set to "Distiller". A CFArray of CFStrings.

let kMDItemFinderComment: CFString!

Finder comments for this file. A CFString.

let kMDItemFonts: CFString!

Fonts used in this item. You should store the font's full name, the postscript name, or the font family name, based on the available information. A CFArray of CFStrings.

let kMDItemHeadline: CFString!

A publishable entry providing a synopsis of the contents of the file. For example, "Apple Introduces the iPod Photo". A CFString.

let kMDItemIdentifier: CFString!

A formal identifier used to reference the resource within a given context. A CFString.

let kMDItemInstantMessageAddresses: CFString!

Instant message addresses related to this item. A CFArray of CFStrings.

let kMDItemInstructions: CFString!

Editorial instructions concerning the use of the item, such as embargoes and warnings. For example, "Second of four stories". A CFString.

let kMDItemKeywords: CFString!

Keywords associated with this file. For example, “Birthday”, “Important”, etc. An CFArray of CFStrings.

let kMDItemKind: CFString!

A description of the kind of item this file represents. A CFString.

let kMDItemLanguages: CFString!

Indicates the languages of the intellectual content of the resource. Recommended best practice for the values of the Language element is defined by RFC 3066. A CFArray of CFStrings.

let kMDItemLastUsedDate: CFString!

The date and time that the file was last used. This value is updated automatically by LaunchServices everytime a file is opened by double clicking, or by asking LaunchServices to open a file. A CFDate.

let kMDItemNumberOfPages: CFString!

Number of pages in the document. A CFNumber.

let kMDItemOrganizations: CFString!

The company or organization that created the document. A CFArray of CFStrings.

let kMDItemPageHeight: CFString!

Height of the document page, in points (72 points per inch). For PDF files this indicates the height of the first page only. A CFNumber.

let kMDItemPageWidth: CFString!

Width of the document page, in points (72 points per inch). For PDF files this indicates the width of the first page only. A CFNumber.

let kMDItemParticipants: CFString!

The list of people who are visible in an image or movie or written about in a document. A CFArray of CFStrings.

let kMDItemPhoneNumbers: CFString!

Phone numbers related to this item. A CFArray of CFStrings.

let kMDItemProjects: CFString!

The list of projects that this file is part of. For example, if you were working on a movie all of the files could be marked as belonging to the project “My Movie”. A CFArray of CFStrings.

let kMDItemPublishers: CFString!

The entity responsible for making the resource available. For example, a person, an organization, or a service. Typically, the name of a publisher should be used to indicate the entity. A CFArray of CFStrings.

let kMDItemRecipients: CFString!

Recipients of this item. A CFArray of CFStrings.

let kMDItemRecipientAddresses: CFString!

This attribute indicates the recipient addresses of the document. A CFArray of CFStrings.

let kMDItemRights: CFString!

Provides a link to information about rights held in and over the resource. A CFString.

let kMDItemSecurityMethod: CFString!

The security or encryption method used for the file. A CFNumber.

let kMDItemStarRating: CFString!

User rating of this item. For example, the stars rating of an iTunes track. A CFNumber.

let kMDItemStateOrProvince: CFString!

Identifies the province or state of origin according to guidelines established by the provider. For example, "CA", "Ontario", or "Sussex". A CFString.

let kMDItemTextContent: CFString!

Contains a text representation of the content of the document. Data in multiple fields should be combined using a whitespace character as a separator. A CFString.

let kMDItemTitle: CFString!

The title of the file. For example, this could be the title of a document, the name of a song, or the subject of an email message. A `CFString`.

let kMDItemVersion: CFString!

The version number of this file. A CFString

let kMDItemWhereFroms: CFString!

Describes where the file was obtained from. A CFArray of CFStrings.

let kMDItemAuthorEmailAddresses: CFString!

This attribute indicates the author of the emails message addresses. (This is always the email address, and not the human readable version). A CFArray of CFStrings.

let kMDItemRecipientEmailAddresses: CFString!

This attribute indicates the recipients email addresses. (This is always the email address, and not the human readable version). A CFArray of CFStrings.

let kMDItemTheme: CFString!

Theme of the this item. A CFString.

let kMDItemSubject: CFString!

Subject of the this item. Type is a CFString.

let kMDItemCFBundleIdentifier: CFString!

If this item is a bundle, then this is the CFBundleIdentifier. A CFString.

let kMDItemFSHasCustomIcon: CFString!

Boolean indicating if this file has a custom icon. Type is a CFBoolean.

let kMDItemFSIsStationery: CFString!

Boolean indicating if this file is stationery. Type is a CFBoolean.

let kMDItemInformation: CFString!

Information about the item. A CFString.

let kMDItemURL: CFString!

Url of the item. A CFString.

