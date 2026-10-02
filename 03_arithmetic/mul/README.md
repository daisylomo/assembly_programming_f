# MUL Programs

**## mul1.asm**

```text
[IF]
```

| Flag | Status    | Explanation                                                                                                                                                                 |
| ---- | --------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| CF   | Cleared   | For MUL, CF is cleared when the upper half of the product is zero. The upper half of the 16-bit result is zero, so the product fits within the original 8-bit operand size. |
| IF   | Set       | The Interrupt Flag is enabled in the processor state while the program is running. It is not caused by the MUL instruction.                                                 |
| OF   | Cleared   | For MUL, OF has the same status as CF. Since the upper half of the product is zero, OF is cleared.                                                                          |
| PF   | Undefined | MUL does not define the Parity Flag, so its value after the instruction cannot be interpreted as a result of the multiplication.                                            |
| AF   | Undefined | MUL does not define the Auxiliary Carry Flag, so its value after the instruction cannot be interpreted as a result of the multiplication.                                   |
| SF   | Undefined | MUL does not define the Sign Flag, so its value after the instruction cannot be interpreted as a result of the multiplication.                                              |
| ZF   | Undefined | MUL does not define the Zero Flag, so its value after the instruction cannot be interpreted as a result of the multiplication.                                              |

**## mul2.asm**

```text
[CF IF OF]
```

| Flag | Status    | Explanation                                                                                                                               |
| ---- | --------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| CF   | Set       | For MUL, CF is set when the upper half of the product is non-zero. The upper 16 bits of the 32-bit result are `0009`, so CF is set.       |
| IF   | Set       | The Interrupt Flag is enabled in the processor state while the program is running. It is not caused by the MUL instruction.               |
| OF   | Set       | For MUL, OF has the same status as CF. Since the upper half of the product is non-zero, OF is set.                                        |
| PF   | Undefined | MUL does not define the Parity Flag, so its value after the instruction cannot be interpreted as a result of the multiplication.          |
| AF   | Undefined | MUL does not define the Auxiliary Carry Flag, so its value after the instruction cannot be interpreted as a result of the multiplication. |
| SF   | Undefined | MUL does not define the Sign Flag, so its value after the instruction cannot be interpreted as a result of the multiplication.            |
| ZF   | Undefined | MUL does not define the Zero Flag, so its value after the instruction cannot be interpreted as a result of the multiplication.            |
