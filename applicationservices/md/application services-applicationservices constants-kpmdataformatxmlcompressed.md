

- Application Services
- ApplicationServices Constants
-  kPMDataFormatXMLCompressed 

Global Variable

# kPMDataFormatXMLCompressed

macOS 10.5+

``` source
var kPMDataFormatXMLCompressed: PMDataFormat { get }
```

## Discussion

Specifies a compressed data format that is approximately 20 times smaller than `kPMDataFormatXMLDefault`. This data format is only compatible with macOS 10.5 and later. This format is a good choice when you do not need to use the data in versions of macOS prior to 10.5 and the minimum data size is important. Note that this format is not a pure XML representation of the data.

