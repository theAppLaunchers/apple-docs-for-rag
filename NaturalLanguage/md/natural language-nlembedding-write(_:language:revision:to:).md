

- Natural Language
- NLEmbedding
-  write(\_:language:revision:to:) 

Type Method

# write(\_:language:revision:to:)

Exports the word embedding contained within a Core ML model file at the given URL.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
@nonobjc
class func write(
    _ dictionary: [String : [Double]],
    language: NLLanguage?,
    revision: Int,
    to url: URL
) throws
```

## Parameters 

`dictionary`  

A dictionary of terms, and their vectors, which are represented by an array of doubles.

`language`  

The language of the text in the word embedding.

`revision`  

The revision of the word embedding.

`url`  

The location in the file system to write the file to.

