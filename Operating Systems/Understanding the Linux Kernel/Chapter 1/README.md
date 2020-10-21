# Chapter 1

- Linux is a member of the Unix-like operating system family (hereby referred to as, "ULOSes").
- Other members of this family include:
  1. System V Release 4
  2. Berkeley Software Distribution 4.4
  3. Digital Unix
  4. AIX
  5. HP-UX
  6. Solaris
  7. MacOS
  8. FreeBSD (Opensource)
  9. NetBSD (Opensource)
  10. OpenBSD (Opensource)
- It was created by Linus Torvalds in 1991 for the Intel i386 microprocessor.
- It is still kept up-to-date today with thousands of developers working on it.
- It is available for many other architectures other than the i386.
- It isn't a commercial operating system.
- Its source code is under the GNU General Public License (GPL) and is open and available for anyone to study.
- _Linux_ is a registered trademark of Linux Torvalds.
- The GNU project in under the Free Software Foundation (FSF).
- The foundation has an aim of creating a whole operating system free for everyone.
- It has made available the GNU C compiler which was essential for the success of the Linux OS.
- Linux is a Unix kernel but not a Unix operating system.
- This is because Linux does not contain other utilities for general-purpose operating system.
- These utilities are provided free by GNU so, people can just install them after installing the kernel.
- The source code can be downloaded from www.kernel.org.

## Linux vs. Other ULOSes
- All ULOSes tend to agree on common standards like the IEEE Portable Operating Systems based on Unix (POSIX) standard or the X/Open Common Applications Environment (CAE).
- These standards provide interfaces that need to be offered to user programs by the kernel.
- This will allow applications to have the same source code while calling operating system resources.
- The standard does not define the internal implementation of these APIs and therefore, the operating system can implement its own way to service the user application's request.
< INSERT FIGURE ON STANDARD >
- This means that most Unix applications build for other ULOSes can be compiled without any changes to the source code for Linux as well.
- This also means that most ULOses also share a common design philosophy since they must share interfaces for the APIs.
- Linux tries to take the best from each ULOS and implement it.
- Linux is a monolithic kernel. This means that the entire kernel is compiled as a single binary that runs in kernel mode.
- This is unlike microkernel implementations like GNU HURD and MacOS which is based off of the Carnegie-Mellon's Mach microkernel.
- Linux allows dynamic linking of portions of kernel code through the use of **modules**.
- These modules can be loaded and unloaded into the kernel _on-demand_.
- Linux supports limited kernel threading.
- Kernel threads runs kernel procedues and may even be associated with a user program.
- Context switches betweek kernel threads are much less expensive than process switches since the former acts on a shared address space (so there is no need to flush the address space with each switch).
- On most other ULOS, kernel thread form the basic execution context. However, on Linux, this is not true.
- Linux also supports multithreaded applications - applications which are designed as multiple independent execution flows with each of them acting on a common address space.
- Linux's basic execution context is the light-weight process (LWP) which are processes which act on common address spaces (common memory, files, etc.).
- LWPs are handled using the `clone()` system call.
- Linux allows for kernel-mode premption if enabled during compilation (through compilation flags).
- This will allow kernel flows to be interleaved.
- It also allows for _fixed premption points_.
- Linux supports multiple processors.
- Symmetric multi-processing (SMP) for different memory models (including Non-Uniform Memory Access (or NUMA)).
- Some critical paths can/will still be used under a giant kernel-lock.
- Linux supports the powerful **Virtual File System** feature that allows many different file-systems to be used with Linux.
- Therefore, it is easy to port a file-system to Linux.
- Linux doesn't support the STREAMS I/O subsystem due to performance impacts on the kernel operation.
- Linux is cost-free.
- Linux is customizable thanks to the use of feature flags during compilation.
- Linux also allows you to modify the source code since it's open source.
- Linux can run on low-end hardware.
- Linux is powerful and catered to high performance and speed.
- Linux is created by excellent programmers so they have a high stability and low failure-rate.
- Linux is small and compact.
- It is highly compatible with other operating systems.
  - You can mount file-systems from other operating systems (like NTFS (Windows) and HFS (MacOS)).
  - Given the right libraries, you can also run applications compiled for other operating systems on Linux.
- Linux is well-supported due to the large developer base and the open source nature of the kernel.

## Hardware Dependency
- Linux separates hardware dependent code from the rest of the source code.
- The `include` and `arch` directory contain hardware architecture dependent code.

## Linux Versions
- Linux 2.5
  - eg. X.Y.Z
  - X represents the major versions
  - Y represents stable (even) or developer (odd)
  - Z represents the release.
- Linux 2.6+
  - eg. X.Y.Z.A
  - X represents the major version
  - Y represents the minor version (this will change only for disruptive changes)
  - Z represents releasese.
  - A represents patcheWs for fixes since there are no developer and stable versions anymore.

## Basic Operating System Concepts
- Each computer includes a basic set of programs called operating systems.
- The *kernel* is one such program.
- It is loaded into the RAM when the system boots and contains all the procedues required for the system to operate.
- Operating systems have 2 major functions:
  1. Interact with the hardware compoenents, servicing all low-level programmable elements included in the hardware platform.
  2. Provide an execution environment to the applications that run on the computer system.
- Older operating systems (like MS-DOS) allowed user programs to operate on the actual hardware address space - allowing access to the entire hardware.
- For security concerns, Unix abstracts away all the hardware access and complexities and provides a much more simpler (and secure) playground for the userspace applications.
- If a user program wants to access the hardware, it needs to request the operating system and if approved, the operating system will itself manage the hardware on behalf of the user.
- In order to enforce this, the hardware needs to provide support to distinguish between applications and operating systems.
- CPUs like ARM and x86 have different protection modes for this purpose.
- Unix called them **User Mode** and **Kernel Mode**.

### Multiuser Systems
-
