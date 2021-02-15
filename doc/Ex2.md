# HPC exercise 2
###### tags `uni-rostock` `HPC`

## Table of Content
<!-- ts -->
* [Task2-1](#t1)
* [Task2-2](#t2)
* [Task2-3](#t3)
* [Task2-4](#t4)
* [Task2-5](#t5)
* [Task2-7](#t7)
* [Task2-8](#t8)
* [Task2-10](#t10)
<!-- te -->

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

<img alt="MIC-1" src="https://upload.wikimedia.org/wikipedia/it/d/db/Mic-1.jpg" width="500">

> image source: [Wiki](https://it.wikipedia.org/wiki/MIC-1)

* B bus: connected to the output of the registers and to the input of the ALU.
* C bus: connected to the output of the shifter and to the input of the registers.

The B bus can be enabled by just one register at a time, since the transfer of data from 2 registers at the same time, would make this data inconsistent. Therefore, a 4-bit field is enough to represent.

In contrast, the C bus can be enabled by more than 1 register at the same time. Because of this reason, a complete bit map is specified for C bus.

<a name="t5">

## Task 2.5: Microarchitecture level: execution time
How long does a 2.5‐GHz Mic‐1 take to execute the following Java statement
```i = j + k;```
Make use of the following table excerpt of the Mic‐1’s microprogram

<img alt="table2-5" src="/image/table2-5.png" width="500">


<a name="t6">
  
## Task 2.6: Microarchitecture level: improving performance
**Question**

Why are computers equipped with multiple layers of cache? Would it not be better to simply have one big one?

**Answer**

In computer architecture, the memory hierarchy separates computer storage into a hierarchy based on response time. The one with smaller capacity and near to a processor has less response time. With a pipline algorithm and branch predictor, memory hierarchy outperforms a single big memory.

<a name="t7">

## Optional Task 2.7: ISA level: compiling Java to IJVM code

**Question**

Give two different IJVM translations for the following Java statement:

```i = k + n + 5; ```

**Answer**

(method 1)\
ILOAD k\
ILOAD n\
IADD\
BIPUSH 5\
IADD\
ISTORE i

(method 2)\
ILOAD k\
BIPUSH 5\
IADD\
ILOAD n\
IADD\
ISTORE i

<a name="t8">

## Optional Task 2.8: ISA level: IJVM code and Java
**Question**

Give the Java statement that produced the following IJVM code:\
ILOAD j\
ILOAD n\
ISUB\
BIPUSH 7\
ISUB\
DUP\
IADD\
ISTORE i\

> Note:
> ISUB: Pop two words from stack; subtract the second to top word from top word, push the answer.
> DUP: Copy top word on stack and push onto stack.

```i = 2 * (7 - (n - j));```

<a name="t10">

## Task 2.10: Assembly language level: execution time
**Question**

For a certain program, 2% of the code accounts for 50% of the execution time. Compare the following three strategies with respect to programming time and execution time. Assume that it would take 100 months to write it in C, and that assembly code is 10 times slower to write and four times more efficient.
1. Entire program in C.
2. Entire program in assembler.
3. First all in C, then the key 2% rewritten in assembler.

**Answer**

Assume when using c, programming time p, executing time e.

(1)Entire program in C\
p + e

(2) Entire program in assembler\
10p + e/4

(3) First all in C, then the key 2% rewritten in assembler\
0.98p + 0.2p + 0.5e + 0.125e\
= 1.18p + 0.625e

> Note: Human's time is more valuable than machine's time :smirk:
