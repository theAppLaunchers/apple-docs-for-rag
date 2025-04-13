

- Core Foundation
-  CFStringTokenizerCreate(\_:\_:\_:\_:\_:) 

Function

# CFStringTokenizerCreate(\_:\_:\_:\_:\_:)

Returns a tokenizer for a given string.

iOS 3.0+iPadOS 3.0+Mac Catalyst 13.1+macOS 10.5+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func CFStringTokenizerCreate(
    _ alloc: CFAllocator!,
    _ string: CFString!,
    _ range: CFRange,
    _ options: CFOptionFlags,
    _ locale: CFLocale!
) -> CFStringTokenizer!
```

## Parameters 

`alloc`  

The allocator to use to allocate memory for the new object. Pass `NULL` or kCFAllocatorDefault to use the current default allocator.

`string`  

The string to tokenize.

`range`  

The range of the characters in `string` to tokenize.

`options`  

A tokenization unit option that specifies how `string` should be tokenized. The options can be modified by adding unit modifier options to tell the tokenizer to prepare specified attributes when it tokenizes `string`. For possible values, see Tokenization Modifiers.

`locale`  

A locale that specifies language- or region-specific behavior for the tokenization. You can pass `NULL` to use the default system locale, although this is typically not recommended—instead use CFLocaleCopyCurrent() to specify the locale of the current user. For more information, see Tokenization Modifiers.

## Return Value

A tokenizer to analyze the range `range` of `string` for the given locale and options. Ownership follows the The Create Rule.

