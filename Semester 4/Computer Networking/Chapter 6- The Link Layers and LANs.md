The Link Layer: The basic Service of any link layer is to move a datagram from one node to an adjacent node over a single communication link.

MAC (Medium Access Control) and LLC (Logical Link Control) are the two sublayers of the Data Link layer.

Where is the Link Layer implemented?

- Most of the Link Layer is typically implemented in hardware
- High-level functionalities may be implemented in software that runs on the host’s CPU

Types of Communication Links

- Point-to-point communication link
- Broadcast Channel
- Unidirectional
    - Simplex
- Bidirectional
    - Full-duplex
    - Half-duplex

Data link Layer

- Basic Service of any link layer:
    - Move a datagram
    - from one node to an adjacent node
    - over a single communication link
- Actual service provided can vary widely across different link-layer protocols

Basic Services provided by the Link Layer:

- Framing
- Link Access
- Reliable Delivery
- Error correction and detection

The Multiple access problem:

- Problem: Multiple nodes share a single broadcast domain
- Solution: MAC protocol that coordinates the transmission of data link frames from different nodes. (There exists many different MAC protocols)
- Ideal Characteristics of a MAC protocol:
    - When only one node has data to send, that node has a throughput of R bps, whereas R is the channel rate
    - When N nodes have data to send, each node has an average transmission rate of R/N bps.
    - There is no primary node that represents a single point of failure for the network (decentralized operation)
    - Inexpensive and simple to implement

Types of multiple access protocol

- Channel partitioning protocols
    - TDM
        - Time-division multiplexing (TDM)
    - FDM and CDMA
        - Frequency-division multiplexing (FDM)
- Taking-turns protocols
    - Polling protocols
    - Token-passing protocols
- Random access protocols
    - Transmitting nodes always send a full rate R bps
    - If there is a collision, a back-off mechanism is used to decide when to retransmit
    - Example of random access protocols
        - ALOHA
        - Slotted ALOHA
        - CSMA/Cd
        - Ethernet

ALOHAnet

- Built to connect users on Hawaiian islands with central computer on the main Oahu campus
- Using cheap radio equipment
- (Telephone costs were high)
- Setup:
    - One Host
    - Many client machines
    - Downlink from host to clients uses frequency f1
    - Uplink from clients to host uses frequency f2
- Example:
    - If nodes has frame to send: Send
    - When transmission of current frame completed:
        - Received acknowledgment message (ACK) from hub?
            - YES → DONE
            - NO → There was a collision/error
        - IF no ACK received:
            1. With probability p: Retransmit immediately
            2. With probability (1-p): Wait another frame period, then try again.