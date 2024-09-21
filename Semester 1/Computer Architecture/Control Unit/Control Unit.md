- Part of CPU
- "Runs" Program
    - Three step process: `Fetch` `Decode` `Execute`
- Key Parts
    - **Program Counter** (Keeps track of next instruction)
    - **Instruction Decoder** (converts command to microinstruction, which directly controls "signals")
- Controls flow of data through CPU
    - Data flows along standard "[[Class Notes/Computer Architecture/Computer Architecture|Computer Architecture]]"
- **Control Flow:**
    
    - Program Counter (PC). Instruction Pointer (IP)
        - Points to the currently executing instruction
    - Instruction Register (IR)
        - Contains a copy of the currently executing instruction
    
    ![[../../../Attachments/Untitled 60.png|Untitled 60.png]]
    
- **Fetch-Decode-Execute Cycle:**
    1. Fetch next instruction from memory to IR
    2. Change PC to point to following instruction
    3. Determine type of instruction fetched
    4. If instruction used data from memory:
        - Load memory content into a CPU register
    5. Execute instruction
    6. Go to step 1
- **Instruction:**
    - Two types of instruction:
        - `Register` - `Register`
        - `Register` - `Memory`