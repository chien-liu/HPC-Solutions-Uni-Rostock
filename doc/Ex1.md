# HPC exercise 1
###### tags `uni-rostock` `HPC`

## Table of Contents
<!--ts-->
* [Task1.1](#t1)
* [Task1.2](#t2)
* [Task1.3](#t3)
* [Task1.4](#t4)
* [Task1.5](#t5)
<!--te-->

<a name="t1">
  
## Task 1.1 Systems share of supercomputer architectures 
**Question**

How are the architectures represented in the top group of high-performance computing systems?

**Answer**

<img src="https://expertiza.csc.ncsu.edu/images/0/0c/Architecture_Share1.png" width="300">

> source: [https://expertiza.csc.ncsu.edu/](https://expertiza.csc.ncsu.edu/index.php/CSC/ECE_506_Spring_2013/1a_pg)

As the image shows, recent types of supercomputer are [massively parallel processing (MPP)](https://en.wikipedia.org/wiki/Massively_parallel) and [cluster](https://en.wikipedia.org/wiki/Computer_cluster).

**Difference between MPP and cluster**

In a cluster, each machine is largely independent of the others in terms of memory, disk, etc. They are interconnected using some variation on normal networking. The cluster exists mostly in the mind of the programmer and how s/he chooses to distribute the work.

In a Massively Parallel Processor, there really is only one machine with thousands of CPUs tightly interconnected. MPPs have exotic memory architectures to allow extremely high speed exchange of intermediate results with neighboring processors.

The major variants are SIMD (Single Instruction, Multiple Data) and MIMD (Multiple Instruction, Multiple Data). In a SIMD system, every processor is executing the same instruction at the same time, only on different bits of memory. Essentially, there is only one Program Counter. In a MIMD machine, each CPU has it's own PC.

MPPs can be a bitch to program and are of use only on algorithms that are embarrassingly parallel (that's actually what they call it). However, if you have such a problem, then an MPP can be shockingly fast. They are also incredibly expensive.
> credit: [Peter Rowell, MatthewMartin](https://stackoverflow.com/questions/5570936/what-is-the-difference-between-a-cluster-and-mpp-supercomputer-architecture)

<a name="t2">
  
## Task 1.2: Performance measures for parallel work
**Question**

Name and explain the parameters for the performance gain through parallelization.

**Answer:**

For an parallel program, the speed up can can defined as:
<img src="https://render.githubusercontent.com/render/math?math=S_n = T_1 / T_n">
* <img src="https://render.githubusercontent.com/render/math?math=S_n">: Speed up
* <img src="https://render.githubusercontent.com/render/math?math=T_1">: Time consume using 1 processor
* <img src="https://render.githubusercontent.com/render/math?math=T_n">: Time consume using n processor

Theoritically <img src="https://render.githubusercontent.com/render/math?math=S_n < n">, and <img src="https://render.githubusercontent.com/render/math?math=S_n"> decays when <img src="https://render.githubusercontent.com/render/math?math=n"> goes higher. However, sometimes the effect of memory hierarchy makes <img src="https://render.githubusercontent.com/render/math?math=S_n > n"> in practice.

Effeciency: <img src="https://render.githubusercontent.com/render/math?math=E_n = S_n / n">

An ideal parallel program has its effencieny equal to 1.

Scalability: high efficiency even with large processor numbers
. Kind of like
<img src="https://render.githubusercontent.com/render/math?math=E_\infty">

<a name="t3">
  
## Task 1.3: Limits of scalability
**Question**

Name and explain the laws about the maximum achievable speedup.

**Answer**

Amdahl's law consider a fixed amount of work.
A task can be separated by sequential part s and parallel part p. The sequential part cannot be parallelized.

<img src="https://render.githubusercontent.com/render/math?math=0 < s < 1">

<img src="https://render.githubusercontent.com/render/math?math=s %2B p = 1">

With <img src="https://render.githubusercontent.com/render/math?math=n"> processors, the maximum of speed up is <img src="https://render.githubusercontent.com/render/math?math=S_{max} = \frac{1}{s %2B p/n}">. When <img src="https://render.githubusercontent.com/render/math?math=n"> approaches to infinity, <img src="https://render.githubusercontent.com/render/math?math=S_{max} = \frac{1}{s}">


Gustafson's law assume amount of works growth with systems size.

<img src="https://render.githubusercontent.com/render/math?math=S_{max} = s %2B pn">

<a name="t4">
  
## Task 1.4: Character constants in C
**Question**
What do you understand by character constants? Give the numeric values of the lower letters ‘a’, ‘b’,
and ‘z’ according to the ASCII table.

**Answer**

Characters are reprensented by integer numbers. The mapping is called ASCII TABLE, mapping numbers 0-255 to characters.
* 'a': 97
* 'b': 98
* 'z': 122
* 'A': 65

<a name="t5">
  
## Task 1.5: Escape sequences in C
**Question**

What do you understand by escape sequences? Give the numeric values of the escape sequences that
you got to know in the lecture according to the ASCII table.

**Answer**
Escape sequence is a sequence of characters that does not represent itself, but is translated into another character or a sequence of characters that my be difficult to represent directly. Examples are *newline*, *tab*, *backspace*, and *carriage return*.

|Symbol|Ascii (Hex.)|Description|
|:--:|--|--|
|\\t|0x09|Inserts a tab in the text at this point.|
|\\b|0x08|Inserts a backspace in the text at this point.|
|\\n|0x0A|Inserts a newline in the text at this point.|
|\\r|0x0D|Inserts a carriage return in the text at this point.|
|\\f|0x0C|Inserts a form feed in the text at this point. (It skips to the start of the next page.)|
|\\'|0x27|Inserts a single quote character in the text at this point.|
|\\"|0x22|Inserts a double quote character in the text at this point.|
| \\\ |0x5C|Inserts a double quote character in the text at this point.|


## Optional Task 1.6: Conversions in C
To be added
