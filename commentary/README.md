# Commentary

This is where we keep commentary on the primary sources, explanation
of our current understanding and so forth.

## The Boot Process

* [Plugboard B](plugboard-B) Disassembly of Plugboard B
* [Plugboard A](plugboard-A) Disassembly of Plugboard A

The operator is most likely to boot the system from 377770, so you
could start by reading the code in [plugboard A](plugboard-A#3777770).

I suspect that initially there was only Plugboard A, because early
documentation (e.g. the 1957 conference papers) show the registers in
the locations subsequently occupied by plugboard B.

## Sequence Number Assignments

Sequence number assignments changed as the system hardware changed.
The changes we know about are summarized in [Sequence
Changes](sequence-changes).

## Opcodes

Some of the opcodes for instruction changed over time; some of these
changes are described in [Opcode Changes](opcode-changes.md).
