

- Kernel
- Kernel Functions
-  send_vfs_resolve_dir_with_audit_token 

Function

# send_vfs_resolve_dir_with_audit_token

macOS 12.0+

``` source
kern_return_t send_vfs_resolve_dir_with_audit_token(mach_port_t nspace_handler_port, uint32_t req_id, uint32_t op, nspace_name_t file_name, nspace_path_t path, audit_token_t req_atoken);
```

