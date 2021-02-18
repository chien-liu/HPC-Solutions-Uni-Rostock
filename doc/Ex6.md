# HPC exercise 6
###### tags `uni-rostock` `HPC`

## Table of Contents
<!-- ts -->
* [Task6.1](#t1)
* [Task6.2](#t2)
* [Task6.3](#t3)
* [Task6.4](#t4)
* [Task6.5](#t5)
* [Task6.6](#t6)
<!-- te -->

<a name="t1">

## Task 6.1: Distributed systems: resource sharing
**Question**\
Give five types of hardware resource and five types of data or software resource that can usefully be shared. Give examples of their sharing as it occurs in distributed systems.

**Answer**\
Examples of hardware resources that can be usefully be shared, and examples of their sharing:
1. network\
capacity transmission of data packet transmission is done using the same circuit, this means, many communication channels share the same underlying circuit.
2. screen\
network window systems XWindows  allow processes in remote computers to update the content of the local windows
3. disk\
file server, virtual disk server
4. memory\
cache server
5. CPU\
servers do some computation for their clients, hence their cpu is a shared resource

Examples of data/software resources that can be shared in a distributed system
1. object\
there are unlimited possibilities to share objects in distributed systems, for example shared whiteboard, ticket booking, etc
2. file\
file servers enable multiple clients to have read/write access to the same files
3. webpage\
web servers enable client programs to have read-only access to the page content
4. database\
the content of a database can be usefully shared. There are many
techniques that control the concurrent access to a database.
5. exclusive lock\
 a system-level object provided by a lock server, enabling the coordination of accessing a special resource

<a name="t2">

## Task 6.2: Distributed systems: clock synchronization
**Question**\
How might the clocks in two computers that are linked by a local network be synchronized without reference to an external time source? What factors limit the accuracy of the procedure you have described? How could the clocks in a large number of computers connected by the Internet be synchronized? Discuss the accuracy of that procedure.

**Answer**\
One of the time synchronization protocols is **Christian's protocol**. The round trip time t to send a message and a reply between computers A and B is measured by repeated tests; then computer A sends its clock reading T to B. B sets it clock to (T + t/2). The setting can be refined by repetition. The procedure is subject to inaccuracy because of contention for the use of the local network from other computers and delays in the processing the messages in the operating systems of A and B. For a large number of computers, one computer should be nominated to act as the time server and it should carry out Christian's protocol with all of them. The protocol can be initiated by each in turn. Additional inaccuracies arise in the internet because messages are delayed as they pass through switches in wide area networks.

<a name="t3">

## Task 6.3: Distributed systems: implementation strategies
**Question**\
Consider the implementation strategies for massively multiplayer online. In particular, what advantages do you see in adopting a single server approach for representing the state of the multiplayer game? What problems can you identify and how might they be resolved?

**Answer**\
Technically there is no significant difference in the workings of cloud and client applications on the server. Client sends request data or applications from the server, and the server will respond with running applications and send data to the client. The novelty is in the handling of the server. In the traditional client server, the server must be configured and managed, could be in the application server or the client, the client must know where the application data should be stored. While the cloud eliminates the hassles of managing servers, clients simply have to connect to the cloud via the Internet, the cloud will be managing his own where he will store applications and data, making backups, and others, the client does not need to know.\
There are two types of MMO games. There are real-time games that have high interaction between user like Rising Force and Dota 2, and there are games that do not require high interaction between the user and the nature turn and wait like Pokopang and Ninja Saga. Two game genre requires two different architectures.\
For games like Farmville standard architecture of the server is sufficient, because the gameplay is personal to each user does not need to be real-time interaction between users directly so low that bandwidth capacity is not too inedible. Games that require real-time interaction between hundreds or thousands of users need to have multiple servers because of the gameplay requires a lot of users directly involved in it, so there needs to be multiple servers to menshare bandwidth.

<a name="t4">

## Task 6.4: Distributed systems: cloud computing
**Question**\
Compare and contrast cloud computing with more traditional client-server computing. What is novel about cloud computing as a concept?

**Answer**
Cloud computing is a general for anything that includes delivering hosted services over the internet. Merely, it is taking services/moving them outside of the firms firewall. It is a excellent way to transmit enterprise applications.\
Client server computing: server takes requests from the client computers and shares its resources, applications and or data with one or more client computers on the network.

What is cloud computing?\
Cloud computing is the practice of storing and accessing data and programs over the Internet instead of your computer'shard drive.Cloud computing is a model for enabling ubiquitous, convenient, on-demand network access to a shared pool of configurable computing resources (e.g., networks, servers, storage, applications and services) that can be rapidly provisioned and released with minimal management effort.Cloud computing has become a highly demanded service or utility due to the advantages of high computing power, cheap cost of services, high performance, scalability, accessibility as well as availability.\
Client machine usually manages the front-end processes such as GUIs (Graphical User Interfaces), dispatch requests to server programs, validate data entered by the user and also manages the local resources that the user interacts with such as the monitor, keyboard, workstation, CPU and other peripherals. On the other hand, the server fulfills the client request by performing the service requested.\
Disadvantage of cloud computing is that it requires constant internet access.

The client–server model of computing is a distributed application structure that partitions tasks or workloads between the providers of a resource or service, called servers, and service requesters, called clients. Often clients and servers communicate over a computer network on separate hardware, but both client and server may reside in the same system. 

Difference between cloud computing and client server computing:
Cloud computing is a kind of environment where our software/hardware can be hosted.
1. In cloud computing we can host ‘N’ number client server kind of applications. 
2. In client server computing the server is usually local. The employees access it over a private network. It is owned and operated by the employer and used exclusively by the employees
3. Cloud computing is the server accessed through the internet. The servers are owned by big companies like Google that run applications and many start-ups that provide data storage.
4. Cloud computing is not locally managed while client server computing is locally managed.
5. In client server computing, infrastructure is on site. This is not the case with cloud computing.

<a name="t5">

## Task 6.5: Designing parallel programs: Foster’s method
**Questions**\
Describe Foster’s method for parallel program design and explain each of the method’s steps.

**Answers**

1. Partitioning\
Distribution of data and computation.\
Goal: detet as much parallelism as possible.\
Checklist:
    - [ ] At least one order of magnitude more elementary tasks than processors in target machine
    - [ ] Minimize redundant computations and redundant storage of data
    - [ ] Elementary task of "equal size"
    - [ ] Number of tasks grows with problem size

2. Communication\
Determine communication pattens between elementary tasks.
There are two kinds of communication, local communication (from few other task) and global communication (from many tasks). Note that communication is overhead.\
Checklist:
    - [ ] Distribute communication operations evenly across the tasks
    - [ ] Every task communicates only with a small number of neighbors
    - [ ] Tasks can execute communication concurrntly
    - [ ] Tasks can execute computatio concurrently

3. Agglomeration\
Agglometrate elementary tasks to larger tasks; align number of tasks with number of processors.
When maximum parallelism are much more than parallelism of machine, we use agglomeration to improve locality. The benefit is that there are no communications between agglomerated tasks (data is in shared memory).\
To limit software engineering cost, it's preferred agglomerations that allow more of the sequential code to be reused.\
Checklist:
    - [ ] Agglomeration increases locality of parallel algorithm
    - [ ] Replicated computations use less time than the communication they avoid
    - [ ] Volumn of replicated data is small, does not compromise scalablity
    - [ ] Agglomerated tasks have similar cost regarding computation and communication
    - [ ] Number of tasks grows with problem size
    - [ ] Number of tasks in minimal but at least as large as the number of processors of a potential execution platform
    - [ ] Reasonable trade-off between selected agglomeration and effort for the modification of the sequential code

4. Mapping\
Assign tasks to processes.\
Goal (goals conflict to each other. It needs some trade-off): 
    1. Maximum utiliztion of all proceccors (tasks are evenly distributed on n processor)
    2. minimum interprocessor communication (all tesks in one processor)\
    Checklist:
    - [ ] Consider designs based on one task per processor and multiple tasks per processor
    - [ ] evaluate the static and dynamics allocation of tasks
    If the tasks are dynamically allocated, the task allocator (i.e. manager) is not a performance bottleneck
    - [ ] If tasks are statically allocated, the ratio of tasks to processors is at least 10:1
    
<a name="t6">

## Task 6.6: Designing parallel programs: boundary value problem
**Question**\
What do you understand by the boundary value problem that we discussed in the lecture? Summarize how to apply the four-stage design methodology of Ian Foster to the problem.

**Answer**\
**Data structure**\
By discretizating of space (gris width h) and of time (time step t), we get

<img src="https://render.githubusercontent.com/render/math?math=u_{i,j}">: temperature at grid point i at time j

<img src="https://render.githubusercontent.com/render/math?math=u_{i,j %2B 1} = F(u_{i-1,j}, u_{i,j}, u_{i %2B 1,j})">

<br>
<img src="/image/task6-6-1.png" width="300">

**Step 1: Partitioning**
Each u(i, j) is a separate task. Note that tasks cannot be computed concurrently, we'll deal with it when agglomeration.

**Step 2: Comunication**

<img src="/image/task6-6-2.png" width="300">

Each circle represent a task u(i, j) (x-axis: width; y-axis: time). The arrows represent the communication direction.

**Step 3 : Agglormeration**
Single task for all time steps of element i. In this example: 10 consolidated tasks.

<img src="/image/task6-6-3.png" width="300">

**Step 4: Mapping**
In this example: n = 3 processors. 4 tasks for the first processor. 3 tasks for the second and 3 tasks for the third one.

<img src="/image/task6-6-4.png" width="300">

> image source: [lecture notes](https://lsf.uni-rostock.de/qisserver/rds?state=verpublish&status=init&vmfile=no&publishid=125991&moduleCall=webInfo&publishConfFile=webInfo&publishSubDir=veranstaltung&idcol=k_semester.semid&idval=20202&getglobal=semester&htmlBodyOnly=true)
