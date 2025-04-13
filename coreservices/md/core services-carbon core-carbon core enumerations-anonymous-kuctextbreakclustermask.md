

- Core Services
- Carbon Core
- Carbon Core Enumerations
- Anonymous
-  kUCTextBreakClusterMask 

Global Variable

# kUCTextBreakClusterMask

Mac Catalyst 13.0+macOS 10.0+

``` source
var kUCTextBreakClusterMask: Int { get }
```

## Discussion

If the bit specified by this mask is set, boundaries of character clusters may be located. A cluster is a group of characters that should be treated as single text element for editing operations such as cursor movement. Typically this includes groups such as a base character followed by a sequence of combining characters, for example, a Hangul syllable represented as a sequence of conjoining jamo characters or an Indic consonant cluster.

