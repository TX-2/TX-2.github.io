# Tge Standard Tape Reader Leader

## Purpose

The TX-2's boot code loads a short sequence of instructions from paper
tape into locations 3 to 26 (octal) and transfers control to it.  This
code will normally read in the remaining parts of the user's program
and execute it.

The TX-2's assembler arranges for the first 23 words of its tape
output to contain code which will do this. A listing for this is given
on page 5-26 of the TX-2 User Handbook.

The Reader Leader program is superficially similar to Program VI ("A
Binary Read-In Routine") in Lincoln Lab Memorandum 6M-5780 ("Some
Examples of TX-2 Programming"), but it is different in detail.


## Commentary

The left-hand column here indicates the memory address at which we
will find each instruction.


```tx2
00                   ** Used as a temporary for words read from tape
01                   ** unused?
02                   ** unused?
03   ¹RSX₅₄ 5        ** set X₅₄=-5
04  ³⁶JMP₅₄ 20       ** Call procedure to read first word into [0]
05 h ²RSX₅₃ 0        ** Set X₅₃ = L([0])  ([0] is saved in E)
06   ¹STE 11         ** Set R([11]) to the word we read from tape.

07  ³⁶JMP₅₄ 17       ** Call procedure at 17 (clear metabit, read word)
10 h  LDE   0        ** Load new word into E.

                     ** R([11]) is the end address of the current
                     ** block (this insruction is modified by the
                     ** instruction at 06).
11    STE₅₃ 34       ** Store new word at [X₅₃+end]
12 h ¹JNX₅₃ 7        ** Loop to 7 when X₅₃<0. Postincrement X₅₃.
13  ³⁶JMP₅₄ 20       ** Call procedure to read another word into [0]
14 h  JPX₅₆ 377760   ** if X₅₆ > 0, restart tape loading
15 h  JNX₅₆ 377760   ** if X₅₆ < 0, restart tape loading
16  ¹⁴JPQ 27         ** Call user program (the instruction at 25 may have
                     ** changed this address).

** Read-word procedure (entry point 1, clears meta bit)
17   ²MKZ₄.₁₂ 400011 ** Reset meta bit of [11]
** Read-word procedure (entry point 2, meta bit unaffected)
** On entry , X₅₄ is the return address.
20   ¹RSX₅₇ 3        ** Set R(X₅₇)=R(3) which is 5.
21 h  TSD 0          ** Read tape bits into [0].
22  ³⁶JPX₅₇ 21       ** Loop (to TSD) when X₅₇>0 (i.e. do whole word)
23   ¹AUX₅₆ 0        ** Add R[0] to X₅₆
24 h ²AUX₅₆ 0        ** Add L[0] to X₅₆
25   ¹STE 16         ** Set R[16] to E (which we loaded from [0]).
26  ¹⁵BPQ₅₄ 0        ** Branch to X₅₄ (no offset) - in other words, return.

Location 26 is the last word of the standard reader leader as
loaded by the boot code, but the assembler includes the
instructions after it in a special block loaded at location 27:

27 ¹IOS₅₂ 20000    ** Disconnect PETR, load report word into E.
                   ** This instruction is replaced by `JPQ AA` when
                   ** a start address is used with ☛☛PUNCH.
```
