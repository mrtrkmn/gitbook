
### Objectives of Virtualization

- To enchance the resource sharing by many users at a time.
- To replace and upgrade hardware on the fly (a sort f isolation among guests)
- To add new devices such as network cards, processors, without reboots
- VMs help to reduce the down time
- Virtualization techniques offer administrative tasks such as installing software planning new VMs,
  optimizing number of VMs and so forth at runtime. 
- Faster provisioning of multiple machines


### Basics - Modes of Operation

- Generally, the OS operates in two modes
    - Kernel Mode
        - OS allows all CPU instractions to execute on the underlying hardware ]
        - Kernel codes do not execute in the USER mode
    - User Mode
        - OS allows only a few instructions to be executed
        - If the user applications have to execute the privileged instructions. The applications ask kernels to do the work
        - User applications can't open files, send network packets, print to the screen, or allocate memory
    
- NOTE: 
    - Kernel processes run in the KERNEL mode with the supervisor privilege or superuser privelege
    - User processes run in the USER mode with the user privelege.
    - OS manages processes and threads


### System Calls and CPUs

- OS does
    - Process management (start, run, stop processes)
    - Memory management (Allocate, Deallocate memory)
    - File management (Open, Close, Modify, Read, Rename, Create)
    - Network management (Scheduling, Timing, etc)

- At user mode, the user applications initiate a system call to get OS related services
- There are hundreds of system calls in a 64bit OS. 
    - Eg. sys_enter, sys_exit
- The x86_64 provides > 322 system calls and the x86 provides > 358 different system calls 
- Typically, a system call takes around 242 cycles.


### Bare-Metal Virtualization 

![](../.github/assets/bare-metal.png)

- As multiple OSs should function in a single machine, here
    - hypervisor acts at Ring 0
    - Guest OSs operate at Ring 1
    - Applications operate at Ring 3

- This type of hypervisor is named as **"Bare-metal Hypervisor"**
  E.g: Hyper-V, VMware, ESX/ESXi, XEN

### Hosted Virtualization 

- Here, the hypervisor is loaded on top of an OS. 
- Similar to a computer application/program ! 
- The Guest OS runs on the hosted hypervisors
- Virtualization due to this technology is also named as 
    - Hosted virtualization
- E.g : VMware Workstation, VMWare Fusion, Oracle Virtualbox, Parallels

### Full Virtualization 

- Here, the guest OS is not modified
- Guest OS works in Ring 1; VMM works in Ring 0
- What happens when privilege instructions are executed ? 
    - Every privilege instructions are trapped ( ie. requires a s/w  interrupt) due to the execution in the less privileged ring
    - The VMM intercepts such traps and emulates the instruction on the fly ( IBM S/670)

- Challenge!!!  This approach was not successful in intel x86 machines 
    - over 17 privileged instructions were not trapped by VMM. A failure! 

- In the meantime, VMware was succussfull to implement a binary translator (i.e x86 to x86 translator which overrides such privileged instructions)
    - It translates the binary code and places them in the translation cache

### Impacts of System Call and I/O virtualization

#### Impact of system calls:

    - A binary translated system call with the 32-bit guest OS running on ring 1 takes around 2300 cycles
        - This is due to the fact that CPU issues fault message for every system calls. Later, they were translated and executed,

#### Impact of I/O virtualization

- I/O virtualizaiton is a major issue compared to CPU virtualization. 
- Why ?
    - CPUs could be added by replacing dual-core CPU to quad cores
    - But, memory bandwidth or data path or I/O chipset could not be easily modified/upgraded in a computing machine
- All guest OS should wait for the physical I/O

### Impact of Memory Virtualization

- In fact, virtual memories were introduced in order to reduce system crash !!
- Virtual memory is a memory management technique. 
    - It maps programs' memory addresses (called as Virtual addresses) to the underlying physcial machine memory (in computer)
    - Useually, OS maintains the mapping of virtual memory to physical memory
    - Adv: increased security, isolation, freeing applications
    - 
    ![](../.github/assets/memory-impact.jpg)



- In VMs, we have hypervisors !! if so, how mapping happens ?

    - Here, programs' memory addresses (virtual addresses of VMs) are mapped to Virtual Physical Memory and then to physical memory. 
    - It is a 2-stage mapping process for any guest OS
    - Thus, guest OS cannot directly access the machine memory
    - VMM does the mapping of addresses
    - The page table in VMM is called a shadow page table. 
    - The shadow paging process takes 3 to 400 times more cycles native situations
    - 

    ![](../.github/assets/memory-impact-v2.jpg)


### Para Virtualization

- Here, guest OS needs to be modified at the source code level,  i.e no need for trapping and binary rewriting...

- Runtime changes are avoided. 
    - It avoids on-the-fly modifications due to transformation (eliminates traps)

- Hypervisor provides interfaces to accommodate critical kernel operations such as memory management and intterupt handling

- Performance is comparatively good. 
    - Because, para virtualization **avoids unnecessary trapping** of critical instructions.
    - Thus, the advantage of paravirtualization is to have a lower virtualization overhead
    - But, the challenge is that you need a **modified guest OS**


### Hardware-Assisted VIrtualization 

- A hardware-assisted virtualization support is also available for Intel and AMD
    - VT-x - named as Virtualization Technology
    - Eg. Intel VT-x (formerly, Vanderpool Technology)
    - Eg. Intel VT-i (Vanderpool Technology for itanium)
    - Eg. AMD has AMD-v
    - H/W virtualization support should be enabled in the BIOS setup


#### Purpose - Hardware Assisted Virtualization 

- The purpose of hardware assisted virtualization is not to just add hardware for doing binary translation !!
- The main idea is to quickly identify the privilege instructions and to effficiently execute them. 
    - To do so, one more high priority layer was introduced at the hardware level
    - VMM works at his level and guest OS could operate at Ring 0
    - 
    ![](../.github/assets/vt-x.jpg)
