# HPC exercise 5
###### tags `uni-rostock` `HPC`

## Table of Contents
<!-- ts -->
* [Task5.1](#t1)
* [Task5.2](#t2)
* [Task5.3](#t3)
* [Task5.4](#t4)
* [Task5.5](#t5)
* [Task5.6](#t6)
* [Task5.7](#t7)
* [Task5.8](#t8)
<!-- te -->


<a name="t1">

## Task 5.1: ISO/OSI model
**Question**\
What are two reasons for using layered protocols? What is one possible disadvantage of using layered
protocols?

**Answer**\
Open System Interconnection (OSI) Model\
1. Application Layer
2. Prersentation Layer
3. Session Layer
4. Transport Layer
5. Network Layer
6. Datalink Layer
7. Physical Layer

Advantages\
Each layer has its own functionality protocol, which makes OSI model easy for testing and replacible with better implementations in the fulture.

<a name="t2">

## Task 5.2: Speed of data transmissions
**Question**\
An image is 1600 × 1200 pixels with 3 bytes/pixel. Assume the image is uncompressed. How long does it take to transmit it over a 56-kbps modem channel? Over a 1-Mbps cable modem? Over a 10-Mbps Ethernet? Over 100-Mbps Ethernet? Over gigabit Ethernet?

**Answer**\
The (greyscale) image size is 1600 × 1200 × 3 bytes or 46080000 bits.\
56kps :arrow_right: 46080000 / 56000 = 823 sec \
1-Mbps :arrow_right: 46080000 / 1e6 = 46 sec \
10 Mbps :arrow_right: 46080000 / 1e7 = 4.6 sec \
100 Mbps :arrow_right: 46080000 / 1e8 = 0.46 sec \
1 gigabit :arrow_right: 46080000 / 1e9 = 0.046 sec

<a name="t3">

## Task 5.3: Transfer direction of computer communication
**Question**\
Is an oil pipeline a simplex system, a half-duplex system, a full-duplex system, or none of the above? What about a river or a walkie-talkie-style communication?

**Answer**\
* Simplex system: unidirectional, in one direction only
* Half-duplex system: bidirectional but not simultaneously
* Full-duplex system: bidirectional, even simultaneously

River: simplex
Oil pipeline: half-duplex
Walkie-talkie: full-duplex

<a name="t4">
  
## Task 5.4: Fiber optics and copper
**Question**\
What are the advantages of fiber optics over copper as a transmission medium? Is there any downside of using fiber optics over copper?

**Answer**\
||Fiber Optics|Copper|
|--|--|--|
|Distance|Longer|Shorter|
|Bandwidth|Higher|Lower|
|Noise|Immune|Affected by electromagnetic interferences|
|Weigh|Lighter|Heavier|
|Fragility|fragile||
|Price|Cheaper|Depends|

<a name="t5">
  
## Task 5.5: Communication over Ethernet
**Question**\
Try to explain under which circumstances Ethernet frames can be delayed in switches or even discarded.

**Answer**\
There may be many reasons resulting in a network latency. The posible contributiors to it include the following factors:
* The time it takes for a packet to physically travel from its source to a destination.
* Anti-virus and similar security process, which needs time to finish message recombination and dismantling before sending.
* Error from router or switch since each gateway needs to spend time checking and changing the packet headers.
* Storage delays when packets suffers from storage or disk access delays at intermediate devices like switches and bridges.
* Software bugs from user’s side.
* The problem is from the transmission medium itself, which takes some time to transmit one packet from a source to a destination from fiber optics to coaxial cables.
* Delays occur even when packets travel from one node to another at the speed of light.

<a name="t6">
  
## Task 5.6: Real time and time-sensitive networking 
**Question**\
What do you understand by hard real time? Which kind of multiplexing can be used to enforce real-time behavior in a network? How does time-sensitive networking achieve real-time behavior in a network?

**Answer**\
Hard real time :The hard real-time definition considers any missed deadline to be a system failure. This scheduling is used extensively in mission critical systems where failure to conform to timing constraints results in a loss of life or property.

Time Division Multiplexing: Every user is given with same amount of time transfering its data. (sth like round-robin)\
Statistical Time Division Multiplexing: Every user is given time proportional to workload to tranfering its data.

Time Sensitive Network (TSN)\
A set of standards under development by the Time-Sensitive  networking task group of the IEEE 802.1 working group.

TSN includes _Time Syncronization_, _Scheduling_ and _Traffic Shapping_, which ensures real-time behavior.
  
<a name="t7">

## Task 5.7: Wireless communication
**Question**\
Consider five wireless stations, A, B, C, D, and E. Station A can communicate with all other stations. B can communicate with A, C and E. C can communicate with A, B and D. D can communicate with A, C
and E. E can communicate with A, D and B.
(a) When A is sending to B, what other communications are possible?
(b) When B is sending to A, what other communications are possible?
(c) When B is sending to C, what other communications are possible?

**Answer**\
A: BCDE
B: ACE
C: ABD
D: ACE
E: ABD

(a) A :arrow_right: B
AB\
ACB\
ACDEB\

<a name="T8">

## Task 5.8: Transport protocols UDP and TCP
**Question**\
Compare UDP and TCP in terms of the advantages, disadvantages, and application areas.

**Answer**\
||TCP|UDP|
|--|--|--|
|Protocol|connection-oriented|connectionless|
|Speed|slower|faster|
|Handshake|3-way handshake|No|
|Error Checking|Yes|Yes|
|Error Recovery|Yes|No (discard)|
||heavy-weight|lightweight|
|Application|When an occasional delay is acceptable.<br> e.g.texting|When an occasional delay is also not acceptable.<br>e.g., Multiplayer games|

> source: [guru99.com](https://www.guru99.com/tcp-vs-udp-understanding-the-difference.html)
 
<a name="t9">
  
## Task 5.9: Peer-to-peer networks: BitTorrent
**Question**\
The BitTorrent protocol is useful for distributing files as well as distributing streams. What needs to be considered in the distribution in the case of stream distribution compared to file distribution?

**Answer**\
