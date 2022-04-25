## Disassembly of boot routines in Plugboard B.

The TX-2's start address is configurable via the "Toggle Start
Rgister" which sets the initial program counter when the TX-2 switches
to sequence 0.  This happens when (among other possiblities) the
operator presses the main CODABO ("count down and blast off") button.

The addresses from 0377740 to 0377757 exist (pysically) as Plugboard
B.

### 0377740

This is data to be loaded into the sysem's F-memory.  It's not
intended to be executed.

<pre>
0377740| 760,342,340,000      ** Values for F₃, F₂, F₁, F₀
0377741| 410,763,762,761      ** Values for F₇, F₆, F₅, F₄
0377742| 160,142,140,411      ** Values for F₁₃,F₁₂,F₁₁,F₁₀
0377743| 202,163,162,161      ** Values for F₁₇,F₁₆,F₁₅,F₁₄
0377744| 732,232,230,200      ** Values for F₂₃,F₂₂,F₂₁,F₂₀
0377745| 605,731,730,733      ** Values for F₂₇,F₂₆,F₂₅,F₂₄
0377746| 320,670,750,600      ** Values for F₃₃,F₃₂,F₃₁,F₃₀
0377747| 604,331,330,333      ** Values for F₃₇,F₃₆,F₃₅,F₃₄
</pre>

### 0377750

This routine configures f-memory.  It makes use of data at 0377740.
It sets up the System Configuration values used in subsequent
instructions (i.e. it determines the meanings of the superscripts in
other instructions).

<pre>
0377750| ⁰⁰SPG 377740         **  Load F₃, F₂, F₁, F₀ (F₀ is always 0 anyway)
0377751| ⁰⁴SPG 377741         **  Load F₇, F₆, F₅, F₄
0377752| ¹⁰SPG 277742         **  Load F₁₃,F₁₂,F₁₁,F₁₀
0377753| ¹⁴SPG 277743         **  Load F₁₇,F₁₆,F₁₅,F₁₄
0377754| ²⁰SPG 277744         **  Load F₂₃,F₂₂,F₂₁,F₂₀
0377755| ²⁴SPG 277745         **  Load F₂₇,F₂₆,F₂₅,F₂₄
0377756| ³⁰SPG 277746         **  Load F₃₃,F₃₂,F₃₁,F₃₀
0377757| ³⁴SPG 277747         **  Load F₃₇,F₃₆,F₃₅,F₃₄
</pre>

Execution continues at the next address, [0377760](plugboard-A#0377760).
