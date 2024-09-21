# Table of Contents

---

Table of Contents

2.1 Principles of Network Applications

2.1.1 Network Application Architectures

Client-Server Architecture

P2P Architecture

2.1.2 Processes Communicating

Client and Server Processes:

The Interface Between the Process and the Computer Network:

Addressing Processes

2.1.3 Transport Services Available to Applications

Reliable Data Transfer

Throughput

Timing

Security

2.1.4 Transport Services Provided by the Internet

TCP Service

UDP Service

2.1.5 Application-Layer Protocols

Open vs Proprietary Protocols

2.2 The Web and HTTP

2.2.1 Overview of HTTP

2.2.2 Non-Persistent and Persistent Connections

2.2.3 HTTP Message Format

HTTP response time: Non-persistent Connection

HTTP response time: Persistent HTTP Connection

HTTP 1.1 Pipe-lining

Problem with HTTP/1.1 persistent connections

2.2.4 User-Server Interaction: Cookies

First-part vs Third-party Cookies

2.2.5 Web Caching

2.4 Electronic Mail on the Internet

2.4.1 SMTP

2.4.2 Comparison with HTTP

2.5 DNS — The Internet’s Directory Service

2.5.1 Services Provided by DNS

2.5.2 Overview of How DNS works

A Distributed, Hierarchical Database

DNS Caching

2.5.3 DNS Records and Messages

2.6 Peer-to-Peer Applications

2.6.1 P2P File Distribution

BitTorrent

P2P file distribution using BitTorrent

---

# 2.1 Principles of Network Applications

- In the web application there are two distinct programs that communicate with each other:
    - The browser program running in the user’s host (desktop, laptop, tablet, smartphone, and so on)
    - The web server program running in the web server host.
- When developing your new application, you need to write software that will run on multiple end systems.

![[../../../Attachments/Untitled 35.png|Untitled 35.png]]

Communication for a network application takes place between end systems at the application layer

- Creating a **network application** means writing **programs** that run on (different) end system and **communicate** over the network
- For instance, a web server software communicates with browser software

## 2.1.1 Network Application Architectures

- From the application developer's perspective, the network architecture is fixed and provides a specific set of services to applications.
- The **application architecture,** on the other hand, is designed by the application developer and dictates how the application is structured over the various end system.
- In choosing the application architecture, an application developer will likely draw on one of the two predominant architectural paradigms used in modern network applications:
    - Client-server Architecture
    - Peer-to-Peer (P2P) architecture

### Client-Server Architecture

![[../../../Attachments/Untitled 1 9.png|Untitled 1 9.png]]

Client-server Architecture

- There is an always-on host, called the **server**, which services requests from many other hosts, called **clients.**
- When a web server receives a request for an object from a client host, it responds by sending the requested object to the client host.
    - Note that with the Client-server architecture, clients do not directly communicate with each other; for example, in the web application, two browsers do not directly communicate.
- **Server:**
    - Always-on host
    - Permanent IP address
    - Data Centers for scaling
- **Clients:**
    - Communicate with server
    - May be intermittently connected
    - May have dynamic IP addresses
    - Do not communicate directly with each other

### P2P Architecture

![[../../../Attachments/Untitled 2 7.png|Untitled 2 7.png]]

Peer-to-Peer Architecture

- No always-on server
- Arbitrary end systems directly communicate
- Peers request service from other peers, provide service in return to other peers
    - Self scalability: New peers bring new service capacity, as well as new service demands
- Peers are intermittently connected and change IP addresses
    - Complex management

## 2.1.2 Processes Communicating

- A **process** is a program running within an end system
- Within the same host, two processes communicate using **inter-process communication** (define by OS)
- Processes in different hosts communicate by exchanging **messages**

### **Client and Server Processes:**

- A **client process** is the process that initiates communication
- A **server process** is the process that waits to be contacted
- Example:
    - With the Web, a browser is a client process and a Web server is a server process

### **The Interface Between the Process and the Computer Network:**

- Most applications consist of pairs of communicating processes, with the two processes in each pair sending messages to each other.
- Any message sent from one process to another must go through the underlying network.
- A process sends messages into, and receives messages from, the network through a software interface called a **socket.**

![[../../../Attachments/Untitled 3 5.png|Untitled 3 5.png]]

Application processes, sockets, and underlying transport protocol

- The above figure shows socket communication between two processes that communicate over the Internet.
- As shown in this figure, a socket is the interface between the application layer and the transport layer within a host.
- It is also referred to as the **Application Programming Interface (API)** between the application and the network, since the socket is the programming interface with which network applications are built.
- The application developer has control of everything on the application-layer side of the socket but has little control of the transport-layer side of the socket.
- The only control that the application developer has on the transport-layer side is:
    - the choice of transport protocol
    - perhaps the ability to fix a few transport-layer parameters such as maximum buffer and maximum segment sizes

### **Addressing Processes**

- To receive messages, the process must have an identifier
- Host device has unique IP address
    - 32 bits (IPv4); 128 bits (IPv6)
- Many processes can be running on same host, thus, IB address does not suffice to identify destination process
- Identifier includes both IP address and the **port number** associated with process on host.
- Example port numbers:
    - HTTP server: 80
    - Mail server: 25

## 2.1.3 Transport Services Available to Applications

- Many networks, including the Internet, provide more than one transport-layer protocol.
- When an application is being developed, one must choose one of the available transport-layer protocols.
- In order to choose one, one would need to see which services provided by the available transport-layer protocols provides the best match which the application needs
- The possible services can be classified along four dimensions:
    - **Reliable Data Transfer**
    - **Throughput**
    - **Timing**
    - **Security**

### **Reliable Data Transfer**

- Transport Service may need to provide a reliable data transfer
- A guarantee that the data sent by one end of the application is delivered correctly and completely to the other end of the application.
- If a protocol provides such a guaranteed data delivery service, it is said to provide **reliable data transfer.**
- Some applications (e.g., audio) can tolerate some loss
    - **Loss-tolerant** applications
- Other applications (e.g., file transfer, web transactions) require 100% reliable data transfer
    - Need a **reliable data transfer**

### **Throughput**

- A transport service may need to provide guaranteed available throughput at some specific rate
    - Some applications require a minimum amount of throughput to be “effective”
    - Other applications — called **elastic** applications — make use of whatever throughput they get.

### **Timing**

- A transport service may need to provide timing guarantees available throughput at some specified rate
    - Some applications (e.g., Internet Telephony, interactive games) require low delay to be “effective”

### **Security**

- A transport service may need to provide an application with one or more security services
    - Encryption, data integrity ...

## 2.1.4 Transport Services Provided by the Internet

- The Internet makes two transport protocols available to applications, UDP and TCP.
- Each of these protocols offers a different set of services to the invoking applications.

![[../../../Attachments/Untitled 4 4.png|Untitled 4 4.png]]

Requirements of selected network applications

### **TCP Service**

- Connection-oriented Service
- Reliable Transport between sending and receiving process
- Flow Control
    - The sender won’t overwhelm the receiver
- Congestion Control
    - Throttle sender when network overloaded
- TCP does NOT provide
    - Timing, minimum throughput guarantee, security

### **UDP Service**

- Unreliable data transfer between sending and receiving process
- Does NOT provide
    - Reliability, flow control, congestion control, timing, throughput guarantee, security, or connection setup.

  

![[../../../Attachments/Untitled 5 4.png|Untitled 5 4.png]]

Popular Internet applications, their application-layer protocols, and their underlying transport protocols

## 2.1.5 Application-Layer Protocols

- An **application-layer protocol** defines how an application’s processes, running on different end systems, pass messages to each other.
- In particular, an application-layer protocol defines:
    - The types of messages exchanged, for example, request messages and response messages
    - The syntax of the various message types, such as the fields in the message and how the fields are delineated
    - The semantics of the fields, that is, the meaning of the information in the fields
    - Rules for determining when and how a process sends messages and responds to messages

### Open vs Proprietary Protocols

- Open Protocols:
    - Defined in RFCs
    - Allows for interoperability
    - e.g., HTTP, SMTP
- Proprietary Protocols
    - E.g., Skype

# 2.2 The Web and HTTP

## 2.2.1 Overview of HTTP

- Until the early 1990s the Internet was mainly used to connect academic institutions.
- In 1994, a new application was born: the World Wide Web (www)
- A web page consists of objects
- Objects can be HTML files, JPEG images, Java applets, audio files, etc.
- A web page consists of base **HTML file,** which includes several **referenced objects**
- Each object is addressable by a **Uniform Resource Locator (URL)**
- **Uniform Resource Locator (URL)**
    - A URL is a “reference to a Web resource that specified its **location** on a computer network and a **mechanism** for retrieving it”

![[../../../Attachments/Untitled 6 4.png|Untitled 6 4.png]]

Addressing objects on a Web page

- The client and the server talk to each other by exchanging **HTTP messages**
- The **HyperText Transfer Protocol (HTTP)** is the Web’s application-layer protocol

![[../../../Attachments/Untitled 7 4.png|Untitled 7 4.png]]

HTTP request-response behavior

- HTTP relies on a Client/Server Model
    - **Client:**
        - Browser that requests, receives, (using HTTP protocol) and “displays” Web objects
    - **Server:**
        - Web server sends (using HTTP protocol) objects in response to requests
- HTTP uses TCP as its underlying transport protocol.
    - Client initiates TCP connection (creates socket) to server
    - Server accepts TCP connection from client
    - HTTP messages (application-layer protocol messages) exchanged between browser (HTTP client) and Web server (HTTP server)
    - TCP connection closed
- HTTP is stateless
    - HTTP server maintains no information about past clients requests
    - Protocols that, in contrast to HTTP, maintain “state” are complex

## 2.2.2 Non-Persistent and Persistent Connections

|   |   |
|---|---|
|**Non-persistent HTTP**|**Persistent HTTP**|
|At most one object sent over TCP connection.|Multiple objects can be sent over single TCP connection between client, server|
|Connection then Closed||
|Downloading multiple objects, required multiple connections||

**HTTP with Non-persistent Connections**

![[../../../Attachments/Untitled 8 4.png|Untitled 8 4.png]]

- **Round-Trip Time:**
    - It is the time it takes for a small packet to travel from client to server and then back to the client
    - Time for a small packet to travel from client to server and back
    - The RTT includes packet-propagation delays, packet-queuing delays in intermediate routers and switches, and packet-processing delays.

![[../../../Attachments/Untitled 9 4.png|Untitled 9 4.png]]

The back-of-the-envelope calculation for the time needed to request and receive an HTML file

- HTTP response time
    - One RTT to initiate TCP connection
    - One RTT for HTTP request and first few bytes of HTTP response to return
- File Transmission Time
    - Non-persistent HTTP response time = 2 RTT + File Transmission time

**HTTP with Persistent Connections**

- Non-persistent HTTP issues
    - Require 2 RTTs per object
    - OS overhead for each TCP connection
    - Browsers often open parallel TCP connections to fetch referenced objects.
- Persistent HTTP
    - Server leaves connections open after sending response
    - Subsequent HTTP messages between same client/server sent over open connection
    - Client sends requests as soon as it encounters a referenced object
    - As little as one RTT for all the referenced objects

## 2.2.3 HTTP Message Format

- HTTP specification [RFC 1945; RFC 2616] include the definitions of the HTTP message formats.
- Two types of HTTP messages:
    - **Request** messages
    - **Response** messages

![[../../../Attachments/Untitled 10 4.png|Untitled 10 4.png]]

General format of an HTTP request message

![[../../../Attachments/Untitled 11 4.png|Untitled 11 4.png]]

HTTP Request Message: Example

**Method Types:**

- HTTP/1.0:
    - GET
    - POST
    - HEAD
        - Ask server to leave requested object out of response
- HTTP/1.1
    - GET
    - POST
    - HEAD
    - PUT
        - Uploads file in entity body to path specified in URL field
    - DELETE
        - Deletes file specified in the URL field

**Uploading Form Input**

- POST method
    - Web page often includes form input
    - Input is uploaded to server in entity body
- URL method
    - Uses GET method
    - Input is uploaded in URL field of request line

**HTTP Response Message**

![[../../../Attachments/Untitled 12 3.png|Untitled 12 3.png]]

General Format of an HTTP response message

- Status code appears in 1st line n server-to-client response message
- Sample Codes:
    - 400 Bad Request
    - 404 Not Found
    - 505 HTTP version Not Supported

### **HTTP response time: Non-persistent Connection**

Non-persistent connection, 1 object:

$\triangle_{np} = 2RTT + T_{tx}$

Non-persistent connection, 2 objects:

$\triangle_{np} = 2 \times (2RTT + T_{tx})$

Non-persistent connection, N objects:

$\triangle_{np} = N \times (2RTT + T_{tx})$

### **HTTP response time: Persistent HTTP Connection**

- HTTP 1.1 introduced multiple **pipelines GETs** over a single TCP connection
- The server responds **in-orders** (FCFS: first-come-fist-served scheduling) to GET requests

Persistent connection, 1 object:

$\triangle_{per} = RTT + RTT + T_{tx} $

Persistent connection, 2 objects:

$\triangle_{per} = RTT + 2(RTT + T_{tx} )$

Persistent connection, N objects:

$\triangle_{per} = RTT + N(RTT + T_{tx} )$

### HTTP 1.1 Pipe-lining

- It allows multiple HTTP requests to be sent over a single TCP connection without waiting for the corresponding responses.
- HTTP/1.1 specification requires servers to respond to pipelined requests correctly sending back non-pipelined but valid responses even if server does not support HTTP pipelining.

![[../../../Attachments/Untitled 13 3.png|Untitled 13 3.png]]

![[../../../Attachments/Untitled 14 3.png|Untitled 14 3.png]]

### Problem with HTTP/1.1 persistent connections

- In HTTP 1.1’s the server responds in order to GET requests
    - With FCFS, the small object may have to wait for transmission behind large object(s)
    - Also, loss recovery (retransmitting lost TCP segments) stalls object transmission
- This is known as the **head-of-line (HOL) blocking** problem
- HTTP/2 mitigates the HOL blocking problem
    - It increases the flexibility at server in sending in sending objects to client

## 2.2.4 User-Server Interaction: Cookies

- It is often desirable for a Web site to identify users, either because the server wishes to restrict user access or because it wants to serve content as a function of the user identity.
- For these purposes, HTTP uses cookies.
- **Cookies** allow sites to keep track of users.

![[../../../Attachments/Untitled 15 3.png|Untitled 15 3.png]]

Keeping user state with cookies

- Four Components:
    1. Cookie header line of HTTP response message
    2. Cookie header line in next HTTP request message
    3. Cookie file kept on user’s host, managed by user’s browser
    4. Back-end database at Web site
- Common uses of Cookies
    - Authorization
    - Shopping Carts
    - Recommendations
    - User Session State (Web e-mail)

### First-part vs Third-party Cookies

- **First-party Cookies:** They are stored by the domain (website) you are visiting directly, They allow website owners to collect analytics data, remember language settings, and perform other useful functions that help provide a good user experience
- **Third-party Cookies:** They are created by domains other than the one you are visiting directly, hence the name third-party. They are used for cross-site tracking, re-targeting and ad-serving

## 2.2.5 Web Caching

- A **Web cache** — also called a **proxy server** — is a network entity that satisfies HTTP requests on the behalf of an origin Web server.
- The web cache has its own disk storage and keeps copies of recently requested objects in this storage

![[../../../Attachments/Untitled 16 3.png|Untitled 16 3.png]]

Clients requesting objects through a Web Cache

- As seen above a user’s browser can be configured so that all of the user’s HTTP requests are first directed to the Web cache
- **Goal:**
    - Satisfy client request without involving origin server
- The browser sends all HTTP requests to the cache
    - Object in cache: cache returns object
    - Else cache requests object from origin server, then returns object to client
- The cache acts as both client and server
    - Server for original requesting client
    - Client to origin server
- **Why Web Caching?**
    - Reduce response time for client request
    - Reduce traffic on an institution's access link to the Internet.
- **Problem of Caching**
    - Caching can reduce user-perceived response times and reduce overall network traffic
    - But caching introduces a new problem: Objects in the cache may be **stale.** In order words, the object housed in the Web server may have been modified since the copy was cached at the client.
    - HTTP can verify that an object is up-to-date using the **conditional GET**
- **Conditional GET**
    - An HTTP request message is a so-called conditional GET message if
        - The request message uses the GET method and,
        - The request message includes an **If-Modified-Since:** header line

# 2.4 Electronic Mail on the Internet

- E-mail - Electronic Mail
- Asynchronous communication medium, people send and read messages when it is convenient for them, without having to coordinate with other people’ schedules.
- Fast, easy to distribute, and inexpensive

![[../../../Attachments/Untitled 17 3.png|Untitled 17 3.png]]

A high-level view of the Internet e-mail system

- As seen from the above diagram it has three major components: **user agents, mail servers,** and the **Simple Mail Transfer Protocol (SMTP).**
- **User-Agents:**
    - It allows users to read, reply to, forward, save, and compose messages.
    - The user agent also retrieves the message from his mailbox in his mail server
- **Mail Servers**
    - Each recipient has a **mailbox** located on one of the mail servers.
    - Mailbox manages and maintains the messages that have been sent.
    - A typical message starts its journey in the sender’s user agent, travels to the sender’s mail server, and travels to the recipient’s mail server, where it is deposited in the recipient’s mailbox
    - When someone wants to access the messages in his mailbox, the mail server containing his mailbox authenticates him (with usernames and passwords)
- **SMTP**
    - It is the principal application-layer protocol for Internet electronic mail.
    - It uses the reliable data transfer service of TCP to transfer mail from the sender’s mail server to the recipient’s mail server.
    - SMPT has two sides
        - **Client Side**
            - Executes on the sender’s mail server
        - **Server Side**
            - Executes on the recipient’s mail server
    - When a mail server sends mail to other mail servers, it acts as an SMPT client
    - When a mail server receives mail from other mail servers, it acts as an SMTP server.

## 2.4.1 SMTP

- Uses TCP to reliably transfer email messages from client to server
- Direct transfer: sending server to receiving server
- Three phases of transfer
    - Handshaking
    - Transfer of messages
    - Closure

![[../../../Attachments/Untitled 18 3.png|Untitled 18 3.png]]

Alice sends a message to Bob

## 2.4.2 Comparison with HTTP

- SMTP: push / HTTP: pull
- Both have ASCII command/response interaction, status codes
- HTTP: Each object encapsulated in its own response message
- SMTP: Multiple objects sent in a multipart message

# 2.5 DNS — The Internet’s Directory Service

- One identifier for a host is its **host-name.** Host-names — such as cnn.com, [www.yahoo.com](http://www.yahoo.com) — are mnemonic.
- Host-names provide little, if any, information about the location within the Internet of the host.
- Furthermore, because host-names can consist of variable length alphanumeric characters, they would be difficult to process by routers .
- For these reasons hosts are also identified by so-called **IP addresses**
- AN IP address is hierarchical because as we scan the address from left to right, we obtain more and more specific information about where the host is located in the Internet.

## 2.5.1 Services Provided by DNS

![[../../../Attachments/Untitled 19 3.png|Untitled 19 3.png]]

- A directory service is needed that translates host names to IP addresses.
- This is the main task of the Internet’s **domain name system (DNS).**
- The DNS is:
    - a distributed database implemented in a hierarchy of **DNS servers.**
    - an application-layer protocol that allows hosts to query the distributed database.
- DNS provides a few other important services in addition to translating host-names to IP addresses:
    - **Host Aliasing:**
        - A host with complicated host-name can have one or more alias names.
    - **Mail Server Aliasing:**
        - It is highly desirable that e-mail addresses be mnemonic. For example, if Bob has an account with Hotmail, Bob’s e-mail address might be as simple as bob@hotmail.com. However, the host-name of the Hotmail mail server is more complicated and much less mnemonic.
    - **Load Distribution**
        - If a Web server is busy it can then rotate the IP addresses to reduce the load.

## 2.5.2 Overview of How DNS works

- Suppose that some application running in a user’s host needs to translate a host-name to an IP address.
- The application will invoke the client side of DNS, specifying the host-name that needs to be translated.
- DNS in the user’s host then takes over, sending a query message into the network.
- Then the DNS in the user’s host receives a DNS reply message that provides the desired mapping.
- The problem with this centralized design
    - **A single point of failure:** If the DNS server crashes, so does the entire Internet
    - **Traffic Volume:** A single DNS server would have to handle all DNS queries
    - **Distant Centralized Database:** A single DNS server cannot be “close to” all the querying clients
    - **Maintenance:** The single DNS server would have to keep records for all Internet hosts.

### A Distributed, Hierarchical Database

- In order to deal with the issue of scale, the DNS uses a large number of servers, organized in a hierarchical fashion and distributed around the world.
- No single DNS server has all of the mappings for all of the hosts in the Internet, the mappings are distributed across the DNS servers.

![[../../../Attachments/Untitled 20 3.png|Untitled 20 3.png]]

Portion of the hierarchy of DNS servers

- There are three classes of DNS servers:
    - **Root DNS Servers**
        - In the Internet there are 13 root DNS servers, most of which are located in North America.
    - **Top-level Domain (TLD) DNS servers**
        - These servers are responsible for top-level domains such as com, org, net, and all of the country top-level domains.
    - **Authoritative DNS Servers**
        - Every organization with publicly accessible hosts on the Internet must provide publicly accessible DNS records that map the names of those hosts to IP addresses.
- There is another important type of DNS server called the **local DNS server.**
- **Local DNS Server**
    - A local DNS server does not strictly belong to the hierarchy of servers but is nevertheless central to the DNS architecture.
    - Each ISP — such as a university, an academic department, an employee’s company, or a residential ISP — has a local DNS server.
    - When host makes DNS query, query is first sent to its local DNS server
    - The local DNS server has local cache of recent name-to-address translation pairs

![[../../../Attachments/Untitled 21 3.png|Untitled 21 3.png]]

Interaction of the various DNS servers

### DNS Caching

- In a query chain, when a DNS server receives a DNS reply, it can cache the mapping in its local memory.
- It is used extensively by the DNS system to reduce delays.
- Cached entries may be **out-of-date**

## 2.5.3 DNS Records and Messages

- The DNS servers that together implement the DNS distributed database store **resource records (RRs)**, including RRs that provide host-name-to-IP address mappings.

# 2.6 Peer-to-Peer Applications

- Two different applications that are particularly well suited for P2P designs:
    - **File Distribution**, where the application distributes a file from a single source to a large number of peers.
    - **Database Distributed**

## 2.6.1 P2P File Distribution

- Considering a very natural application, namely, distribution a large file from a single server to a large number of hosts (called peers)
- In client-server file distribution, the server must send a copy of the file to each of the peers — placing an enormous burden on the server and consuming a large amount of server bandwidth.
- In P2P file distribution, each peer can redistribute any portion of the file it has received to any other peers, thereby assisting the server in the distribution process.

### BitTorrent

- It is a **communication protocol** for **peer-to-peer file sharing,** which enables users to distribute data and electronics files over the Internet in a decentralized manner.

### P2P file distribution using BitTorrent

- File divided into 256 KB chunks
- Peers in torrent send/receive file chunks
- Tracker sends to Alice the IP addresses of peers that can share the file chunks
- Alice establishes concurrent TCP connections with these peers
- A new peer joining torrent
    - has no chunks, but will accumulate them over time from other peers;
    - registers with tracker to get list of peers, connects to subset of peers (”neighbors”)
- While downloading, peer uploads chucks to other peers
    - Peer may change peers with whom it exchanges chunks
    - Churn: peers may come and go
    - Once peer has entire file, it may leave or remain in torrent.