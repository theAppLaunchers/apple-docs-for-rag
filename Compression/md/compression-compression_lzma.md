

- Compression
-  COMPRESSION_LZMA 

Global Variable

# COMPRESSION_LZMA

The LZMA compression algorithm, which is recommended for high-compression ratio.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

``` source
var COMPRESSION_LZMA: compression_algorithm { get }
```

## Discussion

The Compression library implements the LZMA encoder at level 6 only. This is the default compression level for open source LZMA, and provides excellent compression. The LZMA decoder supports decoding data compressed with any compression level.

The Compression library only supports LZMA2 that’s embedded in the XZ container. LZMA2 is a resource-restricted and extended variant of LZMA.

## See Also

### Algorithm Constants

var COMPRESSION_LZFSE: compression_algorithm

The LZFSE compression algorithm, which is recommended for use on Apple platforms.

var COMPRESSION_LZ4: compression_algorithm

The LZ4 compression algorithm for fast compression.

var COMPRESSION_LZ4_RAW: compression_algorithm

The LZ4 compression algorithm, without frame headers.

var COMPRESSION_ZLIB: compression_algorithm

The zlib compression algorithm, which is recommended for cross-platform compression.

var COMPRESSION_BROTLI: compression_algorithm

The Brotli compression algorithm, which is recommended for text compression.

var COMPRESSION_LZBITMAP: compression_algorithm

The LZBITMAP compression algorithm, which is designed to exploit the vector instruction set of current CPUs.

