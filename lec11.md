# threads
one serial execution
program counter(pc), registers, stack

# interleave
* multi-core
* switch
  
# shared memory?
*  xv6 kernel thread - yes
*  user processes - no
*  linux user - yes
  
# thread challenges
* switching - interleave
  * scheduling
* what to save/ restore
* compute - boundarys

# timer interrupts
* kernel handler
  * yields - switch
* pre-emptiue schedule(voluntary)
* state
  * running - CPU
  * runnable - save pc, regs
  * sleeping
 