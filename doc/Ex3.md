# HPC exercise 3
###### tags `uni-rostock` `HPC`

## Table of Contents
<!-- ts -->
* [Task3.1](#t1)
* [Task3.2](#t2)
* [Task3.3](#t3)
* [Task3.4](#t4)
* [Task3.5](#t5)
* [Task3.7](#t7)
* [Task3.8](#t8)
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

<a name="t3">
  
## Task 3.3: OpenMP: parallel regions 
**Question**\
What do you understand by parallel regions? Explain how they work in OpenMP.

**Answer**\
An OpenMP program has sections that are sequential and sections that are parallel. In general an OpenMP program starts with a sequential section in which it sets up the environment, initializes the variables, and so on.When run, an OpenMP program will use one thread (in the sequential sections), and several threads (in the parallel sections).There is one thread that runs from the beginning to the end, and it's called the master thread. The parallel sections of the program will cause additional threads to fork. These are called the slave threads.A section of code that is to be executed in parallel is marked by a special directive (omp pragma). When the execution reaches a parallel section (marked by omp pragma), this directive will cause slave threads to form. Each thread executes the parallel section of the code independently. When a thread finishes, it joins the master. When all threads finish, the master continues with code following the parallel section.

<a name="t4">
  
## Task 3.4: OpenMP: work sharing
**Question**\
What do you understand by work sharing? Explain how it works in OpenMP.

**Answer**\
A worksharing construct distributes the execution of the corresponding region among the members of the team that encounters it. Threads execute portions of the region in the context of the implicit tasks that each one is executing. If the team consists of only one thread then the worksharing region is not executed in parallel.\
A worksharing region has no barrier on entry; however, an implied barrier exists at the end of the worksharing region, unless a nowait clause is specified. If a nowait clause is present, an implementation may omit the barrier at the end of the worksharing region. In this case, threads that finish early may proceed straight to the instructions that follow the worksharing region without waiting for the other members of the team to finish the worksharing region, and without performing a flush operation.


<a name="t5">

## Task 3.5: OpenMP: loop parallelization
**Question**\
What do you have to consider when parallelizing loops? Which loops can/cannot be parallelized?

**Answer**\
In order for the compiler to successfully transform the sequential loop into a paralielloop, it must be able to verify that the run-time system will have the information it needs to determine the number of loop iterations when it evaluates the control clause. For this reason the control clause of the for loop must have canonical shape. In addition, the for loop must not contain statements that allow the loop to be exited prematurely. Examples include the break statement, return statement, exit statement, and go to statement.

<a name="t7">

## Task 3.7: OpenMP: loop dependences
**Question**\
What do you understand by loop dependences? Give examples how to detect them.

**Answer**\
(1)Loop-independent dependences
```C++
do i = 1,100
  A(i) = B(i)+1
  C(i) = A(i)*2   // Dependences within the same loop iteration
enddo
```

(2)Loop-carried dependences
```C++
do i = 1,100
  A(i) = B(i)+1
  C(i) = A(i-1)*2   // Dependences that cross loop iterations
enddo
```

<a name="t8">

## Task 3.8: OpenMP: data dependences
**Question**\
What do you understand by data dependences? Which types of data dependences do you know? Give examples for data dependences.

**Answer**\
Data Dependence
* True (flow) dependence: s1 writes memory that s2 later reads
* Anti-dependence: s1 reads memory that s2 later writes
* Output dependences: s1 writes memory that s2 later writes
* Input dependences: s1 reads memory that s2 later reads

