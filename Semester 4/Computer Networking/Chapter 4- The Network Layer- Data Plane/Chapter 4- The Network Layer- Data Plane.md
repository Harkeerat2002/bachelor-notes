# 4.1 Introduction

- **Network-Layer Services and Protocols**
    - Transport Segment from sending to receiving host:
        - **Sender:** encapsulates segments into datagrams, passes to link layer
        - **Receiver:** delivers segments to transport layer protocol
    - network layer protocols in **every Internet device:** hosts, routers
    - **Routers:**
        - examines header fields in all IP datagrams passing through it.
        - Moves datagrams from input ports to output ports to transfer datagrams along the end-end path
- **Two Key network-layer functions**
    - **Forwarding:** move packets from a router’s input link to the appropriate router output link
    - **Routing:** determine the route taken by packets from source to destination
        - routing algorithm
- **Network Layer: Data Plane, Control Plane**
    - **Data Plane:**
        - **local,** per-router function
        - determines how the datagram arriving on the router input port is forwarded to the router output port
    - **Control Plane:**
        - **network-wide** logic
        - determines how the datagram is routed among routers along the end-end path from source host to destination host
        - two control-plane approaches:
            - **traditional routing algorithms:** implemented in routers
                - Individual routing algorithm components in each and every router interact in the control plane.
            - **software-defined networking (SDN):** implemented in (remote) servers
                - The remote controller computer, and installs forwarding tables in routers
- The Internet provides the **best-effort service.**

# 4.2 Virtual Circuit and Datagram Networks

![[../../../Attachments/Untitled 37.png|Untitled 37.png]]

- **Input Port Functions**
    
    ![[../../../Attachments/Untitled 1 11.png|Untitled 1 11.png]]
    
- **Longest Prefix Matching**
    
    - When looking for a forwarding table entry for the given destination address, use the **longest** address prefix that matches the destination address.
    
    ![[../../../Attachments/Untitled 2 9.png|Untitled 2 9.png]]
    

![[../../../Attachments/Untitled 3 7.png|Untitled 3 7.png]]

- **Switching Fabrics**
    - Transfer packet from input link to appropriate output link
    - **Switching rate:** the rate at which packets can be transferred from inputs to outputs
        - often measured as multiple input/output line rate
        - N inputs: switching rate N times line rate desirable
    - Three major types of switching Fabrics
        
        ![[../../../Attachments/Untitled 4 6.png|Untitled 4 6.png]]
        
        - **Memory**
            - copied to an intermediate memory
        - **Bus**
            - Datagram goes from input port memory to output port memory via a bus.
        - **Interconnection Network**
            - Multiple Packets can be transferred at the same time.
- **Input Port Queuing**
    
    ![[../../../Attachments/Untitled 5 6.png|Untitled 5 6.png]]
    
- **Output Port Queuing**

![[../../../Attachments/Untitled 6 6.png|Untitled 6 6.png]]

- **Buffer Management**
    - **Drop:** which packed to add, drop when buffers are full
        - **Tail Drop:** drop the arriving packet
        - **Priority:** drop/remove on a priority basis
    - **Marking:** which packets to mark to signal congestion
- **Packet Scheduling: FCFS**
    - Packed Scheduling: deciding which packet to send next on the link
        - **First Come, First Served**
        - **Priority**
            - Arriving traffic classified, queued by class
        - **Round Robin**
            - Arriving traffic classified, queued by class
            - The server cyclically, and repeatedly scans class queues, sending one complete pack from each class.
        - **Weighted Fair Queueing**
            - Generalized Round Robin
            - Each class, i, has weight, wi, and gets the weighted amount of service in each cycle
            - Minimal Bandwidth Guaranteed.

# 4.3 What’s Inside a Router?

- **What’s a Subnet?**
    - device interfaces that can physically reach each other without passing through an intervening router

# 4.4 The Internet Protocol

### Obtaining a Host Address: The Dynamic Host Configuration Protocol

- **DHCP** allows a host to obtain (be allocated) an IP address automatically.

# NAT: Network Address Translation

**NAT:** all devices in a local network share just **one** IPv4 address as far as the outside world is concerned.