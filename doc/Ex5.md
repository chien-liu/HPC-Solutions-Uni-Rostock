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
