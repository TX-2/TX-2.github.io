# The TX-2 Computer

## Contents
{:.no_toc}

* TOC
{:toc}


## Disclaimer

This document is not yet polished, but I hope it will be useful.
The primary source material is authoritative while this document is
not; see [Primary Sources](#primary).

## Introduction

This is an introduction to the TX-2 computer for modern readers.  The
aim of this document is to provide an overview and understanding of
the machine.

The TX-2 computer was built at MIT's Lincoln Laboratory as an
experimental machine, primarily to determine how reliable transistors
would be as the technical basis for the building of computers; see
[Transistors in the TX-2](transistors.md) for more information.

The introductory description of the TX-2 in Chapter 1 of the TX-2
Technical Manual states,

> TX-2 is currently used as a research tool in scientific computations
> and in data-handling and real-time problems. It differs from
> conventional general-purpose computers in that it permits an
> exceptionally high degree of flexibility in programming and in the
> use of inputoutput devices. This increase in flexibility, needless
> to say, is accompanied by a marked increase in design complexity. In
> many respects the machine is unique and one that has no counterpart
> at present.

They were not kidding.  This is a complex (and for the time, powerful)
machine.  Some of the ideas in the design have now become widespread
in modern computers, though in some cases (I/O through dedicated
threads of control for example) this has taken a while.  Other
features of the TX-2 (for example the "configuration" idea) have not
caught on, and frankly, the author is grateful for this as it makes
programs substantially more difficult to understand (though also, more
powerful).

## Primary Sources {#primary}

This document is not a complete description of the TX-2.  Please refer
to the primary sources for authoritative information.

This document is not a primary source; if you find a primary source
that is not consistent with this description, the primary source will
be correct.  There was only one TX-2 computer, but it was an
experimental machine, so it's not impossible that you could find two
primary sources that describe different things. For example, the
addresses of the Arithmetic Unit registers changed to make room for
[Plugboard B](plugboard-B.md).

This document is based mainly on the following primary sources:

- The [TX-2 Users Handbook](../documentation.md#UH) by Alex
  Vanderburgh, Jr (November 1963).
- The [TX-2 Technical Manual](../documentation.md#TM) by
  J. M. Frankovich, primarily Volume 1 (March-June 1961).

## Architecture

The TX-2 was a 36-bit ones-complement computer with a flat 17-bit
physical address space.  The single address space contained both data
and program instructions.

The components of the TX-2 were physically large, and computation
functions were spread out through it, so it had no "central processing
unit" as such.  The main components ("elements") of the computer are
described in [Physical Organisation](#physical-organization), but most
of this document describes the machine from the programmer's point of
view.


## Performance

The TX-2 was capable of executing about 200,000 instructions per second.

## Memory {#memory}

The TX-2 contains four different kinds of memory.  In ascending order
of address, these are:

| Memory | Words | Storage       | Logic            | Access Time (μs) | Remarks |
| ------ | ----- | ------------- | --------------   | ----------- |--------------------------- |
| S      | 65536 | Magnetic core | Valve drivers    | 4.0 |Slower than other memories. |
| T      |  4096 | Magnetic core | Transistorized   | 2.0 |                             |
| U      |   N/A | Magnetic core | Transistorized   | N/A | Proposed, not fitted |
| V      |   128 | Transistor Flip-flops, Plugboard |     | |Transistorized | See below |

See [The TX-2 Memory
Map](https://github.com/TX-2/TX-2-simulator/blob/main/cpu/src/memorymap.md)
for detailed information on the address layout of the TX-2.

### S, T and U memory

The S and T memory units store 36 value bits at each address, plus two
additional bits:

1. The Parity Bit: A parity bit is stored in core memory alongside the value bits.
Memory operations on words whose parity bit is incorrect will cause an
alarm to be raised.
1. The Meta Bit: This is is used to mark memory locations.  The SKM
instruction is the only instruction that can explicitly modify the
meta bit of a memory word.  The meta bit can also be set or tested by
the TX-2's ["TRAP" Circuit](#trap-circuit).

The U Memory was not fitted but would have been like the T memory.

### V Memory

The V memory is the topmost 128 words of memory.  It contains:

| Address (octal) | Description | Meta bit |
| ------- | ---------- | ------- |
| 0377600 | Start of V-memory. |  |
| 0377604 | A register             | Shared with the M register |
| 0377605 | B register             | Shared with the M register |
| 0377606 | C register             | Shared with the M register |
| 0377607 | D register             | Shared with the M register |
| 0377610 | E register             | Shared with the M register |
| 0377620 | Knob (Shaft Encoder) Register (User Handbook, 5-20) | Controlled by lighted push-button |
| 0377621 | External Input Register (User Handbook, 5-20); 37 push buttons. | Controlled by push button |
| 0377630 | Real Time Clock | Not present (see Technical Manual Volume 1, Table 2-1) |
| 0377710 | Toggle-switch register giving location of CODABO start point 0 | Controlled by toggle-switch |
| 0377711 | Toggle-switch register giving location of CODABO start point 1 |Controlled by toggle-switch |
| 0377712 | Toggle-switch register giving location of CODABO start point 2 |Controlled by toggle-switch |
| 0377713 | Toggle-switch register giving location of CODABO start point 3 |Controlled by toggle-switch |
| 0377714 | Toggle-switch register giving location of CODABO start point 4 |Controlled by toggle-switch |
| 0377715 | Toggle-switch register giving location of CODABO start point 5 |Controlled by toggle-switch |
| 0377716 | Toggle-switch register giving location of CODABO start point 6 |Controlled by toggle-switch |
| 0377717 | Toggle-switch register giving location of CODABO start point 7 |Controlled by toggle-switch |
| 0377740 | [Plugboard B](plugboard-B.md) | Set by the plugboard |
| 0377760 | [Plugboard A](plugboard-A.md) |Set by the plugboard |
| 0377777 | Last location in Plugboard A, and the top of physical memory  |

NOTE: Fig 2-13 in Volume 1 of the TX-2 Technical Manual states that
the V-memory has 144 registers, implying that it starts at 0377560
octal.

None of the locations in V-memory include a parity bit (though this is
present in the other memory units).

## Registers

In the TX-2's documentation, all memory locations capable of storing
data were described as "registers".  This encompassed general memory
storage, arithmetic and indexing registers used in computation, and
non-program-accessible stores used in the implementation (for example
the N register which was used to load the instruction to be executed).

### Arithmetic Element Registers

The Arithmetic Element (AE) registers are 36-bit registers which can
be used directly in arithmetical operations.  Each of these registers
can be loaded from or stored to other memory locations (inclusing the
other AE registers).

| Register | Functions |
| -------- | --------  |
| A        | Addition, subtraction, multiplication, division, logic and shift operations; A's sign controls conditional jumps.  Functions as the most-significant half of AB.|
| B        | Shift operations. Controls which bits of A are stored by an INS instruction.  Functions as the least-significant half of AB. |
| C        | Populated with carry flags after addition, subtraction or DSA instruction |
| D        | Implicitly loaded during add, subtract and shift operations (and DSA instruction); set by TLY |

Some operations operate on both the A and B register as if it were a
72-bit value; this combination is referred to as "AB".

These registers have memory addresses and can therefore be used for
instructions which operate on memory words.  For example the `STA C`
instruction can be used to store the value in A into the C register,
and the `TSD B` instruction can be used to output the value in the B
register to a peripheral.

### Index Registers

The Index Registers (sometimes called the X-registers) are 18 bits
wide and provided an indexed addressing mode for instructions and can
also be used as counters with jump instructions (for example with
automatic decrement and jump on non-zero).

The Index Registers were redsesigned to provide faster access and
cycle times, because most instructions feature address indexing and
therefore the performance of index memory was important.  Access time
was approximately 0.6μs (cycle time 3.6μs).

When set, the top bit of the index register generated a trap when the
TX-2 changed to the associated sequence (i.e. when that index register
was loaded into the P register).

### Configuration Registers

The TX-2's instruction word included 5 bits of "configuration" which
formed an index into a dedicated store, "F-memory".  F-memory
contained 32 9-bit values which specified how an instruction's
operands would be modified on the way to or from memory.  These
configuration registers could be changed with the `FLF` and `FLG`
instructions.  However, changing the F-memory would entirely change
the effect of a program's instructions, and so using a non-standard
F-memory configuration would likely cause difficulty.

Nevertheless the standard F-memory configuration was modified during
the lifetime of the TX-2 (but after the creation of Sketchpad) to
support the APEX environment.

See [Operand Configuration](#operand-configuration) for a description
of how the configuration values were used.

### Special Registers

| Register | Functions |
| E | When instructions perform a memory load/store, this register is set to the value of the memory word|
| Z | Overflow register |
| Q | Contains the address of the most recent memory reference |

## Sequences {#sequences}

I/O on the TX-2 was primarily performed via dedicated I/O
instructions.  Each peripheral had a dedicated "sequence" (today we
would say "thread") whose execution address was saved (when its
execution was suspended) in an index register.

Each sequence has a flag indicating whether it is ready to run.  At
any given time, the highest-priority (i.e. numerically lowest)
runnable sequence will run, unless a lower-priority sequence is
already executing an instruction and the instruction's "hold" bit it
set.

Sequences without associated hardware are still usable, but do not
perform I/O; instead they function like threads. When a sequence
issues a `TSD` instruction, I/O is attempted.  If the relevant
periperals is available for I/O, then the contents of a memory
location are transferred.  Any given sequence is either for reading or
writing (and peripherals which are capable of both occupy two
sequences).  If the peripheral is not yet ready, its sequence is
suspended until I/O is possible.

Sequences' flags can be raised or lowered (making them runnable or
not) and they can be "dismissed" (in other words made to yield
execution).

Many of the TX-2's sequences have several bits of mode information
which is used to control or configure the associated hardware.  This
is used for example to rewind the paper tape in the reader or to
configure the [Trap Circuit](#trap-circuit).

## Instructions

| Opcodes | Description |
| ------- | ----------- |
| LDA, LDB, LDC, LDD, LDE | Load an arithmetic register from memory (or another arithmetic register) |
| STA, STB, STC, STD, STE | Store an arithmetic register to memory (or another arithmetic register) |
| EXA | Swap contents of A register with contents of memory location |
| RSX | Load ("reset") an index register from a memory location |
| DPX | Store ("deposit") an index register to a memory location |
| EXX | Exchange contents of an index register with contents of a memory location |
| AUX | Increment ("augment") value of an index register by a value in a memory location |
| ADX | Increment value in a memory location by an the value of an index register |
| SKX | See [The SKX Instruction](#SKX) below |
| JPX, JNX | Jump if index register is positive/negative, then increment/decerment the index register |
| JMP | Unconditional jump with optional index offset, possibly saving return address in an index register or in E.  Can be used to dismiss a sequence. |
| JPA, JNA | Jump when A reigster is positive/negative
| JOV |  Jump when register Z is nonzero |
| SKM | Bitwise set, reset and flip operations on memory, as well as bit-test operations.  Successful bit tests cause the next instruction to be skipped. Optional logical rotation of the value.  See also [Extra Bits](#extra-bits). |
| SED | Skip next instruction if register E does not contain the same value as a memory location.  Does not change E. |
| SCA, SCB, SAB | Shift register A or B, or AB |
|NOA, NAB | Shift A or AB to remove leading zeroes |
|CYA|Rotate bits in register A|
|ITA|Logical AND between A and a memory word|
|UNA|Logical inclusive OR between A and a memory word|
|DSA|Logical exclusive OR (XOR) between A and a memory word|
|INS|Store masked bits of A (mask is in B)|
|COM|Complement the contents of a memory word|
|SPF, SPG|Load one or more F-registers from memory|
|FLF, FLG|Store one or more F-registers to memory|
|ADD|Add a memory word (which is left in D) to the A register|
|SUB|Subtract a memory word (which is left in D) from the A register|
|MUL|Multiply contents of A with a contents of a memory word; product is left in AB|
|DIV|Divide AB by the contents of a memory word.  Store quotient in A and remainder in B|
|TLY|Load A from memory word, storing the count of set bits in D|

### The SKX Instruction {#SKX}

The SKX register acts on the index registers without modifying the
arithmetic element's registers or the E register.  The operand part of
the instruction is used as the operand itself (as opposed to the
address of the operand, as is usual in other instructions).

The speicific operation performed is determined by the contents of the
configuration syllable of the instruction:

| Least-significant 3 bits of configuration value (octal) | Effect                              |
| ------------------- | ----------------------------------- |
| 0 | Store immediate value in index register |
| 1 | Store negated immediate value in index register |
| 2 | Increment index register by immediate value |
| 3 | Decrement index register by immediate value |
| 4 | Skip next instruction if index register holds a value which is not equal to the immediate value |
| 5 | Skip next instruction if index register holds a value which is not equal to the negated immediate value |
| 6 | Skip next instruction if the index register is less than the immediate value |
| 7 | Skip next instruction if the index register is greater than the negated immediate value |


The two most-significant bits each act independently (both of each
other and of the least-significant thee bits):

| Most-significant 2 bits of configuration value (octal) | Effect |
| ---- | ---- |
| 00 | No other effect. |
| 10 | Set the flag of the indicated sequence.
| 20 | Dismiss the current sequence (unless the instruction's hold bit is set).|
| 30 | Set flag of the indicated sequence and dismiss the current one. |

## Addressing Modes

The base address field of instructions is used to determine the memory
address of the operand to be used.  But this address is modified by
indexing and deferred addressing (which are not mutually exclusive).

### Immediate

Some instructions do not use indexation or deferred addressing.  In
other words, the address portion of the instruction is used not as the
address of an operand, but the operand itself.

| Instruction | Computed address | Word at computed address |
| ----------- | ---------------- | ------------------------ |
| Loads (e.g. LDA, LDB, LDC, LDD) | Loaded into Q register | Actual value is loaded into E register; exchanged value is loaded into the target register. |
| LDE | Loaded into Q register | Exchanged value is loaded into the E register |
| Stores (e.g. STA, STB, STC, STD) | Loaded into Q register | Set to the exchanged value (and the E register is set to this value). |
| STE | Loaded into Q register | Set to the exchanged value. E register is unchanged. |
| JMP, JPX, JNX, JPA, JNA | Loaded into P register | Loaded into N register when the instruction is next executed |
| Compuation  | Loaded into Q register | Loaded into E register |
| TSD         | Loaded into Q register | Loaded into E register |
| SKX         | No indexing or deferred addressing.  Value is loaded into index register | Not used |
| IOS         | No indexing or deferred addressing.  The address portion of the instruction is used both to indicate the I/O configuration operation to be performed and the mode to be set on the peripheral | Not used |

For some instructions (such as JMP) the configuration portion of the
instruction can disable indexing.

### Indexing

Most TX-2 instructions can be used in several addressing modes.   An
index register number can be specified, and its value is added to the
base address given in the instruction to determine the address of the
operand to be used for the instruction.

### Deferred Addressing (Indirection)

If the most significant bit (0400000 octal) of an operand address is
set, this selects deferred addressing.  In deferred addressng, a
36-bit value is loaded from the (possibly indexed) operand address.
This value has left (more significant) and right (less significant)
half.  The right half is used once more as the address of the operand,
indexing it with the value in whichever index register is identified
by the left half of the word what was loaded.

If the topmost bit of the resulting address also has the "defer" bit
set, this process is repeated.

This process is rather like the indirect addressing modes of modern
CPUs, but it is not restricted to only one level of indirection.

## Operand Configuration {#operand-configuration}

The Operand Configuration feature of the TX-2 is one of its most
complex aspects.

The transformation of operands in the [Exchange
Element](#exchange-element) was governed by the system configuration
selected by an instruction (via its configuration bits).
Configuration encompassed a number of transformations, which we
describe below.

| Transfer Direction | Permutation? | Activity? | Subword Form? | Sign Extension? |
| ------------------ | ------------ | --------- | ------------- | --------------- |
| Memory Fetch       | Yes | Yes | Yes | Yes |
| Memory Store       | Yes (in reverse) | Yes | No  | No  |

Quarter Permutation and Quarter Activity are applied in the E
register.

The [TX-2 Users Handbook](../documentation.md#UH) contains many
illustrations of the effect of operand permutation, primarily in
chapter 3 (which explains each instruction in detail).  The effect of
the standard configuration values is summarised in table 7-2.

### Quarter Permutation

As a word was transferred between the M and E registers, its quarters
could be permuted.  That is, quarters of the source (M or E) would be
written to, in general, different quarters of the destination (E or
M).

Bits 1, 2 and 3 of the configuration value specify the permutation to
be performed; these are described in table 7-2 of the Users Handbook
(this table appears twice; the "OLD" table would correspond to the
Sketchpad code).

### Quarter Activity

Which quarters of an operand were active during an instruction was
determined by bits 4 to 7 (counting from 1) of the system
configuration word.

| Bit | If zero, which quarter is active? |
| --- | --------------------------------- |
|   4 | Q1 |
|   5 | Q2 |
|   6 | Q3 |
|   7 | Q4 |

### Subword Form

The "Subword Form" of a configuration (bits 8 and 9) determined how
arithmetic worked on the operand.  This made it possible to treat a
36-bit word in any of the following ways:

| Bit 9 | Bit 8 | Subword Form | How was the operand handled? |
| ----  | ----- | ------------ | -----------                 |
|    0  |     0 | 36           | A single 36-bit value       |
|    0  |     1 | 18,18        | Two 18-bit values           |
|    1  |     0 | 27,9         | A 9-bit and a 27-bit value  |
|    1  |     1 | 9,9,9,9      | Four 9-bit values           |

The 27,9 subword form was sometimes used for floating-point numbers of
the form a×2<sup style="vertical-align: super">b</sup>.  See the note
in the description of the `MUL` instruction in the [TX-2 Users
Handbook](../documentation.md#UH).

### Sign Extension

If a subword (determined by the Subword Form) is partially active (as
determined by the Quarter Activity), the sign bit of the
most-significant active quarters in each subword is extended into any
more-siginificant portion of each subword.


### Example

In the standard configuration, F-register 12 (octal) has the value 142
(octal), or in binary 001 100 010.  In this configuration, bits 7 to 4
are 1100, meaning that Q1 and Q2 are active.  Bits 8 and 9 are both
zero meaning that the subword form is 36.  The remaining bits (1-3)
specify the permutation as 2.  In this permutation we have (for a load
from memory):

| Source | Destination |
| ------ | ----------- |
| Q4     | Q2          |
| Q3     | Q1          |

If the memory word being loaded had the octal value 701 123 777 555,
permutation would convert this to xxx xxx 701 123 (the xxx digits are
not active).  Since the subword form is 32, the inactive bits of the
(36-bit_ subword are sign-extended.  Q2 has the value 701, and so its
top bit is 1.  This is sign-extended, yielding the final result 777
777 701 123.

## I/O

## Alarms and Traps

### Alarms

The TX-2 featured a number of alarms which could be raised in response
to some condition.  Some of these could be masked.

| Alarm | Maskable? | Description |
| ----- | --------- | ----------- |
| FPAL  |     Yes   | Parity failure in Configuration Memory (F-Memory) |
| IOSAL |     Yes   | Selection of a peripheral that is in maintenance mode |
| MISAL       Yes   | Raised when data is ready for a sequence but it does not read it fast enough (i.e. more data arrives before the buffer has been read). If sequence 41 is connected, this alarm is suppressed automatically.|
| MOUSETRAP |  No   | Stops the computer during special maintenance operations|
| MPAL  |     Yes   | Parity failure in S, T or U Memory for operand     |
| NPAL  |     Yes   | Parity failure in S, T or U Memory for instruction |
| OCSAL |     Yes   | Executing instruction with invalid opcode (or OPR opcode with invalid subcode) |
| PSAL  |     Yes   | Attempt to fetch an instruction from an invalid address |
| QSAL  |     Yes   | Attempt to fetch an operand from an invalid address |
| SYAL  |     Yes   | Synch system alarm - synch system stopped the comptuter|
| TSAL  |      No   | T Memory selection circuits fail to perform properly |
| USAL |       No   | U Memory selection circuits fail to perform properly |
| XPAL  |     Yes   | Parity failure in Index Memory |

#### The EIA (Equipment Inability) Alarm

Some peripherals an "inability" alarm.  This would not stop the
computer, but it may ring a buzzer or stop the relevant peripherals.
Examples included:

- Xerox printer is low on paper
- Camera low on film

These conditions could be returned in the I/O status word for the
relevant peripheral, or detected by the [alarm
sequence](#alarmsequence).

#### Other Alarms

The TX-2's power supply also had some audible alarms which sounded
when a circuit breaker tripped.

The TX-2 emulator also defines some additional alarms, not present in
the real TX-2, to signal problems detected in the emulator.

### The Alarm Sequence {#alarmsequence}

Sequence 41 (octal) was dedicated to I/O alarms and could be set to
run in response to I/O conditions:

| Alarm | Description | Explanation |
| ----- | ----------- | ----------- |
| EIA   | Equipment Inability | Signals a problem with a peripheral |
| MISAL | Missed Data| Program serviced the peripheral too slowly |

Reading from the device of sequence 41 provided a bitmap indicating
which MISAL and EIA alarms were in effect.  For more details, see the
documentation for this sequence in the TX-2 Users Handbook.

### The Trap Circuit {#trap-circuit}

The TX-2's "TRAP" circuit is associated with sequence 42 (octal).  It
can be set up to raise the flag of sequence 42 in a number of
situations involving the meta bit of memory words, and to set the meta
bit of a word when it is used in several ways:

| Metabit of | Trap when detected | Set by (values are octal) |
| ---------  | ------------------ | ----------- |
| Instruction| Faise flag when executed (mode bit 001) | Implicitly on execution (mode bit 100) |
| Value used as deferred address | Raise flag (mode bit 002) | Implicitly on use (mode bit 0200) |
| Value used as operand | Raise flag (mode bit 004) | Implicitly on use (mode bit 0400) |
| Index register j | Change to sequence j (mode bit 010) | Set explicitly by loading the index register |

Index registers are 18 bits wide, and the topmost bit is considered to
be the meta bit for the purposes of mode bit 010 of the trap sequence.


## Physical Organization {#physical-organization}

### The Control Element

The Control Element provided timing and interlock controls, started
and stopped the computer and controlled the various kinds of (what we
would today describe as) bus cycles for transferring data.  The
control element also managed the alarms which signaled various kinds
of problem.

The Control Element arranged for partial overlap between the phases of
instruction execution. When possible, it arranged for the next
instruction to be fetched while the memory read/write operations of
the current instruction were still proceeding.

### The Memory Element

This part of the computer contained the S and T Memory (and would have
contained the U Memory, if fitted).  See the [Memory](#memory) section
above for the programmer's view of the various kinds of memory.

The memory element was capable of supporting concurrent fetches of
instructions and data, where the Control Element permitted this (for
example because different memory locations were being used for these).

### The Program Element

The program element was concerned with determining from what location
the next instruction should be loaded (including sequence selection),
and decoding the instruction once that has happened.

The Program Element contains a number of components:

| Component | Purpose |
| --------- | ------- |
| K register | Identifies the current sequence |
| N register | Current instruction |
| P register | Instruction address (i.e. program counter) |
| Q register | Operand address |
| Index registers | Indexed addressing (see [Indexing](#Indexing)) |
| X Adder | Indexed addressing |
| F-Memory | Stores configurations for [Operand Configuration](#operand-configuration). |
| J decoder | Decodes the index (J) bits of N register to identify the correct index register|
| CF decoder | Selection of correct F-memory register |

The Program Element performs the deferred and indexed addressing, when
these are required.

### The Exchange Element {#exchange-element}

The E and M registers exist inside the Exchange Element; the behaviour
of the exchange element was described above in [Operand
Configuration](#operand-configuration).

The M register was used to temporarily store a word that was being
loaded from or stored to S, T, U or V memory, or which was being read
from or written to a peripheral.  Parity checking was performed on the
M register.  The M register also provided the meta bit for the
Arithmetic Unit's registers and the E register.

While a word is inside the Exchange Element, it is altered according
to the value of the configuration bits of the current instruction word
(though note that this was not performed for some instructions; see
the TX-2 Users Handbook for details).

The altered ("configured") word ends up in the E register.  The
permutation is performed forwards of backwards depending on the
direction in which the word was traversing the Exchange Element.  The
permutation was carried out "forwards" for loads from memory and
"backwards" for stores to memory.

### The Arithmetic Element

The Arithmetic Element houses the A, B, C and D registers.  Each
quarter of the A register is associated with a ("Z") overflow
flip-flop.  The Arithmetic Element performs the following functions:

- Addition
- Subtraction
- Multiplication
- Division
- Logical operations (OR, XOR, AND)
- Shift, Cycle, Normalize, Tally


### The In-Out Element

The In-Out Element is responsible for peripheral I/O, and it connects
the E register to the In-Out Bus.  The In-Out element is responsible
for carrying out the operations determined by the IOS and TSD
instructions.  The In-Out Element includes a buffer for each
peripheral.

See [Sequences](#sequences) for the programmer's view of I/O on the
TX-2.  For more information on the TX-2's peripherals, see the [TX-2 Users
Handbook](../documentation.md#UH).  For information on sequence number
assignments, see [Sequence Changes](sequence-changes).

## Boot Process

The TX-2's console provided a lot of human control over the operation
of the control element, which was the part of the system which
controlled the boot process.  The console also provided a facility
which combined the most commonly-used start-up methodd.  This was the
CODABO (meaning "count down and blast off") button.

I assume that Ivan Sutherland's pronunciation of CODABO matches the
one used in Lincoln Lab generally.  His emphasis is on the first
syllable, so CODABO is pronounced rather one like one might say "coder
boe", and not like "code arbo".

When the CODABO button is pressed, alarms and registers are reset and
sequence 0 is started from the value in the Start Point Register.
It's likely this register is human-settable.  Perhaps by operation of
the switches in the Toggle-Switch Storage unit.  In any case, the most
frequent start point would be 0377750 (octal) which is in [Plugboard
B](plugboard-B.md).

That code sets up F-memory, switches from sequence 0 to 53 (the paper
tape reader), rewinds the tape and reads its first 23 words into
addresses 4 to 26 (octal). The boot code then transfers control to
location 3, which is the code loaded from the reader leader.  In
principle that could be any code, but it will usually be start-up code
generated by the assembler which will read the rest of the program
from paper tape and transfer control to it.  For more details see
[The Standard Tape Reader Leader](readerleader.md).
