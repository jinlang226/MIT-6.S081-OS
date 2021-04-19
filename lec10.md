# locks
app wants to multiple cares
kernel must handle parallel system calls
access shared data structures in parallel
-> locks for correct sharing
-> locks can limit performance

# why locks 
avoid race conditions

# lock abstraction
* struct lock: have field, mintain state of the lock
  * acquire lock: one process can acquire lock s
  * critical section: all executed all togetgher or none
  * release lock struct
* programs have many locks -> more parallelisms
* lock limit paralellism and performace

# when lock
* constitutive rule: 2 processes access a shared data structure.
* one is write -> lock data structure
* too strict: lock free programming -> better performance and parallel
* to loose: use lock on printf(".....") atomatically

# could locking be atomic
* every struct has a lock -> too rigid
* rename

# lock perspective
1. locks help avoid lost updates
2. make multi step operation atomic
3. help maintain invariant
   
# deadlock
* acquire a lock in critical section, and in critial section acure the same lock

| CPU1 | CPU2 |
| ------ | ------ |
| rename("d1/x", "d2/y") | rename("d1/x", "d2/y") |
| acquire d1 | acquire d2 |
| acquire d2 | acquire d1 |

* deadlock
* soln: order locks, acquire locks in order

# locks v.s. modularity
* the ordering in one lock set is global
* the ordering the other lock set is independent of the other ordering

# lock v.s. performance
* need to split up data structures
  * best split is a challenge
  * may need to rewrite to code too
  * lot of work
* method:
  1. start with coarse-grained 粗纹理的 locks
  2. measure

# broken acquire
wrong:
```
while(1) {
    if(l->locked = 0) {
        l->locked = 1; //两个cpu可能同时set 1
        return;
    }
}
```

# hardware test and set support
atomic memory operation swap
lock address
temp <- *addr
*addr <- r1
r2 <- tmp
unlock

# memory ordering
locked <- 1
x <- x + 1
locked <- 0

# summary 
* good for correctness
* bad for performance
* complicate programming
* dont share if you dont have to
* start with lease, race detector