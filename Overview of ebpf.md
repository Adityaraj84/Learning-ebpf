## What is ebpf ?
eBPF is a revolutionary technology with origins in the Linux kernel that can run sandboxed programs(user defined program that can safely run inside the linux kernel) in a privileged context such as the operating system kernel. It is used to safely and efficiently extend the capabilities of the kernel without requiring to change kernel source code or load kernel modules.

Today, eBPF is used extensively to drive a wide variety of use cases: Providing high-performance networking and load-balancing in modern data centers and cloud native environments, extracting fine-grained security observability data at low overhead, helping application developers trace applications, providing insights for performance troubleshooting, preventive application and container runtime security enforcement, and much more. 
![Image](https://github.com/user-attachments/assets/cd7d6e2a-1ab0-4760-87b7-095211a57eab)
## ebpf kernel Runtime 
The core engine that run your ebpf program in the Linux kernel.
## Verifier and JIT
Verifier ensure ebpf code is safe before running the program.

JIT(Just-in-Time Compiler ) Convert ebpf bytecode(when you write an ebpf program in c,go etc it get compiled into ebpf bytecode.)  into native machine code(instructions that your specific CPU can directly execute.)  to optimize execution speed of the program
## Maps 
shared memory structure used to communicate between ebpf(kernel) program and user-space. 
why !? = ebpf runs inside the kernel and can't print, log, or interact directly with user.
## Types of ebpf Maps
Hash(key value store), array(simple indexed base array), stack/queue (FIFO OR LIFO data structure).
## Overview of Hook
eBPF programs don’t run all the time — they only run when something specific happens, like an “event”. or
A hook point(A specific event location like sysclall, Network etc.) spot in the system where an event can be detected, and your eBPF code can be triggered.
### Pre-defined hooks include system calls, function entry/exit, kernel tracepoints, network events, and several others

![Image](https://github.com/user-attachments/assets/fe2b2ed4-1d38-4960-93ae-c9d44fdd8484)

### If a predefined hook does not exist for a particular need, it is possible to create a kernel probe (kprobe) or user probe (uprobe) to attach eBPF programs almost anywhere in kernel or user applications.
![Image](https://github.com/user-attachments/assets/eb781274-525d-4039-9bbb-dd8d7d59ed00)
## How are eBPF programs written?
![Image](https://github.com/user-attachments/assets/ba13daa1-3bca-43f2-b3a0-15057fd9ac8b)

The Linux kernel expects eBPF programs to be loaded in the form of bytecode.
While it is of course possible to write bytecode directly, the more common development practice is to leverage a compiler suite like LLVM to compile pseudo-C code into eBPF bytecode.
## what is Loader ?
When the desired hook has been identified, the eBPF program can be loaded into the Linux kernel using the bpf system call. This is typically done using one of the available eBPF libraries.
## Architecture of Loader 
![Image](https://github.com/user-attachments/assets/3d048b33-7abe-4834-b408-6133a7478a9f)
## Architecture of Verification 

The verification step ensures that the eBPF program is safe to run. It validates that the program meets several conditions, for example:

1. The process loading the eBPF program holds the required capabilities (privileges). Unless unprivileged eBPF is enabled, only privileged processes can load eBPF programs.
2. The program does not crash or otherwise harm the system.
3. The program always runs to completion (i.e. the program does not sit in a loop forever, holding up further processing).
![Image](https://github.com/user-attachments/assets/d2b6d8e6-3149-4952-9bb5-970a994ef08c)
