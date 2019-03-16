# LOCK
 
## Assert LOCK# Signal Prefix
 
 
|Opcode|Mnemonic|Description|
|-|-|-|
|F0|LOCK|Asserts LOCK# signal for duration of the accompanying|
 
## Description
 
Causes the processor's LOCK# signal to be asserted during execution of the accompanying instruction (turns the instruction into an atomic instruction). In a multiprocessor environment, the LOCK# signal insures that the processor has exclusive use of any shared memory while the signal is asserted.
 
Note that in later IA-32 processors (including the Pentium 4, Intel Xeon, and P6 family processors), locking may occur without the LOCK# signal being asserted. See IA-32 Architecture Compatibility below.
 
The LOCK prefix can be prepended only to the following instructions and only to those forms of the instructions where the destination operand is a memory operand: ADD, ADC, AND, BTC, BTR, BTS, CMPXCHG, CMPXCH8B, DEC, INC, NEG, NOT, OR, SBB, SUB, XOR, XADD, and XCHG. If the LOCK prefix is used with one of these instructions and the source operand is a memory operand, an undefined opcode exception (#UD) may be generated. An undefined opcode exception will also be generated if the LOCK prefix is used with any instruction not in the above list. The XCHG instruction always asserts the LOCK# signal regardless of the presence or absence of the LOCK prefix.
 
The LOCK prefix is typically used with the BTS instruction to perform a read-modify-write operation on a memory location in shared memory environment.
 
The integrity of the LOCK prefix is not affected by the alignment of the memory field. Memory locking is observed for arbitrarily misaligned fields.
 
 
## Operation
 
```c
AssertLOCK(DurationOfAccompaningInstruction);

```
 
 
## Flags affected
 
None.
instruction.

 
 
## IA-32 Architecture Compatibility
 
Beginning with the P6 family processors, when the LOCK prefix is prefixed to an instruction and the memory area being accessed is cached internally in the processor, the LOCK# signal is generally not asserted. Instead, only the processor's cache is locked. Here, the processor's cache coherency mechanism insures that the operation is carried out atomically with regards to memory. See "Effects of a Locked Operation on Internal Processor Caches" in Chapter 7 of IA- 32 Intel Architecture Software Developer's Manual, Volume 3, the for more information on locking of caches.

 
 
## Protected Mode Exceptions
 
|[]()||
|-|-|
|#UD|If the LOCK prefix is used with an instruction not listed in the "{description}" section above. Other exceptions can be generated by the instruction that the LOCK prefix is being applied to.|
 
## Real-Address Mode Exceptions
 
|[]()||
|-|-|
|#UD|If the LOCK prefix is used with an instruction not listed in the "{description}" section above. Other exceptions can be generated by the instruction that the LOCK prefix is being applied to.|
 
## Virtual-8086 Mode Exceptions
 
|[]()||
|-|-|
|#UD|If the LOCK prefix is used with an instruction not listed in the "{description}" section above. Other exceptions can be generated by the instruction that the LOCK prefix is being applied to.|