

- QuickTime File Format
- Structuring movie data and features
- Reference movies
-  Movie importer component flags 

Article

# Movie importer component flags

Flags that adjust the behavior of the movie import component.

## Overview

`canMovieImportInPlace`  
Set this bit if a movie import component must be able to create a movie from a file without having to write to a separate disk file. Examples include MPEG and AIFF import components.

`movieImportSubTypeIsFileExtension`  
Set this bit if the component’s subtype is a file extension instead of a Macintosh file type. For example, if you require an import component that opens files with an extension of .doc, set this flag and set your component subtype to ’DOC ’.

`canMovieImportFiles`  
Set this bit if a movie import component must import files.

## See Also

### Describing reference movies

Reference movie atom ('rmra')

A reference movie atom contains references to one or more movies.

Reference movie descriptor atom ('rmda')

An atom that contains other atoms that describe where to find a particular movie, the system requirements to play that movie, and a quality rating.

Reference movie data reference atom ('rdrf')

An atom that contains the information necessary to locate a movie, stream or file.

Data rate atom ('rmdr')

A data rate atom specifies the minimum data rate required to play a movie.

CPU speed atom ('rmcs')

A CPU speed atom specifies the minimum computing power needed to display a movie.

Version check atom ('rmvc')

A version check atom specifies a software package, such as QuickTime or QuickTime VR, and the version of that package needed to display a movie.

Component detect atom ('rmcd')

A component detect atom specifies a QuickTime component, such as a particular video decompressor, required to play the movie.

Quality atom ('rmqu')

A quality atom describes the relative quality of a movie.

