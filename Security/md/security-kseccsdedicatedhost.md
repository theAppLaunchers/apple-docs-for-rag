

- Security
-  kSecCSDedicatedHost 

Global Variable

# kSecCSDedicatedHost

Declares dedicated hosting for the given host.

Mac Catalyst 13.0+macOS 10.0+

``` source
var kSecCSDedicatedHost: UInt32 { get }
```

## Mentioned in 

Hosting Guest Code

## Discussion

In dedicated hosting, the host has exactly one guest (the one this call specifies) and the host spends all of its time running that guest (or running on its behalf). This declaration is irreversible for the lifetime of the host. If the guest terminates, the host terminates as well. Any code object that refers to a dedicated host is assumed by the system to be referring to the guest. Note that this is a declaration about the given host, and is not binding on other hosts on either side of the hosting chain (though they may declare dedicated hosting as well).

It is invalid to declare dedicated hosting if the host already has other guests, and it is invalid to introduce additional guests for this host after this call.

