# Opcode Changes

The IOS instruction was consistent between 1957 and 1963.  Its opcode
was 04, sometimes known as OPR, and apparently also used for the AOP
instruction.

The AOP instruction provided for operations entirely within the
Ariothmetic Element (with no memory reference).  It provided for
encoding the operation to be performed within the base address portion
of the instruction word.  However, none of the documentation we have
found to date explains what these operations were or what they did.

## 1957

I/O instruction opcodes were RDN, RDS, IOS.

IOS provided for connecting and disconnecting peripherals.  RDS and
RDN performed I/O reads or writed, depending on the mode of the
relevant device.

| Opcode | Function | Operand Bits Transferred | Comment |
| ------ | -------- | ---------------- | ------- |
| RDN    | I/O read or write | Least-significant 6 bits | Analogous to TSD's "normal" mode for, say, the paper tape reader. |
| RDS    | I/O read or write | Transfers every sixth bit, and then shifts word one bit leftward | Analogous to the later "Assembly" mode of, say, the paper tape reader.|
| IOS    | I/O control | Operand specifies the operation to be performed, of the device mode to set |

For details, see "The Lincoln TX-2 Input-Output System" by James W
Forgie, Lincoln Lab memo 6M-4968.

## 1963

I/O instruction opcodes were TSD, IOS (see the Users Handbook
[Vanderburgh61]).  The splay ("assembly") and shifting behaviours
still existed, but were selected differently.  The RDN/RDS opcodes are
replaced by a single TSD opcode.

| Opcode | Function          | Comment |
| ------ | -------           | ------- |
| TSD    | I/O Read or write | Normal/Assembly bit distribution and shifting now depends on the mode setting of the device.   Sequences 0, 76, and 77 always perform a shift on TSD.  Sequence 75 never does. |
| IOS    | I/O control | Appears similar to the 1957 description. |

For details, see the TX-2 Users Handbook.
