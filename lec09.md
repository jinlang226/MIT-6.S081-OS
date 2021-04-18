# interrupts
* hardware wants attention now
* software 
  * save its work 
  * process interrupt
  * resume its work
1. asynchronous
2. concurrency (operating parellal)
3. programm device

# driver manages device
uart.c

top: read/ write
bottom: interrupt handler

# programming device
* memory mapped i/o -- ld/st
* ld/ st -- read/ write control register of the device

# case study: $ls
* $:
  * device put $ into uart
  * uart generate intterrupt when the char has been sent
* ls:
  * keyboart connect to the recieve line
  * generate interrupt
  
# RISC-V support for interrupts
* SIE: one bit for external, software, time intterupt
* SSTATUS: bit enable/ disable interrupts
* SIP: interrupt pending register
* SCAVSE: 
* STVEC: trap/ page fault/ interrupt?

# interrupt (hw)
* if SIE bit set: 
  * clear SIE bit
  * sepc <- pc
  * save current mode
  * mode <- supervisor
  * pc <- stvec
  * -> user space

# interrupt and concurrency
1. device + CU run in parrallel, producer/consumer parralelism
2. interrupt stops the current program is running, interrupt enable/disable
3. top of the driver, and the bottom of the driver may run in parrallel.

# producer/consumer
   
# interrupt evolution
* interrupt used to be fast
* simple
* now slow, device is more complicated  

# polling: fast device instruction