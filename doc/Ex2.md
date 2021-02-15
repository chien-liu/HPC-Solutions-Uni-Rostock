# HPC exercise 2
###### tags `uni-rostock` `HPC`

<a name="t1">

## Task 2.1: Structured computer organization: data path speed
**Question**

Consider the operation of a von Neumann machine with the data path you got to know in the lecture. Suppose that loading the ALU input registers takes 5 nsec, running the ALU takes 10 nsec, and storing the result back in the output register takes 5 nsec. What is the maximum number of MIPS this machine is capable of in the absence of pipelining?

<a name="t2">

## Task 2.2: Basics of computer systems: little‐	and big‐endian memory
**Question**

A word on a little‐endian computer with 32‐bit words has the numerical value of 3. If it is transmitted to a big‐endian computer byte by byte and store there, with byte 0 in byte 0, and so on, what is its numerical value on the big‐endian machine?

**Answer**

Range of a 32-bit (4 bytes) word: 0x00000000 - 0xFFFFFFFF

3 = 0x00000003
The table belows shows the representation of 3 in big/little endian.
|Endian|memory a| a+1 | a+2 | a+3 |
|--|:--:|--|--|--|
|Big endian| 00 | 00 | 00 | 03 |
|Little endian| 03 | 00 | 00 | 00 |

Therefore, the value will become <img src="https://render.githubusercontent.com/render/math?math=3 \times 2^6">


<a name="t3">

## Task 2.3: Microarchitecture level: instruction execution
**Question**

What are the four steps CPUs use to execute instructions?

**Answer**

1. Fetch : get the instruction from memory into the processor.
2. Decode : internally decode what it has to do (in this case add).
3. Execute : take the values from the registers, actually add them together
4. Store : store the result back into another register. You might also see the term retiring the instruction.

<a name="t4">

## Task 2.4: Microarchitecture level: control section
**Question**

Remember the block diagram of the microinstruction control Mic‐1 from the lecture. The B bus register is encoded in a 4‐bit field, but the C bus is represented as a bit map. Why?

**Answer**
