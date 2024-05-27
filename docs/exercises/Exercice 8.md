# Exercises sheet 8


**1. Explain in your own words why abstractions are necessary.**
+ They make programming simpler. Without them, user level program will have to understand the logic of every piece of hardware they may have to interact with.
+ Abstractions also allow separation of concerns, presenting an interface that hides away the logic of the "object" being abstracted.
+ Abstractions also help with portability, as long as the same interface is presented to software building upon it, the underlying implementation/hardware should not matter.

  
**2. Explain what piece of hardware thread, address space and files help to abstract.**
+ Thread: CPU, address space: RAM, files: disk.



**3. Processes are not tied to a specific piece of hardware. What is their role?**
+ They encapsulate other abstractions necessary for the execution of a task (i.e. thread, address space and files)


**4. What is a page fault?**
+ Page faults occur when the virtual-physical address translation is not available in the TLB.


**5. Complete the table by using followings:**
a. FIFO replacement policy


| Num    | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 |
|--------|---|---|---|---|---|---|---|---|---|----|----|----|
| Ref    | a | b | c | a | b | e | d | a | e | d  | b  | d  |
| PP1    | a | a | a | a | a | e | e | e | e | e  | b  | b  |
| PP2    |   | b | b | b | b | b | d | d | d | d  | d  | d  |
| PP3    |   |   | c | c | c | c | c | a | a | a  | a  | a  |
| Fault? | * | * | * |   |   | * | * | * |   |    | *  |    |

b. MIN replacement policy

| Num    | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 |
|--------|---|---|---|---|---|---|---|---|---|----|----|----|
| Ref    | a | b | c | a | b | e | d | a | e | d  | b  | d  |
| PP1    | a | a | a | a | a | a | a | a | a | a  | b  | b  |
| PP2    |   | b | b | b | b | b | d | d | d | d  | d  | d  |
| PP3    |   |   | c | c | c | e | e | e | e | e  | e  | e  |
| Fault? | * | * | * |   |   | * | * |   |   |    | *  |    |

c. LRU replacement policy

| Num    | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 |
|--------|---|---|---|---|---|---|---|---|---|----|----|----|
| Ref    | a | b | c | a | b | e | d | a | e | d  | b  | d  |
| PP1    | a | a | a | a | a | a | d | d | d | d  | d  | d  |
| PP2    |   | b | b | b | b | b | b | a | a | a  | b  | b  |
| PP3    |   |   | c | c | c | e | e | e | e | e  | e  | e  |
| Fault? | * | * | * |   |   | * | * | * |   |    | *  |    |

d.Clock Policy


| Num    | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 |
|--------|---|---|---|---|---|---|---|---|---|----|----|----|
| Ref    | a | b | c | a | b | e | d | a | e | d  | b  | d  |
| PP1    | a | a | a | a | a | e | e | e | e | e  | b  | b  |
| PP2    |   | b | b | b | b | b | d | d | d | d  | d  | d  |
| PP3    |   |   | c | c | c | c | c | a | a | a  | a  | a  |
| Fault? | * | * | * |   |   | * | * | * |   |    | *  |    |


**6. Complete the following table using:**
a. FIFO replacement policy
| Num    | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 |
|--------|---|---|---|---|---|---|---|---|---|----|----|----|
| Ref    | a | b | c | e | b | d | b | f | e | f  | b  |  d | 
| PP1    | a | a | a | e | e | e | e | f | f | f  | f  | f  |
| PP2    |   | b | b | b | b | d | d | d | e | e  | e  | e  |
| PP3    |   |   | c | c | c | c | b | b | b | b  | b  | d  |
| Fault? | * | * | * | * |   | * | * | * | * |    |    | *  |



b. Clock replacement policy

| Num    | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 |
|--------|---|---|---|---|---|---|---|---|---|----|----|----|
| Ref    | a | b | c | e | b | d | b | f | e | f  |  b |  d | 
| PP1    | a | a | a | e | e | e | e | f | f | f  |  f | d  |
| PP2    |   | b | b | b | b | b | b | b | e | e  |  e | e  |
| PP3    |   |   | c | c | c | d | d | d | d | d  |  b | b  |
| Fault? | * | * | * | * |   | * |   | * | * |    | *  | *  |
| Victim |V=1|V=1|V=1|V=2|V=2|V=1|V=1|V=2|V=3|V=3 | V=1| V=2|
|        |   |   |   |   |V=3|   |   |   |   |    |    |    |

  
