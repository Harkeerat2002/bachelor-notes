## Table of Contents

---

Table of Contents

Operating-System Services

User and Operating-System Interface

Command Interpreters (Command-Line Interface)

Graphical User Interface (GUI)

Touch-Screen Interface

System Calls

System Call Implementation

System Call Parameter Passing

Types of System Calls

Operating-System Structure

Monolithic Structure

Layered Structure

Micro-kernel System Structure

---

  

## Operating-System Services

![[../../../../Attachments/Untitled 43.png|Untitled 43.png]]

A view of Operating System Services

- Functions helpful to the user
    - **User Interfaces**
        - Almost all operating systems have a user interface (UI): Command-Line (CLI), Graphics User Interface (GUI), Batch
    - **Program Execution**
        - The system must be able to load a program into memory and to run that program, end execution either normally or abnormally (indicating an error).
    - **I/O Operations**
        - A running program may require I/O, which may involve a file or an I/O device.
    - **File-system Manipulation**
        - The file system is of particular interest. Obviously, programs need to read and write files and directories, create and delete them, search them, list file information, permission management.
    - **Communications**
        - Processes may exchange information on the same computer or between computers over a network.
    - **Error Detection**
        - OS needs to be constantly aware of possible errors.
            - May occur in the CPU and memory hardware, in I/O devices, in user program
            - For each type of error, OS should take the appropriate action to ensure correct and consistent computing.
            - Debugging facilities can greatly enhance the user’s and programmer’s abilities to efficiently use the system
- Functions ensuring efficient system operation (via resource sharing)
    - **Resource allocation**
        - When multiple users or multiple jobs running concurrenty, resources must be allocated to each of them
            - Many types of resources - Some (such as CPU cycles, main memory, and file storage) may have special allocation code, others (such as I/O devices) may have general request and release code.
    - **Logging (Accounting)**
        - To keep track of which users use how much and what kinds of computer resources
    - **Protection and Security**
        - The owners of information stored in a multi-user or networked computer system may want to control use of that information, concurrent processes should not interfere with each other.
        - Protections
            - It involves ensuring that all access to system resources is controlled.
        - Security
            - The security of the system from outsiders requires user authentication ,extends to defending external I/O devices from invalid access attempts.

## User and Operating-System Interface

### Command Interpreters (Command-Line Interface)

- Allows direct command entry
- Sometimes implemented in kernel, sometimes by systems program
- Sometimes multiple flavors implemented-**shells**
- Primarily fetches a command from user and executes it
- Sometimes commands built-in, sometimes just names of programs

### Graphical User Interface (GUI)

- User-friendly **desktop** metaphor interface
    - Usually mouse, keyboard, and monitor
    - **Icons** represent files, programs, actions, etc
- Many systems include both CLI and GUI interfaces
    - Microsoft Windows is GUI with CLI “command” shell.

### Touch-Screen Interface

- Both command-line interface or a mouse-and-keyboard system is impractical for most mobile system, smartphones and handheld tablet computers typically use a touch-screen interface.
- Here, users interact by making **gestures** on the touch screen.
- Both the iPad and the iPhone uses the Springboard touch-screen interface.

## System Calls

- Programming interface to the services provided by the OS.
- Typically written in a high-level language (C or C++).
- Mostly accessed by programs via a high-level **Application Programming Interface (API)** rather than direct system call use.
- Example:

![[../../../../Attachments/Untitled 1 15.png|Untitled 1 15.png]]

### System Call Implementation

- Number associated with each system call
- System-call interface maintains a table indexed according to these numbers
- The system call interface invokes intended system call in OS kernel and returns status of the system call and any return values.
- The caller need know nothing about how the system call is implemented
    - Just needs to obey API and understand what OS will do as a result call
    - Most details of OS interface hidden from programmer by API

  

![[../../../../Attachments/Untitled 2 11.png|Untitled 2 11.png]]

API - System Call - OS Relationship

**Standard C Library Example**

![[../../../../Attachments/Untitled 3 9.png|Untitled 3 9.png]]

- C Program invoking printf() library call, which calls write() system call.

### System Call Parameter Passing

- More information is required than simply identity of desired system call
    - Exact type and amount of information vary according to OS and call
- Three general methods
    1. Pass the Parameters in **Registers**
        - Some cases, may be more parameters than registers
    2. Parameters **stored in a block, or table, in memory,** and address of block passed as a parameter in a register
        - Approach taken by Linux and Solaris
            
            ![[../../../../Attachments/Untitled 4 8.png|Untitled 4 8.png]]
            
            Parameter Passing via Table
            
    3. Parameters placed, or pushed, onto the **stack** by program and popped off the stack by the operating system.

### Types of System Calls

- Another aspect of a modern system is its collection of system services.
- In the computer hierarchy, at the lowest level is hardware, next is the operating system, then the system services, and finally the application programs.
- **System services**, also known as **system utilities,** provide a convenient environment for program development and execution.
- **Process Control**
    - Load, execute, create, terminate, wait for time, ...
- **File Management**
    - Create/delete file, read, write, set/set attributes, ...
- **Device Management**
    - Request/release device, read, write, ....
- **Information Maintenance**
    - Get time/date, get/set system data, ...
- **Communications**
    - Create/delete, connection, send/receive, ...
- **Protection**

## Operating-System Structure

- A modern operating system must be engineered carefully if it is to function properly and be modified easily.
- A common approach is to partition the task into small components, or modules, rather than have it on a single system.

![[../../../../Attachments/Untitled 5 8.png|Untitled 5 8.png]]

### Monolithic Structure

- The simplest structure for organizing an operating system is **no structure at all.**
- That is, place all of the functionality of the kernel into a single, static binary file that runs in a single address space.
- Not divided into modules
- Although monolithic struct has some structure, their interfaces and levels of functionality are not well separated.
- Despite the apparent simplicity of monolithic kernels, they are difficult to implement and extend.
- **Disadvantages:**
    - There is very little overhead in the system-call interface
    - Implementation and Maintenance are very difficult

### Layered Structure

![[../../../../Attachments/Untitled 6 8.png|Untitled 6 8.png]]

A layered operating system

- The operating system is **divided into a number of layers** (levels), each built on top of the lower layers. The bottom layer (layer 0), is the hardware: and the highest (layer N) is the user interface.
- With modularity, layers are selected such that each one uses functions (operations) and services of only lower-level layers.
- Layered systems have been successfully used in computer networks (such as TCP/IP) and web applications.
- **Disadvantages**:
    - The overall performance of such a system is poor due to the overhead of requiring a user program to traverse through multiple layers to obtain an operating-system service.
    - Designing such a system is very difficult.
- **Advantages**:
    - Everything is more organized and easy to debug.

### Micro-kernel System Structure

![[../../../../Attachments/Untitled 7 6.png|Untitled 7 6.png]]

- Structures the operating system by removing all nonessential components from the kernel and implementing them as user-level programs that reside in separate address spaces.
- Moves as much from their kernel into “user” space
- Microkernel would provide only the **core** features.
- Communication takes place between user modules using **message passing**
- **Advantages**:
    - Easier to extend a micro-kernel
    - Easier to port the operating system to new architectures
    - More reliable (less code is running in kernel mode)
    - More secure
- **Disadvantages**:
    - Microkernel can suffer performance decrease due to increase in system function overhead.