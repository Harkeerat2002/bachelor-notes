# Computer Systems Organization

## Error-Correcting Codes

Computer memories can make errors occasionally due to voltage spikes on the power line or other causes. To guard against such errors, some memories use error-detecting or error-correcting codes. When these codes are used, extra bits are added to each memory word in a special way. When a word is read out of the memory, the extra bits are check to see if an error has occurred.

# The Digital Logic Level

## CPU Chips:
- Each CPU chip as a set of pins, through which all its communication with the outside world must take place
- Some pins output signals from the CPU to the outside world; others accept signals from the outside world; some can do both.
- The pins on a CPU chip can be divided into three types:
    - _address_,
    - _data_
    - _control_
- The above type of pins are connected to similar pins on the memory and I/O devices via a collection of parallel wires called a bus.

### Procedure to Fetch Instruction

- The CPU first puts the memory address of that instruction on its address pins.
- Then it asserts one or more control lines to inform the memory that it wants to read.
- the memory replies by putting the request word on the CPU’s data pins and asserting a signal saying that it is done.
- When the CPU sees this signal, it accepts the word and carries out the instruction.
- Hence the basic concept is that, CPU communicates with the memory and I/O devices by presenting signals on its pins and accepting signals on its pins.

### Performance of CPU

- Two of the key parameters that determine the performance of a CPU are:
    - Number of Data pins
    - number of address pins
- A chip with _m_ address pins can address up to $2^m$﻿ memory locations.
- A chip with _n_ data pins can read or write an _n_-bit word in a single operation.

### Control Pins

- Each CPU has some control pins in addition to address and data pins.
- The control pins regulate the flow and timing of data to and form the CPU and have other miscellaneous uses.
- The control pins can be roughly grouped into the following major categories:
    1. Bus Control
    2. Interrupts
    3. Bus Arbitration
    4. Coprocessor Signaling
    5. Status
    6. Miscellaneous

![[../../../Attachments/Untitled 3 20.png|Untitled 3 20.png]]

| **Bus Control** | These pins are mostly outputs from the CPU to the bus, telling whether the CPU wants to read or write the memory or do something else. |
| ---- | ---- |
| **Interrupts** | These pins are inputs from I/O devices to the CPU. In most systems, the CPU can tell an I/O device to start an operation and then go off and do something else while the I/O device is doing its work |
| **Bus Arbitration** | These pins are needed to regulate traffic on the bus, in order to prevent two devices from trying to use it at the same time. |
| **Miscellaneous** | These pins differ from the pin to pin. Some of these pins provide status information or some other stuff |

## Computer Buses:

- A **bus** is a common electrical pathway between multiple devices.
- They can be used internal to the CPU to transport data to and from the ALU, or external to the CPU, to connect it to memory or to I/O devices.

### Passive and Active Buses

- Some devices that attach to a bus are active and can initiate bus transfer, whereas others are passive and wait for requests.
- The active ones are called masters; the passive ones are called slaves.
    - When the CPU orders a disk controller to read or write a block, the CPU is acting as a master and the disk controller is acting as a slave.

**Bus Driver, Bus Receiver and Bus Transceiver:**

- The binary signals that computer devices output are frequently too weak to power a bus, especially if it is relatively long or has many devices on it.
- This is why most bus master are connected to the bus by a chop called a **bus driver**, which is essentially a digital amplifier.
- Similarly, most slaves are connected to the bus by a **bus receiver.**
- For devices that can act as both master and slave, a combined chip called a **bus transceiver** is used.

## Bus Clocking:

There are two types of Buses:

- **Synchronous Bus**
- **Asynchronous Bus**

### Synchronous Bus

A synchronous bus governs all communication on the bus by utilizing a synchronous clock.

**Advantages:** Simple to implement and fast

**Disadvantages:** Same clock rate for all devices and clock skew limits the bus length.

---

### Asynchronous Bus

Asynchronous bus has no clock so the data transfer happens when a device is ready.

**Advantages:** No clock skew, so it can have an arbitrary length. Supports all devices (no common clock needed)

**Disadvantages:** Slow and complex to implement

  

## Bus Arbitration:

- For I/O chips to read and write in the memory, they have to become the bus master, and also to cause interrupts.
- **Bus arbitration** mechanism is needed to prevent the chaos of two devices wanting to become bus master at the same time.

### Centralized Bus Arbitration:

There are **3** types of centralized bus arbitration:

1. **Centralized Bus Arbitration 1:**

Centralized because it has an arbiter and has lines that go from and to all devices. There is a grant line and a request line. If a device wants to talk it will assert (high 1 or low 0) on the bus and the arbiter sees that. Arbiter checks if the bus is free and gives access. It gives the access to first and second and third until it gets to the device that needs access after-which it stops the passing access further and sends the data. The cycle then repeats. This process is also called as **daisy chaining.**

![[../../../Attachments/Untitled 17.png]]

1. **Centralized Bus Arbitration 2:**

The same thing happens in this case but we have each device being wired to request 1 or request 2 and the arbiter sees request with different priority. SO the arbiter can assert the grant based on the level or the priority.

![[../../../Attachments/Untitled 18.png]]

1. **PCI:**

On this version we have a more elaborate system where the arbiter is wired to every single device and the arbiter can chose the device with different priority which allows for more flexibility.

![[../../../Attachments/Untitled 19.png]]

### Decentralized Bus Arbitration:

There is only **1** type of decentralized bus arbitration

- We can get by without the arbiter where there is always a granted bus. They all are connected to the bus request line. Since we have no centralized arbiter there is a busy line which shows if the bus is busy or not.

![[../../../Attachments/Untitled 20.png]]

# Interfacing:

A typical small to medium-sized computer system consists of a CPU chip, memory chips, and some I/O controllers, all connected by a bus. I/O chips are chips through which the computer communicates with the external world.

## Address Decoding

- The PIO can be selected in one of the two ways:
    - as a true I/O device
    - as part of explicitly bus line that indicated that an I/O device is being referenced, rather than memory

### Memory-Mapped I/O:

- If memory mapped I/O is used than it must be assigned a 4 bytes of the memory space for the three ports and the control register.

  

# The Microarchitecture Level:

The level above the digital logic level is the microarchitecture level. Its job is to implement the ISA (Instruction Set Architecture) level depends on the ISA being implemented, as well as the cost and performance goals of the computer.

## MIC1

- This example of the micro-architecture includes the subset of the Java Virtual Machine.
- The goal is to create the Micro-architecture that runs and executes IJVM.
- This subset contains only integer instructions, so this is we it is names as **IJVM**.
- This micro-architecture will contain a micro-program (in ROM), whose job is to _fetch, decode_ and _execute IJVM instruction._
- The micro-program has a set of variables, called the **state** of the computer, which can be accessed by all the functions.
- IJVM instructions are short and sweet. Each instructions has a few fields, usually one or two, each of which has some specific purpose.
    
    - **Opcode (Operation Code):** Identifies the instruction, telling whether it is an ADD or BRANCH, or something else.
    - **Additional Field:** Many instructions have additional field, which specifies the operand. For example, instructions that access a _local variables_ need a field to tell which variable.
    
    This Model of execution, sometimes called the **fetch-execute cycle.**
    

### The Data Path

The **data path** is that part of the CPU containing the ALu, its inputs, and its outputs.

![[../../../Attachments/Untitled 28.png|Untitled 28.png]]

|   |   |
|---|---|
|**PC (Program Counter)**|It indicates the memory location containing the next function to be executed.|
|**SP (Stack Pointer)**|Points to the Top of the Stack.|
|**MDR (Memory Data Register)**|One of the ways to communicate with memory, and it controls the 32-bit port.|
|**MAR (Memory Address Register)**|It contains word addresses, so that the values 0, 1, 2, etc., refer to the consecutive words. Putting a 2 in MAR and starting a memory read will read out bytes 8 - 11 from memory and put them in MDR|
|**PC (Program Counter)**|It contains the byte addresses, so that the values 0, 1, 2, etc. refer to consecutive bytes. Thus putting a 2 in PC and starting a memory read will read out byte 2 from memory and put it in the low-order 8 bits of MBR|
|**H (Holding Register)**|Holds the left input for the ALU.|

- The data path for MIC1 contains a number of 32-bit registers.
- These registers are only accessible at the micro-architecture level (by micro-program).
- Most registers can drive their contents onto the B bus.
- Each of these register are driven by one or two **control signals.**
- The output of the ALU drives the **shifter** and then the C bus, whose value can be written into one or more registers at the same time.
- The **ALU’s** function is determined by six control lines. The ALU needs two data inputs:
    
    - a left input (A)
    - a right input (B)
    
    Attached to the left input is a holding register **H,** and attached to the right input is the B bus.
    
    **H** can be loaded by choosing an ALU function that just passes the right input (from the B bus) through to the ALU output.
    

  

## Memory Operation

- The machine has two different ways to communicate with memory:
    - a 32 bit word-addressable memory port
    - a 8-bit byte-addressable memory port
- The 32-bit port is controlled by two registers, **MAR (Memory Address Register)** and **MDR (Memory Data Register)**
- The 8-bit port is controlled by one register, **PC,** which reads 1 byte into the lower-order 8 bits of **MBR**. This port can only read data from memory; it cannot write data to memory.
- MAR and PC are used to reference two different parts of memory. -
    - MAR/MDR combination is used to read and write ISA-level data words
    - PC/MBR combination is used to read and executable ISA-level program
    - All other register that contain addresses use word addresses, like MAR

### Communicating with memory through a 32 bit word-addressable memory port:

In the actual physical implementation, there is only one real memory and it is byte oriented. Hence this allows MAR to count in words (needed due to the way JVM is defined) while the physical memory counts in bytes is handled by a simple trick. When MAR is placed on the address bus, its 32 bits do not map onto the 32 address lines, directly. Instead MAR bit 0 is wired to address bus line 2, MAR bit 1 is wired address bus line 2 and so on.

![[../../../Attachments/Untitled 4 18.png|Untitled 4 18.png]]

### Communicating with memory through a 8 bit word-addressable memory port:

The data read from memory through the 8-bit memory port are returned in MBR, an 8-bit register. MBR can be gated (i.e., copied) onto the B bus in one of two ways:

- unsigned
- signed

**Unsigned Value:**

When the unsigned value is needed, the 32-bit word put onto the B bus contains the MBR value in the low-order 8 bits and zeros in the upper 24 its. Unsigned values are useful for indexing into a table, or when a 16-bit integer has to be assembled from 2 consecutive (unsigned) bytes in the instruction stream.

**Signed Value:**

The other option for converting the 8-bit MBR to a 32-bit word is to treat it as a signed value between -128 and +127 and use this value to generate a 32-bit MBR sign bit (leftmost bit) into the upper 24 bit positions of the B bus, a process known as **sign extension.** When the option is chosen, the upper 24 bits will either be all 0s or 1s, depending on whether the leftmost bit of the 8-bit MBR is a 0 or a 1.

  

The choice of whether the 8-bit MBR is converted to an unsigned or a signed 32-bit value on the B bus is determined by which of the two control signals is asserted.

## Micro-instructions

To control the data path, we need 29 signals. These can be divided into five functional groups, as described below.

- 9 signals to control writing data from the C bus into registers
- 9 signals to control enabling registers onto the B bus for ALU input
- 8 signals to control the ALU and shifter functions.
- 2 signals to indicate memory read/write via MAR/MDR.
- 1 signal to indicate memory fetch via PC/MBR

The values of these 29 control signals specify the operations for one cycle of the data path. A cycle consist of gating values out of registers and onto the B bus, propagating the signals through the ALU and shifter, driving them onto the C bus, and finally writing the results in the appropriate register or registers. In addition, if a memory read data signal is asserted, the memory operation is started at the end of the data path cycle, after MAR has been loaded. The memory data are available at the very end of the following cycle in MBR or MDR and ca be used in the cycle after that.

There tends to be a delay when adding the data into the register, hence when cycle K ends the data in register would be available at k+2 not k+1.

While it may be desirable to write the output on the C bus into more than one register, it is never desirable to enable more that one register onto the B bus at a time. With a small increase in circuitry, we can reduce the number of bits needed to select among the possible sources for driving the B bus. There are only nine possible input registers that can drive the B bus. Therefore, we can encode the B bus information in 4 bits and use a decoder to generate the 16 control signals, 7 of which are not needed.

At this point we can control the data path with 9+4+8+2+1 = 24 signals, hence 24 bits. However, these 24 bits only control the data path for one cycle. The second part of the control is to determine what is to be done on the following cycle. To include this in the design of the controller, we will create a format for describing the operations to be performed using the 24 control bits plus two additional fields: the NEXT_ADDRESS field and the JAM field.

![[../../../Attachments/Untitled 5 18.png|Untitled 5 18.png]]

MIR (Micro-Instruction Register)

  

|   |   |
|---|---|
|**Addr**|Contains the address of a potential next micro-instruction|
|**JAM**|Determines how the next micro-instruction is selected|
|**ALU**|ALU and shifter functions|
|**C**|Selects which registers are written from the C Bus|
|**Mem**|Memory functions|
|**B**|Selects the B bus source; it is encoded as shown|

# An Example ISA: IJVM

## Stacks

Virtually all programming languages support the concept of procedures (methods), which have local variables. These variables can be accessed from inside the procedure but cease to be accessible once the procedure has returned. The questions thus arises: “Where should these variables be kept in memory?”

The simplest solution to give each variable an absolute memory address, does not work. the problem that a procedure may call itself. If a procedure is active and called twice, it is impossible to store its variables in absolute memory locations because the second invocation will interfere with the first.

**Operand Stack:**

Stacks have another use, in addition to holding local variables. They can be used for holding operands during the computation of an arithmetic expression. When used this way, the stack is referred to as the **operand stack**. Suppose, for example, that before calling B, A has to do the computation

a1 = a2 + a3

One way of doing this sum is to push a2 onto the stack, as show in bellow figure. Here SP has been incremented by the number of bytes in a word, say, 4, and the first operand stored at the address now pointed to by SP. Next a3 is pushed onto the stack. As an aside on notation, we will typeset all program fragments in Helvetica, as above.

The actual computation can be done by now executing an instruction that pops two words off the stack, adds them together, and pushes the result back onto the stack. Finally, the top word can be popped of the stack and stored back in local variable.

![[../../../Attachments/Untitled 31.png|Untitled 31.png]]

**The Constant Pool:** This area cannot be written by an IJVM program and consists of constants, strings, and pointers to other areas of memory that can be referenced. It is loaded when the program is brought into memory and not changed afterward. there is an implicit register, CPP, that contains the address of the first word of the constant pool.

**The Local Variable Frame:** For each invocation of a method, an area is allocated for storing variables during the lifetime of the invocation. it is called the local variable frame. At the beginning of this frame reside the parameters (also called arguments) with which the method was invoked. The local variable frame does not include the operand stack, which is separate. However, for efficiency reasons, our implementation chooses to implement the operand stack immediately above the local variable frame. there is an implicit register that contains the address of the first location in the local variable frame. We will call this register LV. The parameters passed at the invocation of the method are stored at the beginning of the local variable frame.

**The Operand Stack:** The stack frame is guaranteed not to exceed a certain size, computed in advance by the Java Compiler. The operand stack space is allocated directly above the local variable frame. In any case, there is an implicit register that contains the address of the top word of the stack.

**The Method Area:** Finally, there is a region of memory containing the program, referred to as the “text” area in a UNIX process. there is an implicit register that contains the address of the instruction to be fetched next. This pointer is referred to as the Program counter, or PC. Unlike the other regions of memory, the Method Area is treated as a byte array.

![[../../../Attachments/Untitled 1 6.png|Untitled 1 6.png]]

# Design of the Micro-Architecture Level:

## Speed Versus Cost

While faster technology has resulted in the greatest speedup over any period of time, that is beyond the scope of this text. Speed improvements due to organization, while less amazing than that due to faster circuits, have nevertheless been impressive. Speed can be measured in a variety of ways, but given a circuit technology and an ISA, there are thee basic approaches for increasing the speed of execution:

1. Reduce the number of clock cycles needed to execute an instruction.
2. Simplify the organization so that the clock cycle can be shorter.
3. Overlap the execution of instructions.

The number of clock cycles needed to execute a set of operations is known as the **path length.** Sometime the path length can be shortened by adding specialized hardware. For example, by adding an incrementer to PC, we no longer have to use the ALU to advance PC, eliminating cycles.

### Reducing the Execution Path Length:

The Mic-1 was designed to be both moderately simple and moderately fast although there is admittedly an enormous tension between these two goals.

Having seen how IJVM can be implemented in a straightforward way in microcode with little hardware, it is now time to look at alternative, faster implementation. We will next look at ways to reduce the number of micro-instructions per ISA instruction.

**Merging the Interpreter Loop with the Microcode**

In the MIC-1, the main loop consists of one micro-instruction that must be executed at the beginning of every IJVM instruction. In some cases it is possible to overlap it with the previous instruction.

The main loop can in be reduced to nothing in some cases. This can occur in the following way. Consider each sequence of micro-instruction that terminates by branching to Main1. At each of these places, the main loop micro-instruction can be tacked on the end of the sequence (rather than at the beginning of the following sequence), with the multi way branch now replicated man places.

  

![[../../../Attachments/Untitled 1 7.png|Untitled 1 7.png]]

![[../../../Attachments/Untitled 2 5.png|Untitled 2 5.png]]

**A Three-Bus Architecture**

Another easy fix to reduce the execution path length is to have two full input buses to the ALU, an A bus and a B bus, giving three buses in all. All of the register should have access to both input buses. The advantage of having two input buses is that it then becomes possible to add any register to any other register in one cycle.

Many times the ALU is used often to copy a value from one register to another. Thee cycles might be eliminated by introducing additional data paths not going through the ALU.

In the Mic-1, much of the load can be removed from the ALU by creating an independent unit to fetch and process the instructions. This unit, called an **IFU (Instruction Fetch Unit),** can independently increment PC and fetch bytes from the byte stream before they are needed.

**An Instruction Fetch Unit**

To get a dramatic improvement we need something much more radical. Ever instruction the following operations may occur:

1. The PC is passed through the ALU and incremented.
2. The PC is used to fetch the next byte in the instruction stream.
3. Operands are read from memory.
4. Operands are written to memory.
5. The ALU does a computation and the results are stored back

  

## A Design with Prefetching: The MIC-2

The IFU can greatly reduce the