

- TV Services
- TVTopShelfContentStyle
-  TVTopShelfContentStyle.sectioned Deprecated

Case

# TVTopShelfContentStyle.sectioned

When using the sectioned style, your extension should return an array that contains content items that represent sections. Each section object should have an array of content items that represent the available media in that section.

tvOS 9.0–13.0Deprecated

``` source
case sectioned
```

Deprecated

TVTopShelfProvider has been replaced by TVTopShelfContent

## See Also

### Constants

case inset

When the using the inset style, your extension should return a flat array of TV content items. The images of the content items will take up most of the area of the Top Shelf, which will slowly rotate through the items.

Deprecated

