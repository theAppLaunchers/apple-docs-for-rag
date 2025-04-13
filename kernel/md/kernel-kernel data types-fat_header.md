

- Kernel
- Kernel Data Types
-  fat_header 

# fat_header

macOS 10.8+

``` source
struct fat_header {
    ...
};
```

## Topics

### Instance Properties

magic

An integer containing the value `0xCAFEBABE` in big-endian byte order format. On a big-endian host CPU, this can be validated using the constant `FAT_MAGIC`; on a little-endian host CPU, it can be validated using the constant `FAT_CIGAM`.

nfat_arch

An integer specifying the number of fat_arch data structures that follow. This is the number of architectures contained in this binary.

