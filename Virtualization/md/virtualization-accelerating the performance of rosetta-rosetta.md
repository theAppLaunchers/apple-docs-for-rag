

- Virtualization
-  Accelerating the performance of Rosetta 

Article

# Accelerating the performance of Rosetta

Improve Rosetta performance by adding support for the total store ordering (TSO) memory model to your Linux kernel.

## Overview

Rosetta is a translation process that makes it possible to run apps that contain x86_64 instructions on Apple silicon. In macOS, Rosetta allows apps built for Intel-based Mac computers to run seamlessly on Apple silicon, and enables the same capability for Intel Linux apps in ARM Linux VMs.

Rosetta enables Linux distributions running on Apple silicon to support legacy Intel binaries with the addition of a few lines of code in your virtualization-enabled app, and the creation of a directory share for Rosetta to use.

### Optimize the memory model for recompiled x86_64 instructions

By applying a set of kernel optimizations to support the TSO memory model, it’s possible to increase Rosetta performance. The optimizations this patch adds to the Linux kernel sources make the following enhancements to the system:

- Adds support for context-switching the `ACTLR.TSOEN` bit when the thread switches. This optimization allows per-thread setting of the `ACTLR.TSOEN` bit and allows userspace programs to set the `ACTLR.TSOEN` bit of their thread as needed.

- Creates functions that can read and modify the `ACTLR.TSOEN` bit on Apple silicon. Setting this bit to `1` changes the CPU’s memory model to the x86-64 TSO memory model. Clearing it sets the CPU’s memory model to the standard ARM64 memory model.

- Adds a new process control mode to the `prctl` (process control) API that allows userspace programs to change the TSO bit. The process control mode helps emulators that recompile x86_64 instructions to ARM64 instructions. Previously, programs needed to emulate TSO, degrading performance. With this change, emulators can selectively enable TSO for processes that need the emulation. Without selective enablement, the system opts all processes into this memory mode, which degrades performance for native ARM processes that don’t need it.

### Patch the Linux kernel

The Rosetta Linux kernel patches are available to download on Apple’s developer portal; see Rosetta Enhancement Patch.

Warning

Applying patches to and replacing the Linux kernel may result in an unstable or unusable system; the process described below presumes you have experience with kernel patching, and generating and installing new kernel images.

This patch applies cleanly to Linux 6.10 kernel. You can apply these patches to other Linux kernel versions, but they may require some manual editing.

Follow these steps to apply the Rosetta patch:

1.  Download the `RosettaPatch.zip` file into a convenient place on your Mac.

2.  Unzip the archive; it creates a `RosettaPatch` directory that contains a `LICENSE.txt` file and the patch itself, `RosettaPatch.diff`.

3.  Copy the patch file to your Linux system running in your virtualization-enabled app.

4.  Open a new terminal on your Linux system and enable root privileges, for example by using the `sudo` command.

5.  Change directory to the location of your distribution’s kernel sources, typically `/usr/src/linux`.

6.  Apply the patch with the patch command, using the command `patch -p1 Enable Rosetta and activate TSO in your app

To allow Linux apps to take advantage of the TSO memory model, the app needs to call the `prctl` API on each thread that needs TSO support by calling `prctl(PR_SET_MEM_MODEL, PR_SET_MEM_MODEL_TSO)`in order to set the `tso` bit on that thread.

For basic information on Rosetta and running x86_64 binaries on Apple silicon under Linux, see Running Intel Binaries in Linux VMs with Rosetta.

### Provide enhanced Linux kernels or distributions

The Rosetta patches are open source software; you can add them to kernels or distributions you provide to people using your virtualization-enabled app, or include instructions for how people can apply and use the patch in their own kernel builds and take advantage of the optimization.

## See Also

### Virtual machine setup

Running macOS in a virtual machine on Apple silicon

Install and run macOS in a virtual machine using the Virtualization framework.

Running Linux in a Virtual Machine

Run a Linux operating system on your Mac using the Virtualization framework.

Running GUI Linux in a virtual machine on a Mac

Install and run GUI Linux in a virtual machine using the Virtualization framework.

Installing macOS on a Virtual Machine

Download a macOS restore image and install it in a new VM.

Creating and Running a Linux Virtual Machine

Design and run custom Linux guests on Apple silicon or Intel-based Mac Computers.

Virtualize macOS on a Mac

Configure and run macOS guests on Apple silicon.

Virtualize Linux on a Mac

Configure and run Linux guests on Apple silicon and Intel-based Mac computers.

Running Intel Binaries in Linux VMs with Rosetta

Run x86_64 Linux binaries under ARM Linux on Apple silicon.

