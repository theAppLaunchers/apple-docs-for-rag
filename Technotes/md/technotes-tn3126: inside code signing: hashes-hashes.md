

- Technotes
-  TN3126: Inside Code Signing: Hashes 

Article

# TN3126: Inside Code Signing: Hashes

Look inside a code signature to see how it uses hashes to protect the code’s executable pages, resources, and metadata from tampering.

## Overview

The vast majority of developers don’t need to know how code signing works. They use Xcode, or the `codesign` tool, and those take care of all the fiddly details. If they run into problems, those problems usually relate to high-level concepts—signing identities, entitlements, provisioning profiles—not the core code signing implementation.

However, that’s not always the case. Every now and again an issue crops up where you actually need to understand how code signing works. For example:

- Using the Latest Code Signature Format has a diagnostic process that involves code signing hash slots. While that process is actionable in and of itself, it makes more sense if you know what those hash slots hold.

- The issue covered by Updating Mac Software makes more sense once you understand code signing’s lazy per-page signature checking.

This technote explains how code signing uses hashes to protect the code’s executable pages, resources, and metadata from tampering. This technology is absolutely central to code signing’s core function: protecting code from malicious modification.

This description isn’t comprehensive. It skips over some details, sometimes because they’re only of historical interest but mostly because they’re not necessary to explain the core concepts.

The examples in this technote are taken from macOS, but these concepts apply to all Apple platforms.

### About this technote series

Code signing is a foundational technology on all Apple platforms. Many documents that discuss code signing focus on solving a specific problem. The *Inside Code Signing* technotes peek behind the code signing curtain, to give you a better understanding of how it works. For a list of all the technotes in this series, see the introduction in TN3125: Inside Code Signing: Provisioning Profiles.

Important

The *Inside Code Signing* technotes discuss code signing details that aren’t considered API. The structure of a code signature has changed numerous times in the past and may well change again in the future. Don’t encode this information in your product. When signing code, use Xcode (all platforms) or the `codesign` tool (macOS only). To get information or validate a code signature, use the `codesign` tool or the Code Signing Services API. Apple updates these facilities to accommodate any changes to the code signature structure as they roll out.

## Code signature storage

The code signature for an item is stored in one of four ways:

- If the item is a Mach-O image, or is a bundle wrapped around a Mach-O image, the code signature is stored within the image using the `LC_CODE_SIGNATURE` load command:

  ```
  % otool -l "AppWithTool.app/Contents/MacOS/AppWithTool" | grep LC_CODE_SIGNATURE -B 1 -A 3 
  Load command 35
        cmd LC_CODE_SIGNATURE
    cmdsize 16
    dataoff 55120
   datasize 19536
  ```

  To build the AppWithTool app used in this example, follow the instructions in Embedding a Command-Line Tool in a Sandboxed App.

  In a universal binary, each architecture is signed independently. For details on the signature of a specific architecture, pass the `-arch` option to `otool`.

- If the item is a bundle without a Mach-O image, the code signature is stored in the bundle’s `_CodeSignature` directory:

  ```
  % codesign --display -vvv Codeless.bundle  
  …
  Format=bundle
  …
  Authority=Apple Development: …
  …
  % find Codeless.bundle 
  Codeless.bundle
  Codeless.bundle/Contents
  Codeless.bundle/Contents/_CodeSignature
  Codeless.bundle/Contents/_CodeSignature/CodeResources
  Codeless.bundle/Contents/_CodeSignature/CodeDirectory
  Codeless.bundle/Contents/_CodeSignature/CodeRequirements-1
  Codeless.bundle/Contents/_CodeSignature/CodeSignature
  Codeless.bundle/Contents/_CodeSignature/CodeRequirements
  Codeless.bundle/Contents/Resources
  Codeless.bundle/Contents/Resources/config.txt
  Codeless.bundle/Contents/Info.plist
  ```

  To build the Codeless bundle used in this example, use Xcode to create a new project from the macOS \> Bundle template, then add an empty `config.txt` file to it.

- If the item exists within a bundle, it’s covered by the bundle’s code signature. For details on how that works, see Resources.

- Otherwise, the code signature is stored in extended attributes (EAs) on the item:

  ```
  % cat hello.txt 
  Hello Cruel World!
  % codesign --sign "Apple Development: …" hello.txt
  % codesign --display -vvv hello.txt
  …
  Format=generic
  …
  Authority=Apple Development: …
  …
  % ls -l@ hello.txt 
  -rw-r--r--@ 1 quinn  staff  19  8 Apr 12:46 hello.txt
      com.apple.cs.CodeDirectory      129 
      com.apple.cs.CodeRequirements   168 
      com.apple.cs.CodeRequirements-1 165 
      com.apple.cs.CodeSignature      4860 
  ```

Important

Storing a code signature in EAs is brittle because many file transfer mechanisms drop these. To avoid this potential pitfall, follow the rules in Placing Content in a Bundle.

For more information about the tools used in these examples, read their man pages. If you’re unfamiliar with that process, see Reading UNIX Manual Pages. Specifically, the `codesign` man page is the key reference if you’re working at this level.

## Code directory

The central concept in a code signature is the *code directory*. This is a data structure that holds all of the info about the code that was signed. It’s this data structure that’s signed as part of the signing process. Hashes within this data structure seal the executable pages, resources, and metadata of the code.

Note

The final code signature uses Cryptographic Message Syntax. To learn more about this implementation detail, see TN3161: Inside Code Signing: Certificates.

In a universal binary, each architecture is signed independently, each with its own code directory.

Hashing a code directory results in a *code directory hash*, or *cdhash*. This value uniquely identifies the code being signed. It crops up in a variety of places, most notably notarization. A notarized ticket is a set of cdhash values, signed by the notary service to confirm that it has checked that code for malicious components.

The code may have multiple code directories, each associated with a different hash algorithm. This hash algorithm is used both to seal the code directory itself and to seal the executable pages, resources, and metadata of the code. This approach allows the code to run more securely on modern systems while maintaining compatibility with legacy systems that only support legacy hashing. The detailed mechanics of that are beyond the scope of this technote.

Code that targets macOS 10.12 or later has a single code directory that uses SHA-256 hashing:

```
% codesign --display -vvv "AppWithTool.app"
…
Hash type=sha256 size=32
CandidateCDHash sha256=ff19a91b272a49d1a0f16ee54c672da60f0e116f
CandidateCDHashFull sha256=ff19a91b272a49d1a0f16ee54c672da60f0e116fae890512a3609913a01b488c
Hash choices=sha256
…
CDHash=ff19a91b272a49d1a0f16ee54c672da60f0e116f
…
```

If you change the code’s deploying target to include macOS 10.11, the signature includes both a SHA-256 and a legacy SHA-1 code directory:

```
% codesign --display -vvv --arch x86_64 "AppWithTool for macOS 10.11.app" 
…
Hash type=sha256 size=32
CandidateCDHash sha1=4dbc916a07fb02653ceecef8bef09f43e55cf436
CandidateCDHashFull sha1=4dbc916a07fb02653ceecef8bef09f43e55cf436
CandidateCDHash sha256=dec2275a0e3800fefd1c84c76cd01756984a74c1
CandidateCDHashFull sha256=dec2275a0e3800fefd1c84c76cd01756984a74c1d4cbfb2e97b5ebe7a06e3ce3
Hash choices=sha1,sha256
…
CDHash=dec2275a0e3800fefd1c84c76cd01756984a74c1
…
```

Note

The command above includes the `--arch x86_64` option to show the Intel code signature. Without that `codesign` shows the code signature for the architecture on which you run the command. So, if you’re on Apple silicon, you’ll see the Apple silicon code signature. Apple silicon debuted with macOS 11, and thus Apple silicon code never includes a legacy SHA-1 code directory.

The `CDHash` property is the cdhash value used by this Mac; it’s the strongest `CandidateCDHash` value understood by this version of macOS. The `CandidateCDHash` and `CandidateCDHashFull` properties are alternative cdhash values, each specifying a hash algorithm. The `Full` variant includes the full hash, while the other variant is truncated to 20 bytes to match SHA-1.

Each architecture in a universal binary is signed independently and so has different hash values. To get the hashes for a specific architecture, supply the `--arch` argument:

```
% codesign --display -vvv --arch arm64 "AppWithTool.app"
…
CDHash=118bb46834dd39dad5bc1bc30d991b6467c1be2e
…
% codesign --display -vvv --arch x86_64 "AppWithTool.app"
…
CDHash=ff19a91b272a49d1a0f16ee54c672da60f0e116f
…
```

## Per-page hashes

Within a code directory there are a set of *hash slots*. For a summary, look at the `CodeDirectory` property:

```
% codesign --display -vvv "AppWithTool.app"             
…
CodeDirectory v=20500 size=820 flags=0x10000(runtime) hashes=14+7 location=embedded
…
```

This means there are 14 per-page hash slots and 7 special hash slots. For a dump of these hashes, increase the verbosity to the maximum level by adding three more `-v` options:

```
% codesign --display -vvvvvv "AppWithTool.app"        
…
Page size=4096
    -7=662d7e12de97b1d9bf3a9e4574652bc4d1927f4b989a6b7a1d1380e542f2b4f9
    -6=0000000000000000000000000000000000000000000000000000000000000000
    -5=2198747bee96847909af4417876f446cea964f842bd1fbbdea39f53ff947e0d8
    -4=0000000000000000000000000000000000000000000000000000000000000000
    -3=0244f72a51483d010cda907fb8cb22983d372ca57812abe8c3635cedd42ad8bd
    -2=ef927ca54639a460b9519bd5493c1fb192f521a16e0115060b7cb7bf15ff0217
    -1=e3fc08cfb2a658bc588ac603f8bfc04a54a62f5893d586f710f3005a5a763ad2
     0=7bfc0c37d35be00553e99db6c99ce5670cdb53ce7d9314f0019efd8d73f6c1d3
     1=5fd93dda8b09dd27db333a6743c7da8418b637780fd70ee58c725fe00b7d0e76
     2=5b542d3e7e43ec8328307ae7006fadb6ada0ed4d494e1b8a6ef63d899ef458fe
     3=6671e862ed46786ea31773c13605ebd5cef22d01fb7fbb01cfafd188aef4da99
     4=bb31c395959971aa64e9f04770282377b0e9901de85fbf17ac181990caa99848
     5=ad7facb2586fc6e966c004d7d1d16b024f5805ff7cb47c7a85dabd8b48892ca7
     6=ad7facb2586fc6e966c004d7d1d16b024f5805ff7cb47c7a85dabd8b48892ca7
     7=ad7facb2586fc6e966c004d7d1d16b024f5805ff7cb47c7a85dabd8b48892ca7
     8=36932b34d11fe626253a65b73dd11e9269f4e976ef7df8d56b24098cbb14d462
     9=ad7facb2586fc6e966c004d7d1d16b024f5805ff7cb47c7a85dabd8b48892ca7
    10=ad7facb2586fc6e966c004d7d1d16b024f5805ff7cb47c7a85dabd8b48892ca7
    11=ad7facb2586fc6e966c004d7d1d16b024f5805ff7cb47c7a85dabd8b48892ca7
    12=98257719ba902d349f1644c2e856df9ff887f70f5c2da9387369ddc41a5964f8
    13=1fa1c2d0d552c0e016ca088a31892411bb206e9926e399b6a64ebc4408a296c5
…
```

The negative slots are special. For the details, see Special Slots.

The non-negative slots are for per-page hashes: 0 is the hash for the first page of code, 1 for the second, and so on.

This per-page architecture allows the kernel to check each page as it’s loaded into memory. If a process takes a page fault on a memory mapped file that’s code signed then, as part of satisfying that fault, the kernel may choose to verify the hash of the page’s contents. This allows the system to run a code-signed executable and check its code signature lazily (in the computer science sense of that word).

macOS doesn’t *always* check code as it’s paged in. One key feature of the hardened runtime is that it opts the process into this checking by default. The Disable Executable Memory Protection Entitlement opts you out of this and other security features. Don’t do that!

Note

The Disable Executable Memory Protection Entitlement only has this effect on Intel code. For Apple silicon code, this entitlement leaves page protection enabled, making it equivalent to the Allow Unsigned Executable Memory Entitlement.

## Special slots

Within the code directory the negative hash slots are special. They don’t correspond to code but rather to other data structures. Each slot number corresponds to a specific type of data. Here are some highlights:

- Slot -1 holds a hash of the `Info.plist`.

- Slot -3 holds a hash of the resources.

- Slot -5 holds a hash of the entitlements.

Consider this:

```
% codesign --display -vvvvvv "AppWithTool.app"        
…
Page size=4096
    …
    -1=e3fc08cfb2a658bc588ac603f8bfc04a54a62f5893d586f710f3005a5a763ad2
    …
% shasum -a 256 "AppWithTool.app/Contents/Info.plist"
e3fc08cfb2a658bc588ac603f8bfc04a54a62f5893d586f710f3005a5a763ad2 …
```

The `Info.plist` hash matches the value in its hash slot. Neat-o!

Now consider this advice from Using the Latest Code Signature Format:

*If -5 contains a value and -7 contains a zero value, or is not present, you need to re-sign your app to include the new DER entitlements.*

You should now have a better handle on this diagnostic. Slot -5 holds the hash for the legacy property list entitlements, while slot -7 holds the hash for the new-style DER-encoded entitlements. If you have an iOS app whose signature has an entry in -5 but no entry in -7, then it has entitlements but it’s missing the new-style DER-encoded entitlements and you must re-sign it to be compatible with iOS 15.

## Resources

If your code exist in a bundle then the code signature protects not just your code but the resources in your bundle. Central to this is the `CodeResources` file. Slot -3 in the code directory holds the hash of that file:

```
% codesign --display -vvvvvv "AppWithTool.app"        
…
Page size=4096
    …
    -3=0244f72a51483d010cda907fb8cb22983d372ca57812abe8c3635cedd42ad8bd
    …
…
% shasum -a 256 "AppWithTool.app/Contents/_CodeSignature/CodeResources" 
0244f72a51483d010cda907fb8cb22983d372ca57812abe8c3635cedd42ad8bd …
```

So, if that file changes, the code directory hash changes and you break the seal on the code signature.

Now let’s look at that file:

```
% plutil -convert xml1 -o - "AppWithTool.app/Contents/_CodeSignature/CodeResources"
…

  files

    …

  files2

    …

  rules

    …

  rules2

    …

```

It’s a property list with four top-level dictionaries: `files`, `files2`, `rules`, and `rules2`. Amusingly, three out of four of these items are vestigial. The one that matters is `files2`.

Note

The `files` dictionary contains SHA-1 hashes and is present for compatibility purposes. The `rules` and `rules2` dictionaries contain resource rules, a concept that’s now obsolete. For more on the move away from resource rules, see Technote 2206 macOS Code Signing In Depth.

The `files2` dictionary contains two kinds of items. The first kind of item is a reference to a resource file. For example:

```
% plutil -convert xml1 -o - "AppWithTool.app/Contents/_CodeSignature/CodeResources"
…

  …
  files2

    …
    Resources/Base.lproj/Main.storyboardc/MainMenu.nib

      hash2

      5kxOZMmHqiN+QhVFpWQ8xdn5gPGYk+Yanxi+bYAMWFU=

    …

  …

% base64 -D | xxd -p 
5kxOZMmHqiN+QhVFpWQ8xdn5gPGYk+Yanxi+bYAMWFU=
^D
e64c4e64c987aa237e421545a5643cc5d9f980f19893e61a9f18be6d800c
5855
% shasum -a 256 "AppWithTool.app/Contents/Resources/Base.lproj/Main.storyboardc/MainMenu.nib" 
e64c4e64c987aa237e421545a5643cc5d9f980f19893e61a9f18be6d800c5855 …
```

For each resource file reference, the key is the path of the file, relative to the bundle contents, and the value is a dictionary with a `hash2` property holding the SHA-256 checksum of the file.

The other kind of item in the `files2` dictionary is a macOS nested code reference. For example:

```
% plutil -convert xml1 -o - "AppWithTool.app/Contents/_CodeSignature/CodeResources"
…

  …
  files2

    …
    MacOS/ToolX

      cdhash

      j2kgMbA32V6O/SEDnwa+SlnpJ/s=

      requirement
      anchor apple generic and identifier "com.example.apple-samplecode.AppWithTool.ToolX" and (certificate leaf[field.1.2.840.113635.100.6.1.9] /* exists */ or certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = SKMME9E2Y8)

    …

  …

```

Again, the key is the path of the file, relative to the bundle contents, but now the value is a dictionary with two properties:

- The `cdhash` property holds the code directory hash of the nested code:

  ```
  % base64 -D | xxd -p
  j2kgMbA32V6O/SEDnwa+SlnpJ/s=
  ^D
  8f692031b037d95e8efd21039f06be4a59e927fb
  % codesign --display -vvv "AppWithTool.app/Contents/MacOS/ToolX" 
  …
  CDHash=8f692031b037d95e8efd21039f06be4a59e927fb
  …
  ```

- The `requirement` property holds the designated requirement (DR) of that nested code:

  ```
  % codesign --display -r - "AppWithTool.app/Contents/MacOS/ToolX"  
  …
  designated => anchor apple generic and identifier "com.example.apple-samplecode.AppWithTool.ToolX" … SKMME9E2Y8
  ```

In theory this lets you update the nested code with a new version, as long as it has the same DR. In practice, this facility is not used in standard deployment workflows and is now deprecated.

Important

iOS, watchOS, and tvOS have a different model for nested code. They put strict limits on where you can place nested code. For details on those limits, see Placing Content in a Bundle. Also, when you nest code in an app, the app references that nested code as a collection of resource files rather than using a single nested code reference. Nested code references are only used on macOS.

For more information about code signing requirements, see TN3127: Inside Code Signing: Requirements.

## Revision History

- **2024-02-06** Made minor editorial changes.

- **2022-05-24** Made minor editorial changes.

- **2022-05-03** Republished as TN3126. Reworked the examples to fix bugs and make them easier to reproduce at your desk. Also made significant editorial changes.

- **2022-03-14** First published as “A Peek Behind the Code Signing Curtain” on Apple Developer Forums.

## See Also

### Latest

TN3182: Adding privacy tracking keys to your privacy manifest

Declare the tracking domains you use in your app or third-party SDK in a privacy manifest.

TN3183: Adding required reason API entries to your privacy manifest

Declare the APIs that can potentially fingerprint devices in your app or third-party SDK in a privacy manifest.

TN3184: Adding data collection details to your privacy manifest

Declare the data your app or third-party SDK collects in a privacy manifest.

TN3181: Debugging an invalid privacy manifest

Identify common configurations that cause unsuccessful privacy manifest validation with the App Store.

TN3180: Reverting to App Store Server Notifications V1

Migrate from version 2 to version 1 of App Store Server Notifications using the Modify an App endpoint.

TN3179: Understanding local network privacy

Learn how local network privacy affects your software.

TN3178: Checking for and resolving build UUID problems

Ensure that every Mach-O image has a UUID, and that every distinct Mach-O image has its own unique UUID.

TN3177: Understanding alternate audio track groups in movie files

Learn how alternate groups collect audio tracks, and how to choose which audio track to use in your app.

TN3111: iOS Wi-Fi API overview

Explore the various Wi-Fi APIs available on iOS and their expected use cases.

TN3176: Troubleshooting Apple Pay payment processing issues

Diagnose errors that occur when processing Apple Pay payments, identify common causes, and explore potential solutions.

TN3175: Diagnosing issues with displaying the Apple Pay button on your website

Diagnose common errors received while displaying the Apple Pay button on your website by identifying the underlying causes, and explore potential solutions.

TN3174: Diagnosing issues with the Apple Pay payment sheet on your website

Diagnose errors received while presenting the Apple Pay payment sheet on your website by identifying the underlying causes of common errors and explore their potential solutions.

TN3173: Troubleshooting issues with your Apple Pay merchant identifier configuration

Diagnose errors due to invalid Apple Pay merchant identifier configurations by identifying the underlying causes of common errors and explore their potential solutions.

TN3168: Making your App Clip available in the App Store

Learn how to configure your App Clip to prevent it from being unavailable in the App Store.

TN3124: Debugging coordinate space issues

Learn techniques to help debug any coordinate space issue.

