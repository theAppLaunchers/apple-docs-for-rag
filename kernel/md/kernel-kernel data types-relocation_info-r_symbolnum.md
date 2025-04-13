

- Kernel
- Kernel Data Types
- relocation_info
-  r_symbolnum 

Instance Property

# r_symbolnum

Indicates either an index into the symbol table (when the `r_extern` field is set to 1) or a section number (when the `r_extern` field is set to 0). As previously mentioned, sections are ordered from 1 to 255 in the order in which they appear in the `LC_SEGMENT` load commands. This field is set to `R_ABS` for relocation entries for absolute symbols, which need no relocation.

macOS 10.8+

``` source
uint32_t r_symbolnum:24;
```

