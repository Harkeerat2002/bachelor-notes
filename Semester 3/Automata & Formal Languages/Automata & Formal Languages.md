[Semester:: 3]   •   [Year:: 2]   •   [ECT:: 3]• [Completed:: ✅]
- [[Midterm Exam Prep]]
- [[Notion/Class Notes/Automata & Formal Languages/Formal Definitions/Formal Definitions|Formal Definitions]]
- [[Proofs]]
# Regular Languages

The theory of computation start with the question as to what is a computer. In order to understand how computer works it is important to go through some basic computers. With that the mathematical theory could then easily be applied to them, without any major complications. Hence, **computational model** is used, however, as with any model in science, a computational model may be accurate in some ways but perhaps not in others. Hence the simplest models, such as **finite state machine** or **finite automation** will be used.
## 1.1 Finite Automata:

These are models with limited amount of memory. In order to use probabilistic counterpart _**Markov Chains**_ are useful tools when the attempt is being made to recognize patterns in data.

The following figure depicts a finite automation call $M_1$﻿.

![[../../Attachments/Untitled 8.png|Untitled 8.png]]

A finite automation call $M_1$﻿ that has three states.

The above figure is called a **state diagram.** It has three **states**, labeled $q_1, q_2, and \space q_3$﻿. The **start state**, $q_1$﻿is indicated by the arrow pointing at it from nowhere. The **accept state,** **$q_2$**﻿**,** is the one with a double circle. The arrows going from one state to another are called **transistins.**

Therefore, when the automation receives an input string such as _1101_, it processes that string and produces an output. The output is either **accept** or **reject.** Hence the following are the results when $M_1$﻿ is fed the input string:

1. Start in state $q_1$﻿.
2. Read 1, follow transition from $q_1$﻿to $q_2.$﻿
3. Read 1, follow transition from $q_2$﻿to $q_2.$﻿
4. Read 0, follow transition from $q_2$﻿to $q_3.$﻿
5. Read 1, follow transition from $q_3$﻿to $q_2.$﻿
6. _Accept_ because $M_1$﻿is in an accept state $q_2$﻿ at the end of the input.

### Formal Definition of a Finite Automation

**Definition 1.5:**

A _**finite automation**_ is a 5-tuple (Q, Σ, δ, q 0 , F ), where

1. Q is a finite set called the _**states,**_
2. Σ is a finite set called the _**alphabet,**_
3. δ: Q $\times$﻿ Σ $\to$﻿ Q is the _**transition function,**_
4. $q_0$﻿ ∈ Q is the **start state**, and
5. $F \subseteq Q$﻿ is the **set of accept states.**

### Formal Definition of Computation

**Definition 1.16:**

A language is called a _**regular language**_ if some finite automation recognizes it.

**Example:**

Take the machine $M_5$﻿:

![[../../Attachments/Untitled 1 2.png|Untitled 1 2.png]]

Let _w_ be the string $10 <RESET>22<RESET>012.$﻿ Hence when this ran into the machine, it will recognize this as a regular language because it satisfies the defination of a regular language, by satisfying the three conditions.

### The Regular Operations

Hence the properties of _finite automata_ and _regular languages_ would be now investigated. In arithmetic, the basic objects are numbers and the tools are operations for manipulating them, such as + and x. In the theory of computation, the objects are languages and tools include operations specifically designed for manipulating them. There are three operation on languages, called the **regular operations,** use them to study properties of regular languages.

**Definition 1.23:**

Let A and B be languages. We define the regular operations **union, concatenation,** and **stars** as follows:

- **Union:** **$A\cup B = \{x|x\in A \space or \space x \in B\}.$**﻿
- **Concatenation:** **$A \circ B = \{xy|x \in A \space and \space y \in B \}. $**﻿
- **Star:** **$A^* = \{x_1 x_2 ...x_k|K \geq 0 \space and \space each \space x_i \in A \}.$**﻿

The **union** operation simply takes all the strings in both A and B and lumps them together into one language.

The **concatenation** attaches a string from A in front of a string from B in all possible ways to get the strings in the new language.

The **star** operation is different from the other two because it applies to a single language rather than to two different languages. That is, the start operation is a _unary operation_ instead of a _binary operation_. It works by attaching any number of string in A together to get a string in the new language. Because "any number" includes 0 as a possibility

**Example:**

Let the alphabet Σ be the standard 26 letters {a, b, ....., z}. If A = {good, bad} and b = {boy, girl}, then

$A \cup B = $﻿ {good, bad, boy, girl},

$A \circ B =$﻿ {goodboy, goodgirl, badboy, badgirl}, and

A* = {ε, good, bad, goodgood, goodbad, badgood, badbad, goodgoodgood, goodgoodbad, goodbadgood, goodbadbad, ....}.

  

## 1.2: Nondeterminism

- When the machine is in a given state and reads the next input symbol, we know what the next state will be — it is determined, hence it is called _**deterministic computation**_.
- In a _**nondeterministic**_ machine, several choices may exist for the next state at any point.

![[../../Attachments/Untitled 2 2.png|Untitled 2 2.png]]

The nondeterministic finite automation

**Difference between DFA (Deterministic Finite Automaton) and NFA (Nondeterministic Finite Automaton):**

- Every state of a DFA always has exactly one exiting transition arrow fo reach symbol in the alphabet.
- DFA Labels on the transition arrows are symbols from the alphabet. This NFA has an arrow with the label ε.

![[../../Attachments/Untitled 3 2.png|Untitled 3 2.png]]

Difference between DFA and NFA

When a point is reached where there is no more it can go, or the inputs are not satisfied, it is called **death configuration.** In DFA there is **death state.**

  

**Equivalence of two Finite Automata:**

- The two automata are not equivalent if for a pair $\{ q_a, q_b \}$﻿ one is intermediate state and the other is a final state.
- If Initial state is Final state of one automaton, then in second automaton also Initial State must be Final State for them to be equivalent.