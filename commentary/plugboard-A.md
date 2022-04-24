## Disassembly of boot routines in Plugboard A.

This is a disassembly of part of the TX-2's boot code. The TX-2's boot
code is configurable because it is set up in a plugboard.  This
particular boot code is shown as a listing in the Users Handbook.

### 0377760: Read Binary from Tape and Execute It

All values are in octal.  Loading 23 into X₅₄ ensures that we will
load words from tape into memory addresses 3 to 27 (inclusive).  The
load address is determined by the operand field of the `TSD`
instruction.  Registers X₅₂ and so forth are the index registers
(there are 100 octal, of these in total).  At the time this code
begins to run sequence 0 is the only active sequence.

<pre>
0377760|    ¹SKX₅₄ 23     ** X₅₄=-23, length of reader leader.
0377761|     REX₅₂ 377763 ** Load 377763 into X₅₂ (seq 52 start point)

0377762|   ²¹IOS₅₂ 30106  ** Paper tape reader: Load bin, read
                          ** assembly mode. Because the 020 bit was set
                          ** in the configuration syllable of the IOS
                          ** instruction, the flag of the current
                          ** sequence (sequence 0) is dropped,
                          ** allowing sequence 052 (paper tape reader)
                          ** to run once its flag is raised (the
                          ** peripheral will raise the flag when data
                          ** is ready).

                          ** Sequence 0 is done now.  The remaining
                          ** code executes as sequence 52 (at the next
                          ** address due to the setting in X₅₂).

              ** When the paper tape reader is in
                          ** "assembly" mode, The TSD instruction
                          ** loads 6 bits at a time into the 36-bit
                          ** word.

              ** At this point, the machine goes into
                          ** "LIMBO"; no sequence is runnable.  This
              ** changes when a paper-tape line is read by
              ** the paper-tape reader. This raises the
              ** flag of sequence 52, which becomes
              ** runnable. The program counter is restored
              ** from X₅₂, which currently holds 377763.
              ** Thus we proceed at the instruction on the
              ** next line.

              ** The loop starting at 0377763 loads all
              ** the words.  Loop counter is X₅₄.
0377763|     REX₅₃ 5      ** Load 5 into X₅₃ (6 tape lines per word)
              ** The loop starting at 0377764 loads a
              ** single word.  Loop counter is X₅₃.
0377764| h   TSD₅₄ 26     ** Load into 26+X₅₄ (which is negative)
0377765| h ³⁶JPX₅₃ 377764 ** loop if X₅₃>0, decrement it

                          ** We've read a whole word.  Loop to read
                          ** more words, until the value of X₅₄ tells
                          ** us we've read the fixed-length prefix.
0377766| h  ¹JNX₅₄ 377763 ** loop if X₅₄<0, increment it

                          ** The reader leader is fully read.
0377767|   ¹⁴JPQ 3        ** Transfer control to it.
                          ** It will load each block of the
                          ** executable into the correct address and
                          ** verify the checksum of each, then call
                          ** the user's program.
</pre>


### 0377770: Clear Memory

This is the most likely setting for the setting of the Toggle Start
Register.  That is, it is the program counter address at which the
operator will most likely start the machine.

<pre>
377770|    REX₇₇    207777 ** One less than the combined size of
	                       ** S and T memory (these are
						   ** contiguous).  In other words, this
						   ** counts the number of words to clear.
377771|    DPX₇₇    777776 ** Write the sign-extended value of
                           ** X₇₇ to 0+X₇₇.  Since X₇₇>=+0, this
					       ** sets the left subword to zero.
						   ** The right wubword of each location
						   ** is set to its address.
377772|  ¹⁴JPQ₇₇    377773 ** Unsure, see below.
	                       ** This saves the Q register and
						   ** P register in the E register.
						   ** I'm not clear on the intent here.
377773|    REX      777610 ** Unsure, see below.
                           ** This is an indirection from the
						   ** E register (which is at 377610).
					       ** It appears to set X₀, but that
						   ** is read-only.
377774| h³⁶JPX₇₇    377771 ** Loop while X₇₇>0, decrement X₇₇.
377775|  ³⁰SKN₄.₁₂  377744 ** See below.
377776|   77,,0            ** Used by indirection at 377771.
                           ** The right subword gives the base
					       ** address and the left identifies
						   ** which index register to use.
						   ** So 77,,0 simply gives the
						   ** current value of X₇₇.
377777| ¹⁴JPQ       377750 ** Jump to "configure F-memory"
</pre>

The code at 377750 is in [Plugboard A](disassembly-377740).

I'm not clear yet on the precise behaiour of the instructions at
377772-377775, so this assembly listing is not yet fully commented.
