# Page Fault

# Implement VM
## VM benefits
* isolation
* level of indirection
  * va -> pa (trampoline - allow kernel map one page into many adreess spaces, guard page - protect stack both in kernel and user spaces)

## info needed
* the faulting va
  * stval register <- va
* the type of page fault
  * scause: r/ w/ instruction
* the va of oinstruction that cause the page fault
  * sepc trap frame

# Features using page faults

## allocation: sbrk() -> eager allocation
applications tend to ask more

## lazy allocation
sbrk(): p -> sz = p -> sz + n
page fault: va < p below(<) p->sz >  va above stack 
allocate 1 page, zero the page, map the page, restart instruction

## cow fork (copy on write fork)
* shell: fork: parent & children(exec)
* page fault: copy page, map it, restore instruction, userret()

## demand paging
* exec(): load text, data, segment eagerly -> page table
* page fault: 
  * read block/page from file into memory
  * map mem into page table
  * restart instruction
* if out of memory:
  * evit(least recently used LRU) a page -> file
  * use the just free page
  * restart instruction
  * dirty memory(RW)

## memory mapped files
load/ store filess
mmapc va, len, plot, flags, offset