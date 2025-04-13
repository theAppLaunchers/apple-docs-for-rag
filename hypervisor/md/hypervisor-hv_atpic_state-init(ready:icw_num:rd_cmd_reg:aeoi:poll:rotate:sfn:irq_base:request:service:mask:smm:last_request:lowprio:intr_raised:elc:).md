

- Hypervisor
- hv_atpic_state
-  init(ready:icw_num:rd_cmd_reg:aeoi:poll:rotate:sfn:irq_base:request:service:mask:smm:last_request:lowprio:intr_raised:elc:) 

Initializer

# init(ready:icw_num:rd_cmd_reg:aeoi:poll:rotate:sfn:irq_base:request:service:mask:smm:last_request:lowprio:intr_raised:elc:)

macOS

``` source
init(
    ready: Bool,
    icw_num: UInt8,
    rd_cmd_reg: UInt8,
    aeoi: Bool,
    poll: Bool,
    rotate: Bool,
    sfn: Bool,
    irq_base: UInt8,
    request: UInt8,
    service: UInt8,
    mask: UInt8,
    smm: Bool,
    last_request: UInt8,
    lowprio: UInt8,
    intr_raised: Bool,
    elc: UInt8
)
```

