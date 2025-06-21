Framework

# DriverKit

Develop device drivers that run in user space.

DriverKit 19.0+iOS 16.0+iPadOS 16.0+macOS 10.15+

## [Overview](/documentation/DriverKit#overview)

The DriverKit framework defines the fundamental behaviors for device drivers in macOS and iPadOS. The C++ classes of this framework define your driver’s basic structure, and provide support for handling events and allocating memory. This framework also supports appropriate types for examining the numbers, strings, and other types of data in your driver’s I/O registry entry. Other frameworks, such as [USBDriverKit](/documentation/USBDriverKit), [HIDDriverKit](/documentation/HIDDriverKit), [NetworkingDriverKit](/documentation/NetworkingDriverKit), [PCIDriverKit](/documentation/PCIDriverKit), [SerialDriverKit](/documentation/SerialDriverKit), and [AudioDriverKit](/documentation/AudioDriverKit), provide the specific behaviors you need to support different types of devices.

The drivers you build with DriverKit run in user space, rather than as kernel extensions, which improves system stability and security. You create your driver as an app extension and deliver it inside your existing app.

In macOS, use the [System Extensions](/documentation/SystemExtensions) framework to install and upgrade your driver. In iPadOS, the system automatically discovers and upgrades drivers along with their host apps.

Note

The base DriverKit framework is available in macOS for Apple silicon and Intel-based Mac computers, and in iPadOS for devices with an M-series chip. The availability of family frameworks like [USBDriverKit](/documentation/USBDriverKit) and [AudioDriverKit](/documentation/AudioDriverKit) varies by platform.

## [Topics](/documentation/DriverKit#topics)

### [Essentials](/documentation/DriverKit#Essentials)

[

Implementing drivers, system extensions, and kexts](/documentation/kernel/implementing_drivers_system_extensions_and_kexts)

Create drivers and system extensions to communicate with hardware and provide low-level services, and only use kernel extensions for a few tasks.

[

Creating drivers for iPadOS](/documentation/driverkit/creating-drivers-for-ipados)

Bring your drivers to iPadOS by using the platform’s DriverKit support.

### [Entitlements](/documentation/DriverKit#Entitlements)

[

Requesting Entitlements for DriverKit Development](/documentation/driverkit/requesting-entitlements-for-driverkit-development)

Request the entitlement for DriverKit development, and request other entitlements your driver needs to interact with specific devices and interfaces.

[`com.apple.developer.driverkit`](/documentation/BundleResources/Entitlements/com.apple.developer.driverkit)

A Boolean value that indicates whether your extension has permission to run as a user-space driver.

[`com.apple.developer.driverkit.userclient-access`](/documentation/BundleResources/Entitlements/com.apple.developer.driverkit.userclient-access)

An array of strings that represent macOS driver extensions that may communicate with other DriverKit services.

[`com.apple.developer.driverkit.allow-any-userclient-access`](/documentation/BundleResources/Entitlements/com.apple.developer.driverkit.allow-any-userclient-access)

A Boolean value that determines whether a macOS driver accepts user client connections from any application.

[`Communicates with Drivers`](/documentation/BundleResources/Entitlements/com.apple.developer.driverkit.communicates-with-drivers)

A Boolean value that indicates whether an iPadOS app can communicate with drivers.

[`DriverKit Allow Third Party User Clients`](/documentation/BundleResources/Entitlements/com.apple.developer.driverkit.allow-third-party-userclients)

A Boolean value that indicates whether an iPadOS driver accepts calls from third-party user clients.

### [Samples](/documentation/DriverKit#Samples)

[

API Reference

DriverKit sample code](/documentation/driverkit/driverkit-sample-code)

Explore projects that demonstrate how to write macOS device drivers with the DriverKit family of frameworks.

### [Services](/documentation/DriverKit#Services)

[

Creating a Driver Using the DriverKit SDK](/documentation/driverkit/creating-a-driver-using-the-driverkit-sdk)

Create a driver that supports proprietary features of your company’s hardware devices.

[

Debugging and testing system extensions](/documentation/driverkit/debugging-and-testing-system-extensions)

Debug your system extensions by temporarily disabling the security checks that macOS performs during the installation process.

[`IOService`](/documentation/driverkit/ioservice)

The base class for managing the setup and registration of your driver.

### [Event management](/documentation/DriverKit#Event-management)

[`IODispatchQueue`](/documentation/driverkit/iodispatchqueue)

An object that manages the serial execution of blocks.

[`IOInterruptDispatchSource`](/documentation/driverkit/iointerruptdispatchsource)

A dispatch source that reports hardware-related interrupt events to your driver.

[`IOTimerDispatchSource`](/documentation/driverkit/iotimerdispatchsource)

A dispatch source that notifies your driver at a specific time.

[`IODataQueueDispatchSource`](/documentation/driverkit/iodataqueuedispatchsource)

A dispatch source that manages a shared-memory data queue.

[`IODispatchSource`](/documentation/driverkit/iodispatchsource)

The common base class for dispatch sources.

[`OSAction`](/documentation/driverkit/osaction)

An object that executes your driver’s custom behavior.

### [Memory management](/documentation/DriverKit#Memory-management)

[`IOBufferMemoryDescriptor`](/documentation/driverkit/iobuffermemorydescriptor)

A memory buffer allocated in the caller’s address space.

[`IOMemoryDescriptor`](/documentation/driverkit/iomemorydescriptor)

The base class for describing a location in memory.

[`IOMemoryMap`](/documentation/driverkit/iomemorymap)

A reference to an existing block of memory in the current process or in a different process.

[

API Reference

Memory Utilities](/documentation/driverkit/memory-utilities)

Allocate and deallocate memory and manage memory pointers in different address spaces.

### [Registry data types](/documentation/DriverKit#Registry-data-types)

[`OSArray`](/documentation/driverkit/osarray)

A container for an ordered, random-access collection of objects.

[`OSDictionary`](/documentation/driverkit/osdictionary)

A container for a collection with elements that are key-value pairs.

[`OSBoolean`](/documentation/driverkit/osboolean)

A container for a true or false value.

[`OSData`](/documentation/driverkit/osdata)

A container for untyped data.

[`OSNumber`](/documentation/driverkit/osnumber)

A container for an integer value.

[`OSString`](/documentation/driverkit/osstring)

A container for managing an array of characters.

[`OSSerialization`](/documentation/driverkit/osserialization)

A container for one or more objects, serialized in a binary data format that is suitable for messaging.

[`OSCollection`](/documentation/driverkit/oscollection)

The base class for DriverKit collection objects.

[`OSContainer`](/documentation/driverkit/oscontainer)

The base class for DriverKit data objects.

[`OSObject`](/documentation/driverkit/osobject)

The base class for DriverKit objects

[`OSSymbol`](/documentation/driverkit/ossymbol)

A container for managing an array of characters.

[`IOFixed`](/documentation/driverkit/iofixed)

A fixed-point number.

### [External drivers](/documentation/DriverKit#External-drivers)

[`IOUserClient`](/documentation/driverkit/iouserclient)

A connection to another service that the system manages.

[`IOUserServer`](/documentation/driverkit/iouserserver)

A system-managed service.

[`com.apple.developer.driverkit.userclient-access`](/documentation/BundleResources/Entitlements/com.apple.developer.driverkit.userclient-access)

An array of strings that represent macOS driver extensions that may communicate with other DriverKit services.

[

Communicating between a DriverKit extension and a client app](/documentation/driverkit/communicating-between-a-driverkit-extension-and-a-client-app)

Send and receive different kinds of data securely by validating inputs and asynchronously by storing and using a callback.

### [Runtime support](/documentation/DriverKit#Runtime-support)

[`OSDynamicCast`](/documentation/driverkit/osdynamiccast)

Casts an object safely to the specified type, if possible.

[`OSRequiredCast`](/documentation/driverkit/osrequiredcast)

Casts the object to the specified type, stopping the process if the object isn’t of the correct type.

[`IMPL`](/documentation/driverkit/impl)

Tells the system that the superclass implementation of this method runs in the kernel.

[`TYPE`](/documentation/driverkit/type)

Annotates a method declaration to indicate that it conforms to an existing method signature.

[`QUEUENAME`](/documentation/driverkit/queuename)

Tells the system to execute a method on the dispatch queue with the specified name.

[`SUPERDISPATCH`](/documentation/driverkit/superdispatch)

Tells the system to execute the superclass’ implementation of the current method in the kernel.

[`IIG_KERNEL`](/documentation/driverkit/iig_kernel)

Tells the system that the class or method runs inside the kernel.

[`LOCAL`](/documentation/driverkit/local)

Tells the system that the method runs locally in the driver extension’s process space.

[`LOCALONLY`](/documentation/driverkit/localonly)

Tells the system that the class or method runs locally in the driver extension’s process space.

[

API Reference

Error Codes](/documentation/driverkit/error-codes)

Determine the reason an operation fails.

[

API Reference

C++ Runtime Support](/documentation/driverkit/c-runtime-support)

Examine low-level types that DriverKit uses to support kernel-level operations.

### [Classes](/documentation/DriverKit#Classes)

[`IOHistogramReporter`](/documentation/driverkit/iohistogramreporter)

[`IOReportLegend`](/documentation/driverkit/ioreportlegend)

[`IOReporter`](/documentation/driverkit/ioreporter)

[`IOServiceStateNotificationDispatchSource`](/documentation/driverkit/ioservicestatenotificationdispatchsource)

[`IOSimpleReporter`](/documentation/driverkit/iosimplereporter)

[`IOStateReporter`](/documentation/driverkit/iostatereporter)

[`OSBundle`](/documentation/driverkit/osbundle)

[`OSMappedFile`](/documentation/driverkit/osmappedfile)

### [Reference](/documentation/DriverKit#Reference)

[

API Reference

DriverKit Structures](/documentation/driverkit/driverkit-structures)

[

API Reference

DriverKit Enumerations](/documentation/driverkit/driverkit-enumerations)

[

API Reference

DriverKit Constants](/documentation/driverkit/driverkit-constants)

[

API Reference

DriverKit Functions](/documentation/driverkit/driverkit-functions)

[

API Reference

DriverKit Data Types](/documentation/driverkit/driverkit-data-types)

[

API Reference

DriverKit Namespaces](/documentation/driverkit/driverkit-namespaces)

### [Macros](/documentation/DriverKit#Macros)

[

API Reference

Macros](/documentation/driverkit/driverkit-macros)

[`kIOPropertyHashTypeKey`](/documentation/driverkit/kiopropertyhashtypekey)

[`kIOPropertySHA3256Key`](/documentation/driverkit/kiopropertysha3256key)

[`kIOPropertySHA3384Key`](/documentation/driverkit/kiopropertysha3384key)

[`kIOPropertySHA3512Key`](/documentation/driverkit/kiopropertysha3512key)

### [Enumeration Cases](/documentation/DriverKit#Enumeration-Cases)

[`kIOServicePMAssertionCPUBit`](/documentation/driverkit/kioservicepmassertioncpubit)

kIOServicePMAssertionCPUBit When set, PM kernel will prefer to leave the CPU and core hardware running in “Dark Wake” state, instead of sleeping.

[`kIOServicePMAssertionForceFullWakeupBit`](/documentation/driverkit/kioservicepmassertionforcefullwakeupbit)

kIOServicePMAssertionForceFullWakeupBit When set, the system will immediately do a full wakeup after going to sleep.

[`kIOServicePowerCapabilityLPW`](/documentation/driverkit/kioservicepowercapabilitylpw)

[`kSCSICmd_ATA_PASS_THROUGH`](/documentation/driverkit/kscsicmd_ata_pass_through)

[`kSCSICmd_ATA_PASS_THROUGH_EXT`](/documentation/driverkit/kscsicmd_ata_pass_through_ext)