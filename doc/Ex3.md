# HPC exercise 3
###### tags `uni-rostock` `HPC`

## Table of Contents
<!-- ts -->

<!-- te -->

<a name="t1">

## Task 3.1: Parallel computers
**Question**\
Which categories of parallel computer architectures can be distinguished?

**Answer**\
Basically:
* SISD (Single instruction single data)
* SIMD (Single instruction multiple data)
* ~~MISD~~: Not used commercially
* MIMD (Multiple instruction multiple data)

<img alt="parallel computers" src="/image/task3-1.png" width="500">

> image source: [lecture keynotes](https://lsf.uni-rostock.de/qisserver/rds?state=verpublish&status=init&vmfile=no&publishid=125991&moduleCall=webInfo&publishConfFile=webInfo&publishSubDir=veranstaltung&idcol=k_semester.semid&idval=20202&getglobal=semester&htmlBodyOnly=true)

<a name="t2">

## Task 3.2: Parallel computers and OpenMP
**Question**\
Parallel computer architectures can be classified according to their communication model. Which communication model does the parallel programming model OpenMP belong to?

**Answer**\
OpenMP supports multi-threading with shared memory. OpenMP support both SIMD and MIMD.

<a name="t5">

## Task 3.5: OpenMP: loop parallelization
**Question**\
What do you have to consider when parallelizing loops? Which loops can/cannot be parallelized?

**Answer**\
In order for the compiler to successfully transform the sequential loop into a paralielloop, it must be able to verify that the run-time system will have the information it needs to determine the number of loop iterations when it evaluates the control clause. For this reason the control clause of the [or loop must have canonical shape. In addition, the for loop must not contain statements that allow the loop to be exited prematurely. Examples include the break statement, return statement, exit statement, and go to statement.
