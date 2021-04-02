# strawman design - no OS

enforced multiplexing
memory isolation

# unix interface 
abstracts the hardware resources 
provide strong isolations

e.g. 
**process** (created by fork) cannot interact with CPU. abstract CPU
**exec** provide memory unit, abstract memory
**file** how to map file with disk blocks


# OS should be defensive
* app cannot crash the OS
* app should not break out of isolation
* ==> strong isolation between apps and OS
* typical: hard ware support
  * user kernal mode 
  * virtual memory

# User/ Kernal mode
* User mode: CPU execute unpriviledged instruction: add, sub, jr
* Kernal: mode: privileged instruction: set up a page table (maniuplate the statez)
* bit that change the mode: privileged

# CPU provide virtual memory
* page table: virtual adress to physical address
* process its own page table
* strong memory isolation
* e.g.
  * user: ls/ echo (adress from 0 to 2^n)
  * kernal mode: kernal
* user entering kernal: ecall + sys call# 

# kernal = trusted computing base
* must have no bug
* must treat processes as malicious
* **monolithic** kernal design: bug++
* tight integration => performance 

# micro kernal design
* small: fewer bugs
* performance: jump back and out & share?

# kernal
pro.c --gcc--> pro.s --assembler--> pro.o --load--> kernal