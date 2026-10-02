
**## sub1.asm**

```text
[CF PF SF IF]
```

| Flag | Status  | Explanation                                                                                                                 |
| ---- | ------- | --------------------------------------------------------------------------------------------------------------------------- |
| CF   | Set     | The subtraction requires an unsigned borrow because 50 is smaller than 80.                                                  |
| PF   | Set     | The result `11100010` contains four 1-bits. Since this is even parity, PF is set.                                           |
| AF   | Cleared | The subtraction of the lower nibbles does not require a borrow from bit 4.                                                  |
| IF   | Set     | The Interrupt Flag is enabled in the processor state while the program is running. It is not caused by the SUB instruction. |
| SF   | Set     | The most significant bit of the 8-bit result is 1, indicating a negative signed result.                                     |
| OF   | Cleared | The signed result is -30, which is within the signed 8-bit range of -128 to 127.                                            |
| ZF   | Cleared | The result is not zero.                                                                                                     |

**## sub2.asm**

```text
[CF PF SF IF]
```

| Flag | Status  | Explanation                                                                                                                 |
| ---- | ------- | --------------------------------------------------------------------------------------------------------------------------- |
| CF   | Set     | The subtraction requires an unsigned borrow because 1000 is smaller than 2000.                                              |
| PF   | Set     | The low byte of the result is `00011000`, which contains two 1-bits. Since this is even parity, PF is set.                  |
| AF   | Cleared | The subtraction of the lower nibbles does not require a borrow from bit 4.                                                  |
| IF   | Set     | The Interrupt Flag is enabled in the processor state while the program is running. It is not caused by the SUB instruction. |
| SF   | Set     | The most significant bit of the 16-bit result is 1, indicating a negative signed result.                                    |
| OF   | Cleared | The signed result is -1000, which is within the signed 16-bit range of -32768 to 32767.                                     |
| ZF   | Cleared | The result is not zero.                                                                                                     |
