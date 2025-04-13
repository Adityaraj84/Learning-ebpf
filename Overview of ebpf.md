## What is ebpf ?
eBPF is a revolutionary technology with origins in the Linux kernel that can run sandboxed programs(user defined program that can safely run inside the linux kernel) in a privileged context such as the operating system kernel. It is used to safely and efficiently extend the capabilities of the kernel without requiring to change kernel source code or load kernel modules.
![Image](https://github.com/user-attachments/assets/cd7d6e2a-1ab0-4760-87b7-095211a57eab)
## ebpf kernel Runtime 
The core engine that run your ebpf program in the Linux kernel.
## Verifier and JIT
Verifier ensure ebpf code is safe before running the program.

JIT(Just-in-Time Compiler ) Convert ebpf bytecode(when you write an ebpf program in c,go etc it get compiled into ebpf bytecode.)  into native machine code(instructions that your specific CPU can directly execute.) for performance.
## Maps 
shared memory structure used to communicate between ebpf(kernel) program and user-space. 
why !? = ebpf runs inside the kernel and can't print, log, or interact directly with user.
