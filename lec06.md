# isolation and syscall exit

# supervisor
* read/write control register
  * stap
  * stvec
  * sepc
  * sscratch
* use PTEs w/o PTE_U(user can use it)
  
# shell
* write
* ecall -> user vec(in kernal)
  * -> uservec - trapoliwe
  * -> usertrap()
  * -> syscall() -> usertrampoline() -> userset() -> ecall
  * -> sys_write()


