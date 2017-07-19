# Embedded_Interview
Linux Device Model (LDM)

1. Explain about the Linux Device Model (LDM)?
2. Explain about about ksets, kobjects and ktypes. How are they related?

Questions about sysfs.

Linux Boot Sequence
1. Explain about the Linux boot sequence in case of ARM architecture?
2. How are the command line arguments passed to Linux kernel by the
u-boot (bootloader)?
3. Explain about ATAGS?
4. Explain about command line arguments that are passed to linux
kernel and how/where they are parsed in kernel code?
5. Explain about device tree.

Interrupts in Linux

1. Explain about the interrupt mechanims in linux?
2. What are the APIs that are used to register an interrupt handler?
3. How do you register an interrupt handler on a shared IRQ line?
4. Explain about the flags that are passed to request_irq().
5. Explain about the internals of Interrupt handling in case of Linux
running on ARM.
6. What are the precautions to be taken while writing an interrupt handler?
7. Explain interrupt sequence in detail starting from ARM to
registered interrupt handler.
8. What is bottom half and top half.
9. What is request_threaded_irq()
10.If same interrupts occurs in two cpu how are they handled?
11.How to synchronize data between 'two interrupts' and 'interrupts
and process'.
12.How are nested interrupts handled?
13.How is task context saved during interrupt.

Bottom-half Mechanisms in Linux

1. What are the different bottom-half mechanisms in Linux?
2. Softirq, Tasklet and Workqueues
3. What are the differences between Softirq/Tasklet and Workqueue?
Given an example what you prefer to use?
4. What are the differences between softirqs and tasklets?
5. Softirq is guaranteed to run on the CPU it was scheduled on, where
as tasklets don’t have that guarantee.
    The same tasklet can't run on two separate CPUs at the same time,
where as a softirq can.
6. When are these bottom halfs executed?
7. Explain about the internal implementation of softirqs?
    Bottom-halves in Linux - Part 1: Softirqs
8. Explain about the internal implementation of tasklets?
    Bottom-halves in Linux - Part 2: Tasklets
9. Explain about the internal implementation of workqueues?
    Bottom-halves in Linux - Part 3: Workqueues
10. Explain about the concurrent work queues.

Linux Memory Management

1. What are the differences between vmalloc and kmalloc? Which is
preferred to use in device drivers?
2. What are the differences between slab allocator and slub allocator?
3. What is boot memory allocator?
4. How do you reserve block of memory?
5. What is virtual memory and what are the advanatages of using virtual memory?
6. What's paging and swapping?
7. Is it better to enable swapping in embedded systems? and why?
8. What is the page size in Linux kernel in case of 32-bit ARM architecture?
9. What is page frame?
10.What are the different memory zones and why does different zones exist?
11.What is high memory and when is it needed?
12.Why is high memory zone not needed in case of 64-bit machine?
13.How to allocate a page frame from high memory?
14.In ARM, an abort exception if generated, if the page table doesn't
contain a virtual to physical map for a particular page. How
exactly does the MMU know that a virtual to physical map is present in
the pagetable or not?
    A Level-1 page table entry can be one of four possible types. The
1st type is given below:
    A fault entry that generates an abort exception. This can be
either a prefetch or data abort, depending on the type of access.
   This effectively indicates virtual addresses that are unmapped.
    In this case the bit [0] and [1] are set to 0. This is how the MMU
identifies that it's a fault entry.
    Same is the case with Level-2 page table entry.
15.Does the Translation Table Base Address (TTBR) register, Level 1
page table and Level 2 page table contain Physical addresses or
 Virtual addresses?
    TTBR: Contain physical address of the pgd base
    Level 1 page table (pgd): Physical address pointing to the pte base
    Level 2 page table (pte): Physical address pointing to the
physical page frame
    Since page tables are in kernel space and kernel virtual memory is
mapped directly to RAM. Using just an easy macro like
__virt_to_phys(), we can get the physical address for the pgd base or
pte base or pte entry.

Kernel Synchronization

1. Why do we need synchronization mechanisms in Linux kernel?
2. What are the different synchonization mechanisms present in Linux kernel?
3. What are the differences between spinlock and mutex?
4. What is lockdep?
5. Which synchronization mechanism is safe to use in interrupt context and why?
6. Explain about the implementation of spinlock in case of ARM architecture.
7. Explain about the implementation of mutex in case of ARM architecture.
8. Explain about the notifier chains.
9. Explain about RCU locks and when are they used?
11. Explain about RW spinlocks locks and when are they used?
12. Which are the synchronization technoques you use 'between
processes', 'between processe and interrupt' and 'between interrupts';
why     and how ?
13. What are the differences between semaphores and spinlocks?

Process Management and Process Scheduling

1. What are the different schedulers class present in the linux kernel?
2. How to create a new process?
3. What is the difference between fork( ) and vfork( )?
4. Which is the first task what is spawned in linux kernel?
5. What are the processes with PID 0 and PID 1?
    PID 0 - idle task
    PID 1 - init
6. How to extract task_struct of a particular process if the stack
pointer is given?
7. How does scheduler picks particular task?
8. When does scheduler picks a task?
9. How is timeout managed?
10. How does load balancing happens?
11. Explain about any scheduler class?
12. Explain about wait queues and how they implemented? Where and how
are they used?
13. What is process kernel stack and process user stack? What is the
size of each and how are they allocated?
14. Why do we need seperate kernel stack for each process?
15. What all happens during context switch?
16. What is thread_info? Why is it stored at the end of kernel stack?
17. What is the use of preempt_count variable?
18. What is the difference between interruptible and uninterruptible
task states?
19. How processes and threads are created? (from user level till kernel level)
20. How is virtual run time (vruntime) calculated?

Timers and Time Management

1. What are jiffies and HZ?
2. What is the initial value of jiffies when the system has started?
3. Explain about HR timers and normal timers?
4. On what hardware timers, does the HR timers are based on?
5. How to declare that a specific hardware timers is used for kernel
periodic timer interrupt used by the scheduler?
6. How software timers are implemented?

Power Management in Linux

1. Explain about cpuidle framework.
2. Explain about cpufreq framework.
3. Explain about clock framework.
4. Explain about regulator framework.
5. Explain about suspened and resume framwork.
6. Explain about early suspend and late resume.
7. Explain about wakelocks.

Linux Kernel Modules

1. How to make a module as loadable module?
2. How to make a module as in-built module?
3. Explain about Kconfig build system?
4. Explain about the init call mechanism.
5. What is the difference between early init and late init?
6. Early init:
7. Early init functions are called when only the boot processor is online.
8. Run before initializing SMP.
9. Only for built-in code, not modules.
10. Late init:
11. Late init functions are called _after_ all the CPUs are online
12. Linux Kernel Debugging

Linux Kernel Debugging

1. What is Oops and kernel panic?
2. Does all Oops result in kernel panic?
3. What are the tools that you have used for debugging the Linux kernel?
4. What are the log levels in printk?
5. Can printk's be used in interrupt context?
6. How to print a stack trace from a particular function?
7. What's the use of early_printk( )?
8. Explan about the various gdb commands.

Miscellaneous

1.How are the atomic functions implemented in case of ARM architecture?
2.How is container_of( ) macro implemented?
3.Explain about system call flow in case of ARM Linux.
4.What 's the use of __init and __exit macros?
5.How to ensure that init function of a partiuclar driver was called
before our driver's init function is called (assume that both these
 drivers are built into the kenrel image)?
6.What's a segementation fault and what are the scenarios in which
segmentation fault is triggered?
7.If the scenarios which triggers the segmentation fault has occurred,
how the kernel identifies it and what are the actions that the
kernel takes?


Question set :

1. What is the difference in features between kernel 2.2, 2.4 and 2.6 ?

2. What are Static and Shared libraries ?

3. What is dynamic linking ? What is static linking ?

4. What are the advantages of Dynamic linking or Shared libraries ?

5. Does gcc search for both static and shared libraries ? Which is
searched initially by gcc compiler ?

6. What should be done for Shared library based linking in gcc ?

7. What should be done for static library based linking in gcc ?

8. What is object file and what are symbols ?

9. Can you tell the memory layout based on Data,BSS,HEAP and STACK ?

10. What are the ways in which linux kernel can be compiled ?

11. How will get the driver added into the kernel ? What are Kconfig files ?

12. What is a kernel module ?

13. What is the difference between insmod and modprobe ?

14. How will you list the modules ?

15. How do you get the list of currently available drivers ?

16. How will you Access userspace memory from kernel ? What are the
various methods ?

17. What is the use of ioctl(inode,file,cmd,arg) ApI ?

18. What is the use of the poll(file, polltable) API ?

19. What is the use of file->private_data in a device driver structure ?

20. What is a device number ?

21. What are the two types of devices drivers from VFS point of view ?

22. What are character devices ?

23. How does the character device driver adds and remove itself from
the kernel ?

24. What is the role of interrupts in a device driver ? How are
interrupts handled in device driver ?

25. How will you make interrupt handlers as fast as possible ?

26. What are the types of softirqs ?

27. Difference between Timer Softirq and Tasklet Softirq ?

28. What are tasklets ? How are they activated ? when and How are they
initialized ?

29. What is task_struct and how are task states maintained ?

30. What is rwlock and spinlock ? Briefly explain about both of them ?

31. When will you use rwlock instead of spinlock ?

32. Can spinlock/rwlock be used in Interrupt handler ?

33. Tell about the Memory Layout of a Process in Linux .

34. How will you trace the system calls made into the kernel of lInux ?

35. What is mmap ? MMAP & malloc ? MMAP & brk ? MMAP adv & dis-adv.

36. Tell the relation between Malloc and MMAP

37. Advantages of MMAP over Read ?

38. Tell the role of brk() in malloc / Tell the relation between heap and brk?

39. Example of using MMAP and MUNMAP in C ?

40. Tell about the method/steps in Linux Kernel Compilation.

41. What is Kmalloc and how does it differ from normal malloc ? or Why
can’t we use malloc in kernel code ?

42. What happens as soon as a packet arrives from the network in Linux ?

43. What is a stack frame, stack pointer & frame pointer ?

44. What is a profiler ? Which one have you used ?

45. How do you determine the direction of stack growth ?

Question set :

1. user/kernel interface (system calls, procfs/sysfs, ioctl)

2. process vs interrupt context

3. deferred actions: softirq, tasklets, workqueues, timers

4. synchronization between contexts (how would you synchronize access
to a shared memory area used from an interrupt handler and a
workqueue on a SMP preemptive kernel).

5. memory allocation (kmalloc vs vmalloc)

6. debugging - tools and strategies for finding bugs.

7. are you familiar with the Linux kernel development process? Do you
have any patch accepted in the mainline?

On Wed, Jul 19, 2017 at 2:40 PM, Dinesh kumar chaudhary
<dineshece1035@gmail.com> wrote:
>
> How particular driver gets invoked when we connect any peripheral.
>
> Before device tree how the kernel used to invoke the specific drivers.
>
> If we have one address, how do we know whether it is in kernel space
> or in user space.
>
> How to check the kernel panic (how do we know where the program
> counter was there before kernel panic ).
>
> How I2c invokes in kernel space.
>
> Check the loop in the linked list.
>
> Check the given number whether it is multiple of 4 or not.
>
> Can we use spin lock in Mutex and vice-versa?
>
> Variants of spinlock.
>
> How to make an interrupt shared.
>
> Concurrent interrupt.
>
> Workqueue and differed function.



