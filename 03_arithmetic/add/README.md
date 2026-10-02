
**## add1.asm**

```text
[PF AF SF IF OF]
```

| Flag | Status  | Explanation                                                                                                                                       |
| ---- | ------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| CF   | Cleared | There is no carry out of the most significant bit of the 8-bit result.                                                                            |
| PF   | Set     | The result `10000010` contains two 1-bits. Since this is even parity, PF is set.                                                                  |
| AF   | Set     | The addition of the lower nibbles (`1000 + 1010`) produces a carry from bit 3 to bit 4.                                                           |
| IF   | Set     | The Interrupt Flag is enabled in the processor state while the program is running. It is not caused by the ADD instruction.                       |
| SF   | Set     | The most significant bit of the 8-bit result is 1, so the result has a negative signed interpretation.                                            |
| OF   | Set     | Both operands are positive signed 8-bit values, but the result has a sign bit of 1. The signed result therefore overflows the signed 8-bit range. |
| ZF   | Cleared | The result is not zero.                                                                                                                           |

**## add2.asm**

```text
[IF]
```

| Flag | Status  | Explanation                                                                                                                 |
| ---- | ------- | --------------------------------------------------------------------------------------------------------------------------- |
| CF   | Cleared | There is no carry out of the most significant bit of the 16-bit result.                                                     |
| PF   | Cleared | The low byte of the result is `11110100`, which contains five 1-bits. Since this is odd parity, PF is cleared.              |
| AF   | Cleared | The addition of the lower nibbles does not produce a carry from bit 3 to bit 4.                                             |
| IF   | Set     | The Interrupt Flag is enabled in the processor state while the program is running. It is not caused by the ADD instruction. |
| SF   | Cleared | The most significant bit of the 16-bit result is 0, so the result has a positive signed interpretation.                     |
| OF   | Cleared | Both operands are positive signed 16-bit values and the result remains within the signed 16-bit range.                      |
| ZF   | Cleared | The result is not zero.                                                                                                     |