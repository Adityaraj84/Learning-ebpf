## What is ebpf ?
eBPF is a revolutionary technology with origins in the Linux kernel that can run sandboxed programs(user defined program that can safely run inside the linux kernel) in a privileged context such as the operating system kernel. It is used to safely and efficiently extend the capabilities of the kernel without requiring to change kernel source code or load kernel modules.

Today, eBPF is used extensively to drive a wide variety of use cases: Providing high-performance networking and load-balancing in modern data centers and cloud native environments, extracting fine-grained security observability data at low overhead, helping application developers trace applications, providing insights for performance troubleshooting, preventive application and container runtime security enforcement, and much more. 
![Image](https://github.com/user-attachments/assets/cd7d6e2a-1ab0-4760-87b7-095211a57eab)
## ebpf kernel Runtime 
The core engine that run your ebpf program in the Linux kernel.
## Verifier and JIT
Verifier ensure ebpf code is safe before running the program.

JIT(Just-in-Time Compiler ) Convert ebpf bytecode(when you write an ebpf program in c,go etc it get compiled into ebpf bytecode.)  into native machine code(instructions that your specific CPU can directly execute.) for performance.
## Maps 
shared memory structure used to communicate between ebpf(kernel) program and user-space. 
why !? = ebpf runs inside the kernel and can't print, log, or interact directly with user.
## Types of ebpf Maps
Hash(key value store), array(simple indexed base array), stack/queue (FIFO OR LIFO data structure).
## Overview of Hook
eBPF programs don’t run all the time — they only run when something specific happens, like an “event”. or
A hook point is a spot in the system where an event can be detected, and your eBPF code can be triggered.
### Pre-defined hooks include system calls, function entry/exit, kernel tracepoints, network events, and several others
