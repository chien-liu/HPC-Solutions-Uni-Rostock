# HPC exercise 4
###### tags `uni-rostock` `HPC`

<a name="t1">
  
## Task 4.1: Introduction to operating systems
**Question**\
Give the definition of operating systems according to DIN 44300 and explain the duties of an operating systems.

**Answer**\
The programs of a digital computer system which, together with the properties of the computer system, form the basis of the possible operating modes of the digital computer system and, in particular, control and monitor the execution of programs.

<a name="t2">
  
# Task 4.2: Multiprogramming
**Question**\
What do you understand by multiprogramming?

**Answer**\
Multiprogramming is a computer running more than one program at a time. It's done by process scheduling which is handled by an operating system. The OS is constantly doing context switch, storing state of running process in PCB, and dispatches other process. ALthough, there's small overhead doing context switch, it is a way to hide (I/O) latency and utilize the computer more efficiently.

<a name="t3">

## Task 4.3: Virtual memory
**Question**\
A machine has a 32-bit byte-addressable virtual address space. The page size is 4 KB. How many pages of virtual address space exist?

**Answer**\
4 KB = <img src="https://render.githubusercontent.com/render/math?math=2^{12}">bit

<img src="https://render.githubusercontent.com/render/math?math=2^{32} / 2^{12} = 2^{20} = 1"> million

<a name="t4">

## Task 4.4: File systems
**Question**\
Compare the bit-map with the free-list methods for keeping track of free space on a disk with 800 cylinders, each one having 5 tracks of 32 sectors. How many holes would it take before the hole list would be larger than the bit map? Assume that the allocation unit is the sector and that a hole requires a 32-bit table entry.
