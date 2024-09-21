
# 1.1 What is Internet?

_The_ _**Internet**_ _is a computer network that interconnects billions of computing devices throughout the world._

The internet is a **compound of networks,** interconnected with each other.

## **Computer:**

- _An electronic machine that can store, organize and find information, do processes with numbers and other data, and control other machines._

## **Computer Network:**

- _A number of computers and other devices that are connected together so that equipment and information can be shared._
- A number of interconnected computers, machines, or operations.
- There are **hosts** or **end systems.**

## Components of the Internet:

![[../../../Attachments/Untitled 34.png|Untitled 34.png]]

**Host/End System:**

- A _host_ or _end system is a device connected to the Internet._
- **Host** is a computer connected via Internet whereas **End system** are those type of computer connected computer network.
- Traditional Devices:
    - Desktop PCs, Linux workstations, servers
- Non-Traditional Devices (Now-days)
    - laptops, smartphones, tablets, TVs, gaming consoles,  
        thermostats, home security systems, home appliances, watches,  
        eyeglasses, cars, traffic control systems

  

The **Internet of things (IoT)** describes the network of **physical objects**.

**End systems** are connected together by a network of **communication links** and **packet switches.**

- Different links can transmit data at different rates, which the **transmission rate** of a link measured in bits/seconds

**Packets:**

- When one end system has data to send to another end system, the sending end system segments the data and **adds** **header** **bytes** to **each** **segment**.
- The resulting packages of information, known as **packets** in the jargon of computer networks to the destination end system, where they are reassembled into the original data.

A **packet switch** takes a packet arriving on one of its incoming communication links and forwards that packet to one of its outgoing communication links.

**Two Prominent types of Packet Switch:**

Both types of switches forward packets toward their ultimate destinations.

- Router
- Link-layer switches

![[../../../Attachments/Untitled 1 8.png|Untitled 1 8.png]]

**Router:**

- Router are used in the network core.

**Link-layer Switch:**

- Link-layer switches are used in access networks.

![[../../../Attachments/Untitled 2 6.png|Untitled 2 6.png]]

- point-to-point link:
- multiple access link:
    - There is going to concurrency, as the multiple computer access the link, there would be crashes.

There are many types of communication links, which are made up of different types of **physical media**.

Different links can transmit data at different rates, with the **transmission rate** of a link measured in bits/second.

Router vs Switch:

- Difference between a router and a switch is that router takes the message, reads the message, takes some decision then it goes somewhere else. While switch essentially takes the input and and goes to some output.

The sequence of communication links and packet switches traversed by a packet from the sending end system to the receiving end system is known as a **route** or **path** through the network.

## Service Description:

- Terms of service → delivers data (reliable) to TCP.
    
    “Best Effort” data delivery protocol to OP
    
- Terms of infrastructure → the internet provides a communication infrastructure. It enables distributed applications i.e. web, games, email.

## Internet Protocols:

End systems, packet switches, and other pieces of the Internet run **protocols** that control the sending and receiving of information within the Internet.

![[../../../Attachments/Untitled 3 4.png|Untitled 3 4.png]]

A Human Protocol and a Computer Network Protocol

The set of communication protocols used on the Internet is known as the **TCP/IP protocol suite.**

All activity on the Internet that involves two or more communication remote entities is governed by a protocol.

_A protocol defines the_ **_format_** _and the_ **_order_** _of_ **_messages_** _exchanged between two or more_ **_communicating entities,_** _as well as the_ **_action taken_** _on the transmission and/or receipt of a message or other event._

# 1.2 Network Edge

- The Internet hosts - i.e., computer or other device connected to the Internet - constitute that so called **network edge.**

![[../../../Attachments/Untitled 4 3.png|Untitled 4 3.png]]

End-system Interaction

- The computers and other devices connected to the Internet are often referred to as end system.
- They are referred to as end systems because they sit at the edge of the Internet.

## 1.2.1 Access Networks:

![[../../../Attachments/Untitled 5 3.png|Untitled 5 3.png]]

Access Networks

- **Access Network:** The network that physically connects an end system to the first router on a path from the end system to any other distant end system.

### **Home Access: DSL, Cable, FTTH, Dial-Up, and Satellite**

Two most prevalent types of broad-land residential access are:

- Digital Subscriber line (DSL)
- Cable

**Digital Subscriber Line (DSL):**

- A DSL internet access is obtained from the same local telephone company which provides its wired local phone access.
- Hence, when DSL is used, a customer’s telecom is also its ISP.

![[../../../Attachments/Untitled 6 3.png|Untitled 6 3.png]]

DSL Internet access

**Cable Internet Access:**

- While DSL makes use of the telecom's existing local telephone infrastructure, cable internet access makes use of the cable television company’s existing cable television infrastructure.
- A residence obtains cable Internet access from the same company that provides its cable television.
- The fiber optics are connected to the cable head end to neighborhood-level junctions, from which traditional coaxial cable is then used to reach individual houses and apartments.
- Since both fiber and coaxial cable are employed in this system, it is often referred to as hybrid fiber coax (HFC).

![[../../../Attachments/Untitled 7 3.png|Untitled 7 3.png]]

A hybrid fiber-coaxial access network

**FTTH:**

- Although DSL and cable networks currently represent more than 90 percent of residential broadband access in the United States, an up-and-coming technology that promises even higher speeds is the deployment of **fiber to the home (FTTH).**
- It is a concept which mean to provide an optical fiber path from the CO directly to the home.

![[../../../Attachments/Untitled 8 3.png|Untitled 8 3.png]]

FTTH Internet access

**Satellite link & Dial-up:**

- A satellite link can be used to connect a residence to the Internet at speeds of more than 1Mbps; StarBand and HughesNet.
- The Dial-up access is over the traditional phone lines which is based on the same model as DSL.

### **Access in the Enterprise: Ethernet and WiFi**

**Ethernet:**

- Although there are many types of LAN technologies, Ethernet is by far the most prevalent access technology in corporate, university, and home networks.
- Ethernet users use twisted-pair copper wire to connect to an Ethernet switch.
- The Ethernet switch, or a network of such interconnected switches, is then in turn connected into the larger Internet.
- With Ethernet access, users typically have 100 Mbps access to the Ethernet switch, whereas servers may have 1 Gbps or even 10 Gbps access.

![[../../../Attachments/Untitled 9 3.png|Untitled 9 3.png]]

Ethernet Internet access

**WIFI:**

- In a wireless LAN setting wireless users transmit/receive packets to/from an access point that is connected into the enterprise’s network, which in tun is connected to the wired Internet.
- The user must be within a few tens of meters of the access point.

![[../../../Attachments/Untitled 10 3.png|Untitled 10 3.png]]

A typical home network

**Wide-Area Wireless Access: 3G and LTE:**

- With this devices such as smartphones could still be connected to the internet
- Unlike WIFI, a user need only be within a few tens of kilometres of the base station.

## 1.2.2 Physical Media:

- For each transmitter-receiver pair, the bit is sent by propagating electromagnetic waves or optical pulses across a **physical medium**.
- Physical Medium fall in two categories:
    - **Guided Media**
    - **Unguided Media**
- Guided Media: The waves are guided along a solid medium, such as a fiber-optic cable, a twisted-pair copper wire, or a coaxial cable.
- Unguided Media: The waves propagate in the atmosphere and in outer space, such as in a wireless LAN or a digital satellite channel.

**Twisted-Pair Copper Wire**

- Least Expensive and most commonly used guided transmission medium is twisted-pair copper wire.
- Been there for the last 100 year, and is still used for high data transfer.

**Coaxial Cable**

- Consists of two copper conductors, but the two conductors are concentric rather than parallel.
- Common in cable television systems.
- Could be used as a guided shared medium.

**Fiber Optics**

- It is thing, flexible medium that conducts pulses of light, with each pulse representing a bit.
- A single optical can support tremendous bit rates, up to tens or even hundred of gigabits per second.

**Terrestrial Radio Channels**

- Radio channels carry signals in the electromagnetic spectrum.
- They are an attractive medium because they require no physical wire to be installed, can penetrate walls, provide connectivity to a mobile user, and can potentially carry a signal for long distances.

# 1.3 The Network Core

Mesh of packet switches and links that interconnects the Internet’s end systems.

![[../../../Attachments/Untitled 11 3.png|Untitled 11 3.png]]

The Network Core

## 1.3.1 Packet Switching:

- In a network application, end systems exchange **messages** with each other.
- To send a message from a source end system to a destination end system, the source breaks long messages into smaller chunks of data known as **packets.**
- Between source and destination, each packet travels through communication links and **packet switches.**
- Packets are transmitted over each communication link at a rate equal to the _full_ transmission rate of the link.
- So, if a source end system or a packet switch is sending a packet of _L_ bit over a link with transmission rate _R_ bit/sec, then the time to transmit the packet is $\frac{L}{R} \space seconds$﻿.

**Store-and-forward Transmission:**

- Store-and-forward transmission means that the packet switch must receive the entire packet before it can begin to transmit the first bit of the packet onto the outbound link

![[../../../Attachments/Untitled 12 2.png|Untitled 12 2.png]]

Store-and-forward packet switching

- Calculating the amount of time that elapses from when the source begins to send the packet until the destination has received the entire packet.
    - The source begins to transmit at time 0.
    - At time $\frac{L}{R}$﻿seconds, the source has transmitted the entire packet.
    - At time $\frac{L}{R}$﻿ seconds, since the router has just received the entire packet, it can begin to transmit the packet onto the outbound link towards the destination.
    - At time $2\frac{L}{R}$﻿, the router has transmitted the entire packet, and the entire packet has been received by the destination.
    - Thus, the total delay is $2\frac{L}{R}$﻿.
- **End-To-End delay is:**
    - $d_{end-to-end} = N \frac{L}{R}$﻿
        - P packets sent over a series of N links
        - R = rate

**Queuing Delays and Packet Loss**

- Each packet switch has multiple links attached to it.
- For each attached link, the packet switch has an **output buffer,** which stores packets that the router is about to send into that link
- Output buffers play a key role in packet switching.
- If an arriving packet needs to be transmitted onto a link but finds the link busy with the transmission of another packet, the arriving packet must wait in the output buffer.
- In addition to the store-and-forward delays, packets suffer output buffer **queuing delays.**
- Due to the amount of buffer space being finite, an arriving packet may find that the buffer is completely full with other packets waiting for transmission.
    - In this case, **packet loss** will occur - either the arriving packet or one of the already-queued packets will be dropped.

![[../../../Attachments/Untitled 13 2.png|Untitled 13 2.png]]

Packet Switching

**Forwarding Tables and Routing Protocols**

- How does the router determine which link it should forward the packet onto?
- Every end system has an address called an IP address.
- The address has a hierarchical structure.
- When a packet arrives at a router in the network, the router examines a portion of the packet’s destination address and forwards the packet to an adjacent router.
- More specifically, each router has a **forwarding table** that maps destination addresses. to that router’s outbound links.

## 1.3.2 Circuit Switching:

- There are two fundamental approaches to moving data through a network of links and switches
    - Circuit Switching
    - Packet Switching
- In circuit-switched networks, the resources needed along a path to provide for communication between the end systems are _reserved_ for the duration of the communication session between the end systems.

![[../../../Attachments/Untitled 14 2.png|Untitled 14 2.png]]

A simple circuit-switched network consisting of four switches and four links

### **Multiplexing in Circuit-Switched Networks**

- It is when a circuit in a link is implemented with either **frequency-division multiplexing (FDM)** or **time-division multiplexing (TDM).**
- With FDM, the frequency spectrum of a link is divided up among the connections established across the link.
- The width of the band is called, the **bandwidth.**
- For TDM link, time is divided into frames of fixed duration and each frame is divided into a fixed number of time slots.

![[../../../Attachments/Untitled 15 2.png|Untitled 15 2.png]]

With FDM, each circuit continuously gets a fraction of the bandwidth. With TDM, each circuit gets all of the bandwidth periodically during brief intervals of time (that is, during slots)

  

### Advantages and Disadvantages of Circuit Switching:

Pros:

- No bandwidth divisions
- No Dedicated allocation
- No reservation overhead

Cons:

- Resource connection
- Congestion (when everything high speed)
- Store and Forward

### **Packet Switching Versus Circuit Switching**

|   |   |
|---|---|
|**Circuit Switching**|**Packet Switching**|
|The physical path between source and destination|No physical path|
|All packets use the same path|Packets travel independently|
|Reserve the entire bandwidth in advance|Does not reserve|
|Bandwidth Wastage|No Bandwidth Wastage|
|No store and forward transmission|Supports store and forward transmission|

# 1.4 Delay, Loss, and Throughput in Packet-Switched Networks

## 1.4.1 Overview of Delay in Packet-Switched Networks:

- As a packet travels from one node (host or router) to the subsequent node (host or router) along this path, the packet suffers from several types of delays at _each_ node along the path.

![[../../../Attachments/Untitled 16 2.png|Untitled 16 2.png]]

The Nodal Delay at router A

- The most important of these delays are the **nodal processing delay, queuing delay, transmission delay,** and **propagation delay;** together, these delays accumulate to give a **total nodal delay.**
- **Nodal Delay:**
    - Delay at a single router.
- The performance of many Internet applications - such as search, Web browsing, email, maps, instant messaging and voice-over-IP - are greatly affected by network delays.

### **Types of Delay**

**Processing Delay:**

- The time required to examine the packet’s header and determine where to direct the packet is part of the **processing delay.**
- The processing delay can also include other factors, such as the time needed to check for bit-level errors in the packet that occurred in transmitting the packet’s bits from the upstream node to router A.

**Queuing Delay:**

- At the queue, the packet experiences a **queuing delay** as it waits to be transmitted onto the link.
- The length of the queuing delay of a specific packet will depend on the number of earlier-arriving packets that are queued and waiting for transmission onto the link.
- If the queue is empty and no other packet is currently being transmitted, then our packet’s queuing delay will be zero.

**Transmission Delay:**

- Assuming the packets are transmitted in a first-come-first-served manner, as is common in packet-switched networks, our packet can be transmitted only after all the packets that have arrived before it have been transmitted.
- The **Transmission delay** is $\frac{L}{R}$﻿.

**Propagation Delay:**

- Once a bit is pushed into the link, it needs to propagate to router B.
- The time required to propagate from the beginning of the link to router B is the **propagation delay.**
- The bit propagates at the propagation speed of the link.
- It is a function of the distance d between the two routers.
- _The propagation delay is the distance between two routers divided by the propagation speed._

**Comparing Transmission and Propagation Delay:**

- The transmission delay is the amount of time required for the router to push out the packet; it is a function of the packet’s length and the transmission rate of the link but has nothing to do with the distance between the two routers.
- The propagation delay, on the other hand, is the time it takes a bit to propagate from one router to the next; it is a function of the distance between the two routers but has nothing to do with the packet’s length or the transmission rate of the link.

|   |   |
|---|---|
|**Transmission Delay**|**Propagation Delay**|
|Amount of time required for the router to push out the packet|The time it takes a bit to propagate from one router to the next|
|it is a function of the packet’s length L and of the transmission rate R of the link|It is a function of the distance d between the two routers.|
|It has nothing to do with the distance between the two routers|It has nothing to do with the packet’s length or the transmission rate of the link.|

Analogy on the notion of Transmission and Propagation Delay:

- Consider a highway that has tollbooths every 100 kilometres.
- You can think of the highway segments between tollbooths as links and the tollbooths as routers.
- Suppose that cars travel (that is, propagate) on the highway at a rate of 100km/hour (that is, when a car leaves a tollbooth, it instantaneously accelerates to 100 km/hour and maintains that speed between tollbooths).
- Suppose next that 10 cars, traveling together as a caravan as a packet.
- Also suppose that each tollbooth services (that is, transmits) a car at a rate of one car per 12 seconds, and that is is late at night so that the caravan’s cars are the only car per 12 seconds, and that it is late at night so that the caravan’s car are the only cars on the highway.

## 1.4.2 Queuing Delay and Packet Loss:

- Unlike the other three delays, the queuing delay can vary from packet to packet.

### **Queuing Delay:**

- For example, if 10 packets arrive at an empty queue at the same time, the first packet transmitted will suffer no queuing delay, while the last packet transmitted will suffer a relatively large queuing delay.
- Therefore, when characterizing queuing delay, one typically uses statistical measures, such as average queuing delay, the variance of queuing delay, and the probability that the queuing delay exceeds some specified value.
- To understand if the queuing delay is large or when is it insignificant, it depends on the rate at which traffic arrives at the queue, the transmission rate of the link, and the nature of the arriving traffic.

**How to Compute the Queuing Delay?**

Quantification of the queuing delay:

- Average queuing delay
- The variance of queuing delay
- Probability that queuing delay exceeds some threshold value

Crucial Parameters:

- Rate at which traffic arrives at the queue: **a packets/second**
- Transmission rate of the link: **R bits/second**
- Nature of the arriving traffic
    - Periodic or in Burst

Parameters to compute queuing delay?

- Packet length: $L$﻿ bits
- Average rate at which traffic arrives at the queue: $a$﻿ packets/second
- Transmission rate of the link: $R$﻿ bits/second

**Average rate at which bits arrive at the queue:** $L \times a$﻿

**Average rate at which bits can leave the queue:** $R$﻿

Ratio $\frac{La}{R}$﻿ is the **traffic intensity**

If $La > R$﻿ then the average rate at which bits arrive at the queue exceeds the rate at which the bits can be transmitted from the queue

Traffic intensity should be smaller than one: $\frac{La}{R} < 1$﻿

### **Packet Loss:**

- It is assumed that the queue, is capable of holding an infinite number of packets, however in reality a queue preceding a link has finite capacity, although the queuing capacity greatly depends on the router design and cost.
- Since the queue is finite, packet delays do no really approach infinity as the traffic intensity approaches 1.
- Instead, a packet can arrive to find a full queue.
- With no place to store such a packet, a router will **drop** that packet; that is, the packet will be **lost.**

## 1.4.3 End-to-End Delay

- Now consider the total delay from source to destination.
- Assuming there are $N-1$﻿ router between the source host and the destination host.
- Also assuming that the network is un-congested (so that queuing delays are negligible), the processing delay at each router and at the source host is $d_{proc}$﻿, the transmission rate out of each router and out of the source host is $R \space bits/sec$﻿, and the propagation on each link is $d_{prop}$﻿.
- The nodal delays accumulate and give an end-to-end delay,

$d_{end-end} = N(d_{proc}+d_{trans}+d_{prop})$

### One-hop Transmission Delay (1 hops)

$d_{tx, 1hop} = \frac{L}{R}$

![[../../../Attachments/Untitled 17 2.png|Untitled 17 2.png]]

![[../../../Attachments/Untitled 18 2.png|Untitled 18 2.png]]

![[../../../Attachments/Untitled 19 2.png|Untitled 19 2.png]]

### End-to-end Transmission Delay (2 hops)

$d_{tx, 2hops} = 2\frac{L}{R}$

![[../../../Attachments/Untitled 20 2.png|Untitled 20 2.png]]

  

### End-to-end Transmission Delay (3 hops)

$d_{tx, 2hops} = 3 \frac{L}{R}$

![[../../../Attachments/Untitled 21 2.png|Untitled 21 2.png]]

  

### End-to-end Transmission Delay (N hops)

$d_{tx, e2e} = N \frac{L}{R}$

![[../../../Attachments/Untitled 22 2.png|Untitled 22 2.png]]

  

### End-to-end transmission Delay (N hops, different rates)

$d_{tx, e2e} = \sum^{N}_{i = 1} \frac{L}{R_{i}}$

![[../../../Attachments/Untitled 23 2.png|Untitled 23 2.png]]

![[../../../Attachments/Untitled 24 2.png|Untitled 24 2.png]]

### End System, Application, and Other Delays

- There can be additional significant delays in the end systems, other than processing, transmission, and propagation delays.
- For example, an end system wanting to transmit a packet into a shared medium may _purposefully_ delay its transmission as part of its protocol for sharing the medium with another system.
- Another important delay is media packetization delay, which is present in Voice-over-IP (VoIP) applications.

## 1.4.4 Throughput in Computer Networks

- Another critical performance measure in computer networks is end-to-end throughput.
- To define throughput, consider transferring a large file from Host A to Host B across a computer network.
- The **instantaneous throughput** at any instant of time is the rate (in bits/sec) at which Host B is receiving the file.
- If the file consists of _F_ bit and the transfer takes _T_ seconds for Host B to receive all _F_ bits, then the **average throughput** of the file transfer is _F/T_ bits/sec.

![[../../../Attachments/Untitled 25 2.png|Untitled 25 2.png]]

- The above figure shows two end systems, a server, and a client, connected by two communication links and a router.
- Consider the throughput for a file transfer from the server to the client
- Let $R_{s}$﻿ denote the rate of the link between the server and the router; and $R_{c}$﻿ denote the rate of the link between the router and the client.
- Suppose that the only bits being sent in the entire network are those from the server to the client.
- In the ideal scenario, it is asked what is the server-to-client throughput.
- To answer this question we think of bits as _fluid_ and communication links as _pipes._
- Clearly, the server cannot pump bits at a rate faster than $R_{c}$﻿ bps.
- If $R_{s} < R_{c}$﻿ then the bits pumped by the server will “flow” right through the router and arrive at the client at a rate of $R_{s}$﻿bps, giving a throughput of $R_{s}$﻿bps.
- If on other hand $R_{c} < R_{s}$﻿, then the router will not be able to forward bits as quickly as it receives them. In this case, bits will only leave the router at rate $R_{c}$﻿, giving an end-to-end throughput of $R_{c}$﻿

# 1.5 Protocol Layers and Their Service Models

## 1.5.1 Layered Architecture

### Protocol Layering

- To provide structure to the design of network protocols, network designers organize protocols - and the network hardware and software that implement the protocols - in **layers.**
- Each protocol belongs to one of the layers, and each layer provides its service by:
    - performing certain actions within that layer
    - by using the service of the layer directly below it
        - For example, the services provided by layer _n_ may include reliable delivery of messages from one edge of the network to the other. This might be implemented by using an unreliable edge-to-edge message delivery service for layer _n - 1,_ and adding layer _n_ functionality to detect and re-transmit lost messages.
- A protocol layer can be implemented in software, in hardware, or in a combination of the two.

![[../../../Attachments/Untitled 26 2.png|Untitled 26 2.png]]

Five-layer Internet Protocol Stack

- Taken together, protocols of various layers are called the **protocol stack.**
- Application-layer protocols — such as HTTP and SMTP — are almost always implemented in software in the end systems; so are transport-layer protocols.

**Layered Architecture of the Internet:**

![[../../../Attachments/Untitled 27 2.png|Untitled 27 2.png]]

### Application Layer

- The application layer where network applications and their application-layer protocols reside
- Example of application layer protocols
    - HTTP (Hypertext Transfer Protocol)
    - FTP (File Transfer Protocol)
    - SMTP (Simple Mail Transfer Protocol)
- A packet of information in the application later is referred to as a **message**

### Transport Layer

- The Internet’s transport layer transports application-layer messages between application endpoints.
- Transport Layer protocols
    - TCP (Transmission Control Protocol)
    - UDP (User Data-gram Protocol)

|   |   |
|---|---|
|**TCP**|**UDP**|
|Connection-oriented|Connection-less service|
|Guaranteed delivery|No guarantee of message delivery|
|Flow Control|No Flow Control|
|Congestion Control|No congestion control|

- Packet of information at the transport layer is referred to as **segments**

### Network Layer

- The Internet’s network layer routes a datagram through a series of routers between the source and destination
- Only one network-layer protocol: **Internet Protocol (IP)**
- Responsible for moving **packets** from one host to another

### Link Layer

- The link layer is responsible for moving a packet from one node (host or router) to the next node in the route
- Examples of link-later protocols
    - Ethernet
    - Wi-fi
- A packet of information at the link layer is referred to as a **frame**

### Physical Layer

- The physical layer is responsible for moving the individual bits within a frame from one node to the next
- Example of physical layers
    - Twisted-pair copper wire
    - Coaxial cable
    - Fiber optic cable
- The packet of information at the physical layer is the **bit**

## 1.5.2 Encapsulation

![[../../../Attachments/Untitled 28 3.png|Untitled 28 3.png]]

Hosts, routers, and link-layer switches; each contains a different set of layers, reflecting their differences in functionality

- The above figure shows the physical path that data takes down a sending end system’s protocol stack, up and down the protocol stacks of an intervening link-layer switch and router, and then up the protocol stack at the receiving end system.