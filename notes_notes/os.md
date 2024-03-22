## os 


- manages hw
- intermediary between user and kernel and basis for application software
- allocation of resources
- security and memory
- convienience and efficiency


## the diagram


- apps / user
- os
- user


## os types


- batch
- time sharing
- multi programming
- processing and multitasking


## modern pcs


- one or more cpus
- device controllers connected through bus
- to give access to shared memory
- disk controllers usb controllers and video adapters
- memory controller will synchronize access to the memory


## important terms


- bootstrap program
- stored in rom
- load it onto os kernel
- interrupt
- occurence of an event
- does it through system bus
- systemcall
- software triggers an interrupt



## what happens in interrpted


- stops and transfers execution to a fixed location
- service routine executes
- isr ka starting address
- on completion it continues



## storage structures


- registers
- cache
- volatile
- main m
- disk
- n-volatile
- nv-ram 
- battery backup 


## io structure


- device controller
- device driver
- uniform interface with device and rest of the operating system
- local buffer storage
- general purpose registers


## io operations


- loads the registers ( driver )
- checks what to do ( controller )
- data device to local buffer
- controller that operation is finished via interrupt
- drive will return control to os
- high overhead for bulk movement ( dma ) ( buffer to memory directly ) ( interrupt per block )


## categorization


- single processor ( 1 gp processor ) ( maybe lot of special purpose processor )
- multi processor ( parallel system sharing bus or clock )
- thrughput
- economy
- reliability
- symmetric ( equal )
- assymetric ( master slave )
- clustered system ( two or more system coupled together )
- availability
- assymetric ( hot standby )
- symmetric ( all monitor another )


## common capabilities

- multiprogrammign 
- one task will keep busy
- organise tasks so that there is always a task to run
- efficient system
- eg: lawyer
- multitasking ( time sharing ) ( round robin )
- switches betwenn jobs 
- user can interact
- direct com between user and system
- def process


## os services

- interface
- program execution
- io operations
- file system management
- communications ( between processes )
- error detection
- resource allocation
- accounting ( usage statistics )
- protection and security


## os interface

- command line interface ( remember the commands ) 
- command interpreter shell
- graphical user interface


## systemcalls

- interface to the services made available by the operating system
- kernel mode ( previledge ) 0 
- when you need to do something do the context switch by doing a call to the system
- routies written in c and c++
- user mode 1

## structure of os

- ms-dos ( simple )
- monolithic 
- user
- commands
- kernel ( everything ) ( difficult to implement and maintain )
- layered structure ( all circles ) ( may want to arrange properly ) ( might be slow )
- microkernel   
- only base functionalities and remaining is implemented as user program
- user mode 
- message passing
- modules 
- as when required
- message passing not there


## virtual memory

- abstract the hardware into several into several different execution units 
- illusion of sepatate execution
- software runs in kernel mode
- vm runs on usermode
- virtual usermode and virtual kernel mode
- minidisk and sharing


## boot 

- the process of starting a comp by loading a kernel
- bootstrap program
- cant be effected by virus
- firmware


## processes and threads

- threads is a unit of execution within a process 
- consist ofthread_id, pc, register_set, stack, state
- multithreadingmore than one task at a time 
- benefits
- responsiveness
- resource sharing
- utilization of multiprocessor atchi


## process state

- state = current activity
- new ( being created )
- ready ( ready to be assigned )
- waiting  ( waiting for some event to occur )
- running ( being executed )
- terminated ( finished exec )
- vagina diagram 


## process control block

- to represent a process we use a pcb
- proc id ( pid )
- proc state
- prog count
- cpu reg
- cpu sched info 
- mem lim
- accounting info
- io status


## process scheduling

- process scheduler
- job queue
- ready queue
- see the diagram


## context switch

- stop the current task and run a kernel routine ( save the current context )
- state save and state restore ( also called as context switch )
- pure overhead


## operation of processes

- creating = parent
- new = children
- fork()sepatate duplicate process ( different id ) n form 2^n pid
- exec()replace the entire process 
- init is the parent for all
- possibilities
- concurrently ( parent and child )
- wait for some or all child to terminate
- address space 
- child is dipli of parent
- new program
- termination ( exit() )
- normal termination
- returns a int to parent's wait()
- everything is deallocated
- one can cause other via syscall ( usually only by the parent )
- exceeded usage
- task is no longer required
- parent terminates ( orphan process ( init is parent ) )


## interprocess communication

- independant process ( effect other process )
- cooperating process ( can't )
- information sharing
- computation speed up
- modularity
- convenience
- shared memory ( address space of the process creating the sm )
- must attach to their address space
- normally this cant happen accessing mem
- but 2 or more mem can agree to remove the restriction
- message passing
- useful in dist systems ( present on different network )
- direct symsend(p, message) <sub>receive(q</sub> message)
- asssymsend(p, message) <sub>receive(id</sub> message)
- limited modularity ( id is changes then problem )
- indirect, mailbox, port ( like a buffer ) send(a, message) receive(a, message) ( owned by os or process )
- when dilemma allow at most one process to receive()
- select which one will receive the msg ( like an algo )
- fixed size ( sys easy prog diff )
- variable size ( sys diff prog easy )


## blocking or non-blocking

- blocking ( blocking send )  ( blocking receive )
- non-blocking ( non-blocking send ) ( non-blocking receive valid message or null )
- buffering
- 0 capacity ( blocking shit )
- bounded capacity ( block if full )
- unbounded capacity ( never block )


## producer consumer problem

- buffer os items
- must be synchronized
- no buffer
- unbounded buffer
- bounded buffer


## cpu scheduling algos

- decission when 
- running to waiting
- running to ready
- waiting to ready
- when process terminates



## dispatcher

- gives control of the cpu to the process selected by the cpu scheduler ( dispatch latency )


## scheduling criteria

- cpu utilization ( 40-90 )
- throughput ( n / t )
- turn around time ( see notes )
- waiting time ( see notes )
- response time ( see notes )


## process sync

- data inconsistency
- producer-consumer
- counter
- shared data critical sec
- must request entry
- implementing the request ( entry )
- followed by an exit section
- remainder section
- must satisfy
- mutual exclusion
- progress
- bounded waiting


## peterson's sol

- for iflag[i], turn j, while(j), flag[i]
- for j change


## test and set lock

- lock 1 || 0 


## semaphores

- semaphore = simple integer value
- wait(), signal(), s = number of possible simul connections
- this must be sunchronized
- binary semaphores = mutex locks on some systems
- counting sema
- diadvantage
- busy waiting ( stuck in while loop ) ( spinlock )
- block() instead of waiting, waiting queue
- can cause deadlock and starvation 2 are waiting for [eachother]


## classic problem with sync

- bounded buffer
- sol producer wait(empty), wait(mutex), add data to buffer,  signal(mutex), signal(full)
- sol consumerwait(full), wait(mutex), remove data, signal(mutex), signal(empty)
- reader-writer 2 sema and integer
- writerwait(write) signal(write)
- readerwait(mutex), read++, cond, wait(write), signal(mutex), wait(mutex), read--, cond, signal(write), signal(mutex)
- dining-philthink, eat
- wait i wait (i+1)%size
- can still result in deadlock when all are hungry
- only 4 to sit simultaneously
- pick up only if both are avaible
- ass solution odd left and right, even right and left


## deadlocks

- no progress
- mutual exclusion
- no preemption
- circular wait
- hold and wait


## ignore, prevention, avoidance, detection and recovery

- ignore ( restart )
- prevent make atleast 1 cond false, 
- mutual exclusion false printer not possible
- preemption true ( time quantum method )
- try to do no hold and wait ( give all resource before it starts )
- circular wait ( give the numbering )


## basic hardware

- base register
- limit register
- base + limit to make physical address of not valid then trap


## address binding

- address = variable (symbolic)
- compiler binds variables -> relocatable
- linker binds relocatable -> absolute
- compile timephycical address while compiling
- load timerelocatable code and binds while loading
- execution timebinding while executing


## logical address and physical address

- mmu
- base reg = relocation reg


## dynamic loading

- routine is not loaded until it's called
- relocatable linking loader
- less mem req


## dynamic loading shared libraries

- staticcombined the loader into binary program image
- stub
- no need to recompile after updating
- less memory requirement


## swapping

- temp swapped into backing store
- never swap a process with pending io
- exec io op into os buffer


## memory allocation methods

- merge
- split
- first fit ex frag
- best fit ex frag
- worst fit
- 50 percent rule
- sol compaction but no comp on load time or compile time


## segmentation

- segment_table, offset
- based on this code, global_variables, heap, stacks, standard_c_library
- seg hardware
- seg table segbase, seglimit


## paging

- avoids ext frag and need for compa
- page table pageno, frameno

### hardware support

- set of dedicated reg if small
- page table base register but slow bcz 2 mem access
- translation look aside buffer pageno, frameno
- effective memory access time (hit_ratio*time+miss_ratio*time)

### protection

- valid_invalid bit allow or disallow access to page

### shared pages

- reduces memory cons


## structure of page table 

- hierarchical paging
- outer page table, inner page table, frame
- hashed page table virt_pgno, frame_no, pointer to next
- inverted page table skip


## virtual memory management

### demand paging

- lazy pager

### handling page fault

- internal table for valid or invalid
- invalid terminate, valid use of not in mem bring to mem
- find a free frame
- disk operation
- modify internal table
- restart the instruction

### copy on write

- zero fill on demand while allocating empty pages
- vfork() caution

### page replacement algos

- modify or dirty bit when writing a page instead of writing whenever you change
- fifo page fault may increase or may decrease depending on the algo belady
- optimal replace the page that will not be used for a longest time
- least recently used which was either replaced recently or had a page hit only remaining you replace


## file concept

### file attributes

- name, identifier, type, location, protection, time date and user identification nitlspti encoding and checksum

### file operations

- create, writing, reading, moving, deleting, truncating

### general

- per process table 
- systemwide table
- opencount how many processes opened a table
- things ass with an open file file pointer, fileopen count, disk location, access rights
- shared lock ,exclusive lock
- mandatory and advisory file (explicitly aquire a lock) locking mechanisms

### access methods

- sequential access tape model
- direct access disk model databases

### storage structures

- tmpfs
- objfs
- ctfs
- lofs
- procfs
- ufs, zfs

### directory overview

- search, create, list, rename, traverse
- single level
- two-level
- tree structured no sharing
- acyclic graph sharing

### file sharing

- remote file sharing
- client-server model
- distributed information systems
- failure modes

### consistency semantics

- unix semantics: (write is visible immediately, share file via pointer; single image)
- session semantics: (not visible immediately, once closed; later sessions will see it)
- immutable  shared files semantics: (cannot be modified)
- andrew file system


## implementing file systems

- disk has 2 func
- rewritten in place
- directly access any block of information it contains
- boot control block
- volume control block
- file descriptor

### vfs

- use oop techniques
- file system interface
- virtual file system: (clean vfs interface, uniquely representing the files throughtout the net)
- inode, file, superblock, dentry objects

### directory impl

- linear lists
- hash table

### allocation methods

- contiguous
- linked list
- indexed: (linked, multilevel, combined:15,1,1,1)

### freespace managemenet

- bit vector
- linked list
- grouping 
- counting


## mass storage structures

- constant linear velocity
- constant angular velocity

### disk attachment

- host attached: (fibre channel, 4 conductor copper cable, large switched fabric, arbitrated loop)
- network attached: (nfs, rpc)
- storage area network: ()

### disk scheduling

- fcfs
- sstf
- look and clook
- scan and cscan


## protection

- principle of least proviledge
- domain of protection
- need to know principle
- example unit and multics(seg desc, 3 bits)

### implementation of access matrix

- global table
- access lists
- capability lists
- lock and key mechanism

