
**## div1.asm & div2.asm**

```text
[AF IF]
```

| Flag | Status    | Explanation                                                                                                                 |
| ---- | --------- | --------------------------------------------------------------------------------------------------------------------------- |
| AF   | Undefined | DIV does not define the Auxiliary Carry Flag. Although GDB displays AF as set, its value is undefined after DIV.            |
| IF   | Set       | The Interrupt Flag is enabled in the processor state while the program is running. It is not caused by the DIV instruction. |

```text
DIV leaves all arithmetic status flags undefined so even though AF is seen to have bee 'set', it is still read as undefined.
```