# Table of Contents

---

Table of Contents

3.1 Introduction and Transport-Layer Services

3.1.1 Relationship Between Transport and Network Layers

3.1.2 Overview of the Transport Layer in the Internet

3.2 Multiplexing and Demultiplexing

Connection-less Multiplexing and Demultiplexing

Connection-Oriented Multiplexing and Demultiplexing

3.3 Connection-less Transport: UDP

3.3.1 UDP Segment Structure

3.3.2 UDP Checksum

3.4 Principles of Reliable Data Transfer

3.4.1 Building a Reliable Data Transfer Protocol

rdt1.0: Reliable transfer over a reliable channel

rdt2.0: Channel with bit errors

rdt2.1: Sender, handling garbled ACK/NAKs

rdt2.2: a NAK-free protocol

rdt3.0: Channels with errors and loss

3.4.2 Pipelined Reliable Data Transfer Protocol

3.4.3 Go-Back-N (GBN)

3.4.4 Selective Repeat (SR)

3.5 Connection-Oriented Transport: TCP

3.5.1 The TCP Connection

TCP Fast retransmit

TCP Flow Control

Flow Control:

TCP Connection Management

3.6 Principles of Congestion Control

---

# 3.1 Introduction and Transport-Layer Services

- A transport-layer protocol provides for **logical communication** between application processes running on different hosts
- By logical communication it means that from an application’s perspective, it is as if the hosts running the processes were directly connected; in reality, the hosts may be on opposite sides of the planet, connected via numerous routers and a wide range of link types.

![[../../../Attachments/Untitled 36.png|Untitled 36.png]]

The transport layer provides logical rather than physical communication between application processes

- Transport-layer protocols are implemented in the end system but not in network routers.
- On the sending side, the transport layer converts the application-layer messages it receives from a sending application process into transport-layer packets, known as transport-layer segments in Internet terminology.
- This is done by breaking the application messages into smaller chunks and adding a transport-layer header to each chunk to create the transport-layer segment.
- **Receiver:** Reassembles segments into messages, passes to the Application layer.

## 3.1.1 Relationship Between Transport and Network Layers

- A transport-layer protocol provides logical communication between **processes running on different hosts.**
- A network layer protocol provides logical communication **between hosts.**

![[../../../Attachments/Untitled 1 10.png|Untitled 1 10.png]]

Household Analogy

## 3.1.2 Overview of the Transport Layer in the Internet

- **Transport Services and Protocols:**
    - Provide _logical communication_ between application processes running on different hosts.
    - Transport protocols actions in the end system:
        - Sender: breaks application messages into **segments,** passes them to the network layer
        - Receiver: Reassembles segments into messages, and passes them to the application layer.
- Two Distinct Transport-layer protocols are available to the application layer:
    - **UDP** (User Datagram Protocol)
    - **TCP** (Transmission Control Protocol)
- Transport-layer packet is referred to as a **segment.**
- Packets for UDP are referred to as data-gram
- **Internet's Network-layer protocol**
    - Has a name — IP, for Internet Protocol
        - IP provides logical communication between hosts.
        - The IP service model is a **best-effort delivery service,** meaning the IP makes its best effort to deliver segments between communicating hosts, but it makes no guarantees.
        - For these reasons, IP is said to be an **unreliable service**
- **Service Models provided by UDP and TCP:**
    - A **most** fundamental responsibility of UDP and TCP is to extend IP’s delivery service between two end systems to a delivery service between two processes running on the end systems.
    - Extending host-to-host delivery to process-to-process delivery is called **transport-layer multiplexing** and **demultiplexing.**
    - UDP and TCP also provide integrity checking by including error-detection fields in their segments’ headers.
        - These two minimal transport-layer services — process-to-process data delivery and error checking are the only two services that UDP provides, hence making UDP an **unreliable service** since it doesn't guarantee that data sent by one process would arrive intact.
    - **TCP:**
        - Offers several additional services to applications.
            - **Reliable Data Transfer**
                - Using flow control, sequence numbers, acknowledgments, and timers, TCP ensure that data is delivered from sending process to receiving process, correctly and in order.
            - **Congestion Control**
                - Service provided for the Internet as a whole.
                - TCP congestion control prevents any one TCP connection from swamping the links ad routers between communication hosts with an excessive amount of traffic
            - **Flow Control**
            - **Connection Setup**
    - **UDP:**
        - Offers no services.
            - **unreliable, unordered delivery**
            - **Non-frills extension of** **_best effort_** **IP**

# 3.2 Multiplexing and Demultiplexing

- Extending the **host-to-host** delivery service provided by the network layer to a **process-to-process** delivery service for applications running on the hosts.
- Needed for all computer networks.
- At the destination host, the transport layer receives segments from the network layer just below.
- The transport layer has the responsibility of delivering the data in these segments to the appropriate application process running in the host.

![[../../../Attachments/Untitled 2 8.png|Untitled 2 8.png]]

Transport-layer multiplexing and demultiplexing

- **Example Explanation:**
    - Suppose you are downloading web pages while running one FTP session and two Telnet sessions. (Having 4 network processes running)
    - When the transport layer in your computer receives data from the network layer below, it needs to direct the received data to one of these four processes.
    - A process can have one or more **sockets, and** doors through which data passes from the network to the process and through which data passes from the process to the network.
    - As shown in the above figure, the transport layer in the receiving host does not actually deliver data directly to a process, but instead to an intermediary socket.
    - How a receiving host directs an incoming transport-layer segment to the appropriate socket.
    - Each transport-layer segment has a set of fields in the segment for this purpose.
    - At the receiving end, the transport layer examines these fields to identify the receiving socket and then directs the segment to that socket.
    - This job of delivering the data in a transport-layer segment to the correct socket is called **demultiplexing.**
    - The job of gathering data chunks at the source host from different sockets, encapsulating each data chunk with header information to create segments, and passing the segments to the network layer is called **multiplexing.**
- **Multiplexing at Sender:**
    - Handle data from multiple sockets, and add transport header (later used for demultiplexing).
- **Demultiplexing at receiver:**
    - Use header info to deliver receiver segments to the correct socket.
- **How Demultiplexing works**
    
    - Host Receives IP datagrams
        - Each datagram has a source IP address, destination IP address
        - Each datagram carries one transport-layer segment
        - Each segment has a source, destination port number
    - The host uses **IP addresses and Port Numbers** to direct segments to the appropriate socket
    
    ![[../../../Attachments/Untitled 3 6.png|Untitled 3 6.png]]
    
- **Port Numbers**
    - Port number: **16-bit** number
    - Port numbers from 0 to 1023 called **well-known port numbers**
    - Each application is assigned a default port number

### Connection-less Multiplexing and Demultiplexing

- When creating a segment to send into the UDP socket, the sender must specify:
    - Destination IP address
    - Destination port #
- When receiving host receives UDP segment:
    - Checks destination port in the segment
    - Direct UDP segment to the socket with that port.

![[../../../Attachments/Untitled 4 5.png|Untitled 4 5.png]]

### Connection-Oriented Multiplexing and Demultiplexing

- TCP socket identified by **4-tuple**
    - Source IP address
    - Source port number
    - Destination IP address
    - Destination port number
- Demux: receiver uses **all four values** (4-tuple) to direct segment to appropriate socket
- The server may support many **simultaneous TCP sockets**
    - Each socket is identified by its own 4-tuple
    - Each socket is associated with a different connecting client

![[../../../Attachments/Untitled 5 5.png|Untitled 5 5.png]]

# 3.3 Connection-less Transport: UDP

- Does as little as a transport protocol can do
    - **Multiplexing / De-multiplexing**
    - **Error Checking**
- UDP is **connection-less**
    - There is **no** handshaking between sending and receiving transport-layer entities before sending a segment.
    - Each UDP segment is handled independently of the others.
- Why many applications are better suited for UDP:
    - **Finer application-level control over what data is sent, and when:**
        - Under UDP as soon as an application process passes data to UDP, UDP will package the data inside a UDP segment and immediately pass the segment to the network layer.
        - TCP, on the other hand, has a congestion-control mechanism that throttles the transport-layer TCP sender when one or more links between the source and destination hosts become excessively congested.
    - **No connection establishment**
        - TCP uses a three-way handshake before it starts to transfer data.
        - UDP just blasts away without formal preliminaries.
        - Thus UDP does not introduce any delay to establish a connection.
    - **No connection state**
        - TCP maintains a connection state in the end systems
        - This connection state includes receive and send buffers, congestion-control parameters, and sequence and acknowledgment number parameters.
    - **Small packet header overhead**
        - The TCP segment has 20 bytes of header overhead in every segment, whereas UDP has only 8 bytes of overhead.

## 3.3.1 UDP Segment Structure

![[../../../Attachments/Untitled 6 5.png|Untitled 6 5.png]]

UDP segment structure

- **Fields in the header**
    - Source port (2 bytes)
    - Destination port (2 bytes)
    - Length (2 bytes)
    - Checksum (2 bytes)

## 3.3.2 UDP Checksum

- The UDP checksum provides for error detection.
- That is, the checksum is used to determine whether bits within the UDP segment have been altered as it moved from source to destination.
- The checksum is needed because of Bit Errors
- **Bit Errors:**
    - Bits may “flip”
        - When transmitted over a physical medium
        - While in storage
    - 0 received as 1
    - 1 received as 0
- **Computing UDP Checksum**
    - The UDP checksum is computed as the one’s complement of the sum of several fields of the UDP header plus some filed from the IP header
    - The part of the IP header used in the computation of the UDP checksum is called the **pseudo-header**
- **UDP Checksum: Sender and Receiver Actions**
    - **Sender** side
        - It treads segment contents as a sequence of 16-bit integers
        - These integers are added. Let's call it a sum
        - Checksum: 1’s complement of the sum
        - Sender puts this checksum value in UDP checksum field
    - **Receiver** side
        - Calculate checksum
        - All segments are added and then the sum is added with the sender’s checksum
        - Check that any 0 bit is presented in the checksum, if the receiver checksum contains any 0 then error is detected. So the packet is discarded by the receiver
- **Checksum Example:**

![[../../../Attachments/Untitled 7 5.png|Untitled 7 5.png]]

- **Checksum: Field to sum**
    - Source port
    - Destination Port
    - Length
    - Checksum

# 3.4 Principles of Reliable Data Transfer

![[../../../Attachments/Untitled 8 5.png|Untitled 8 5.png]]

Reliable data transfer: Service Model and Service Implementation

- A data transfer is **reliable** if
    - **no** transferred data bits are **corrupted** (flipped from 0 to 1, or vice versa) or **lost,**
    - and **all** transferred data bits are **delivered in** the **order** in which they were sent.
- The TCP offers a reliable data transport service
- The general problem of reliable data transfer is the central importance of networking.
- The above figure illustrates the framework for our study of reliable data transfer.
- The service abstraction provided to the upper-layer entities is that of a reliable channel through which data can be transferred.
- With a reliable channel, no transferred data bits are corrupted or lost, and all are delivered in the order in which they are sent.
- It is the responsibility of a **reliable data transfer protocol** to implement this service abstraction.

## 3.4.1 Building a Reliable Data Transfer Protocol

### rdt1.0: Reliable transfer over a reliable channel

![[../../../Attachments/Untitled 9 5.png|Untitled 9 5.png]]

- Assumption: **Underlying channel is perfectly reliable**
    - No bit errors
    - No loss of packets
    - Packets received in the order they are sent
    - Plus: the receiver is able to receive data as fast as the sender happens to send data

### rdt2.0: Channel with bit errors

![[../../../Attachments/Untitled 10 5.png|Untitled 10 5.png]]

- Error Detection
    - Internet checksum
- Assumption: **Internet Checksum is reliable**
- Receiver feedback
    - **Acknowledgments (ACKs)**
        - The receiver explicitly tells the sender that the packet received OK
    - **Negative Acknowledgments (NACKs)**
        - The receiver explicitly tells the sender that the packet has errors
        - Sender re-transmits packet on receipt of NAK
- **Re-transmission**
    - Stop and Wait: Sender sends one packet, then waits for receiver's response
- Also known as **Stop and Wait protoco**l:
    - The sender sends one packet, then waits for the receiver's response
- **Flaw**
    - The sender doesn't know if ACK/NAK is corrupted or not
    - It can just re-transmit but possible **duplicates**
- **Handling Duplicates**
    - Sender re-transmits current pkt if ACK/NAK corrupted
    - The sender adds a _sequence numbe_r to each pkt
    - Receiver discards (doesn’t deliver up) duplicate pkt

### rdt2.1: Sender, handling garbled ACK/NAKs

![[../../../Attachments/Untitled 11 5.png|Untitled 11 5.png]]

![[../../../Attachments/Untitled 12 4.png|Untitled 12 4.png]]

- It uses both positive and negative acknowledgments from the receiver to the sender
- When an out-of-order packet is received, the receiver sends a positive acknowledgment for the packet it has received.
- When a corrupt packet is received, the receiver sends a negative acknowledgment.

### rdt2.2: a NAK-free protocol

- Same functionality as rdt2.1, using ACKs only
- Instead of NAK, the receiver sends **ACK for the last pkt received OK**
    - The receiver must explicitly include seq # of pkt being ACKed
- Duplicate ACK at sender results in the **same action as NAK:**
    - Re-transmit current pkt

### rdt3.0: Channels with errors and loss

- Approach: sender waits a “reasonable” amount of time for ACK
    - Re-transmits if no ACK received at this time
    - If pkt (or ACK) is just delayed (not lost):
        - Re-transmission will be duplicated, but seq \#s already handles this
        - The receiver must specify seq # of the packet being ACKed
- This is also known as a **stop-and-wait operation**

## 3.4.2 Pipelined Reliable Data Transfer Protocol

![[../../../Attachments/Untitled 13 4.png|Untitled 13 4.png]]

- rdt3.0 however gives **poor** performance
- The solution to this particular performance problem is that rather than operating in a stop-and-wait manner, the sender is allowed to send multiple packets without waiting for acknowledgments.
- Since the main in-transit sender-to-receiver packets can be visualized as filling a pipeline, this technique is known as **pipelining.**
- Pipelining has the following consequences for reliable data transfer protocols
    - The range of sequence numbers must be increased since each in-transit packet must have a unique sequence number.
    - The sender and receiver sides of the protocols may have to buffer more than one packet.
    - The range of sequence numbers needed and the buffering requirements will depend on the manner in which a data transfer protocol responds to lost, corrupted, and overly delayed packets. Two basic approaches toward pipelined error recovery can be identified: **Go-Back-N** and **selective repeat.**
- Utilization of a sender:

$U_{sender} = \frac{L/R}{RTT + L/R}$

## 3.4.3 Go-Back-N (GBN)

![[../../../Attachments/Untitled 14 4.png|Untitled 14 4.png]]

- In a **Go-Back-N (GBN) protocol** the sender is allowed to transmit multiple packets without waiting for an acknowledgment but is constrained to have no more than some maximum allowable number, N, of unacknowledged packets in the pipeline.
- N is often referred to as the **window size** and the GBN protocol itself is a **sliding-window protocol.**
- Sender holds a **window** of up to N, consecutive transmitted but unACKed pkts
- **Flaws:**
    - A single packet error can cause GBN to re-transmit many packets
    - To mitigate this problem, instead of using cumulative ACKs, the receiver could **individually acknowledge** specific packets as they are received
    - This is what technique is called **Selective Repeat**

## 3.4.4 Selective Repeat (SR)

![[../../../Attachments/Untitled 15 4.png|Untitled 15 4.png]]

- The receiver **individually acknowledges** all correctly received packets
    - Buffers packets, as needed, for eventful in-order delivery to the upper layer
- Sender **times-out/re-transmits individually** for unACKed packets
    - The sender maintains a timer for each unACKed packed
- Flaws:
    - Overhead is created since bits are needed to be used to keep track of the ACK packets.

# 3.5 Connection-Oriented Transport: TCP

## 3.5.1 The TCP Connection

![[../../../Attachments/Untitled 16 4.png|Untitled 16 4.png]]

- TCP implements a **reliable data transfer service**
    - Error Detection
    - Re-transmissions
    - Cumulative acknowledgments
    - Timeouts
    - Header fields for sequence numbers
    - Header fields for acknowledgment numbers
- TCP is a **connection-oriented protocol**
- TCP connection
    - **Full-duplex service**
    - **Reliable**
    - **Point-to-point**
- **Full Duplex Service**
    - It means that the data can be transmitted in both directions on a signal carrier at the same time.
    - A TCP connection provides a **full-duplex service** if there is a TCP connection between process A to process B on another host, then application layer data flows from process B to Process A.
- **Point to Point Service**
    - It means that the data can be transmitted in only one direction on a signal carrier at the same time.
- **TCP round trip time, timeout**
    - How to set TCP timeout value?
        - longer than RTT, but RTT varies
        - _too short:_ premature timeout, unnecessary retransmissions
        - _too long:_ slow reaction to segment loss

$EstimatedRTT = (1-\alpha) * EstimetedRTT + \alpha * SampleRTT \newline \alpha = 0.125$

$TimeoutInterval = EstimatedRTT + 4 * DevRTT$

$DevRTT = (1-\delta) * DevRTT + \delta * |SampleRTT - EstimatedRTT|$

### **TCP Fast retransmit**

- If the sender receives 3 additional ACKs for the same data, resend unACKed segment with the smallest seq #

### **TCP Flow Control**

- What happens if the network layer delivers data faster than the application layer removes data from socket buffers?

### **Flow Control:**

- The receiver controls the sender, so the sender won’t overflow the receiver’s buffer by transmitting too much, too fast.

### **TCP Connection Management**

- With 2-way handshake scenarios, the **half-open connection** can be faced
- TCP uses a **3-way handshake.**
    - Uses SYN and FIN bit. SYN bit for establishing and FIN bit to close the connection.

# 3.6 Principles of Congestion Control

- **Congestion:**
    - Too many sources send too much data too fast for the network to handle.
    - Manifestations:
        - Long Delays (queueing in router buffers)
        - Packet Loss (buffer overflow at routers)
- **Congestion Control vs Flow Control:**
    - Congestion Control:
        - Preventing the sender from overwhelming the network.
    - Flow Control:
        - Preventing the sender from overwhelming the receiver.
- **Cost of Congestion:**
    - More work (retransmission) for given receiver throughput
    - unneeded retransmissions: link carries multiple copies of a packet
        - decreasing maximum achievable throughput.
- **Approaches towards congestion control:**
    - **End-to-end Congestion Control:**
        - no explicit feedback from the network
        - congestion inferred from observed loss, delay
        - the approach was taken by TCP
    - **Network-assisted Congestion Control:**
        - the router provides direct feedback to sending/receiving hosts with flows through congested router
        - may indicate congestion level or explicitly set sending rate.
- **TCP congestion control: AIMD**
    - _approach__:_ senders can increase sending rate until packet loss (congestion) occurs, then decrease sending rate on loss event.
        - **Additive Increase:** Increase sending rate by 1 maximum segment size every RTT until the loss is detected.
        - **Multiplicative Decrease:** Cut sending rate in half at each loss event.
            - Cut in half on loss detected by triple duplicate ACK
            - Cut to 1 MSS (maximum segment size) when loss is detected by timeout.
    - Why AIMD?
        - AIMD - a distributed, asynchronous algorithm - has been shown to:
            - optimize congested flow rates network-wide!
            - have desirable stability properties.
- **TCP Congestion Control: Details**
    - cwnd = Congestion Window
    - TCP sender limits transmission: `LastByteSent - LastByteAcked <= cwnd`.
    - cwnd is dynamically adjusted in response to observed network congestion
    - **TCP slow start:**
        - When the connection begins, increase the rate exponentially until the first loss event:
            - initially **cwnd** = 1 MSS
            - double **cwnd** every RTT
            - done by incrementing **cwnd** for every ACK received
        - The initial rate is slow, but ramps exponentially fast.
    - When should the exponential increase switch to linear?
        - when cwnd gets to 1/2 of its value before timeout.
        - **Implementation:**
            
            ![[../../../Attachments/Untitled 17 4.png|Untitled 17 4.png]]
            
            - variable **ssthresh**
            - on loss event, **ssthresh** is set to 1/2 of cwnd just before the loss event
- **TCP Fairness**
    - **Fairness goal:** if k TCP sessions share the same bottleneck link of bandwidth R, each should have an average rate of R/K