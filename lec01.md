# OS purposes 
* abstract the hardware
* multiplex
* isolation
* sharing
* security
* performance
* range of uses

# OS organization
* user space: vi, c compiler, shell
* kernal(matain data): file system: 
    * manages processes, allocation of memory, access contorl(security)
* bottom: CPU, RAM, disk, network interface

## API kernal
fd -- file descriptor = open("out", 1)
write(fd, "hello\n", 6)

# Why hard/ interesting
* unforgiving
* tensions
  * efficient - abstract
  * powerful - simple
  * flexible - secure
* interaction
  * fd = open
  * pid = fork()

# 
* os: xv6
* run on risc-v
* actually run under QEMU, run xv6 without hardware




