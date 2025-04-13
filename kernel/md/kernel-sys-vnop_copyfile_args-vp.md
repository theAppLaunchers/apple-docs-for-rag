

- Kernel
- sys
- vnop_copyfile_args
-  vp 

# vp

The vnode for which to page out data.

## See Also

### Fields

pl

UPL describing pages needed to be paged out. If UPL is NULL, then it means the filesystem has opted into VFC_VFSVNOP_PAGEOUTV2 semantics, which means that it will create and operate on its own UPLs as opposed to relying on the one passed down into the filesystem. This means that the filesystem must be responsible for N cluster_pageout calls for N dirty ranges in the UPL.

pl_offset

Offset in UPL from which to start paging out data. Under the new VFC_VFSVNOP_PAGEOUTV2 semantics, this is the offset in the range specified that must be paged out if the associated page is dirty.

f_offset

Offset in file of data needing to be paged out. Under the new VFC_VFSVNOP_PAGEOUTV2 semantics, this represents the offset in the file where we should start looking for dirty pages.

size

Amount of data to page out (in bytes). Under VFC_VFSVNOP_PAGEOUTV2, this represents the size of the range to be considered. The fileystem is free to extend or shrink the specified range to better fit its blocking model as long as the page at 'pl_offset' is included.

flags

UPL-style flags: UPL_IOSYNC, UPL_NOCOMMIT, UPL_NORDAHEAD, UPL_VNODE_PAGER, UPL_MSYNC. Filesystems should generally leave it to the cluster layer to handle these flags. See the memory_object_types.h header in the kernel framework if interested.

ctx

Context to authenticate for pageout request.

