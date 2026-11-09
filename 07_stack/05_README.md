## 05.asm

### Program Execution Flow & Stack Behavior (Start to End)

1. **Initialization (`_start`)**:
   * `mov rax, 0x1122334455667788`: Loads 64-bit quadword into RAX.
   * `mov rbx, 0x1234`: Loads 16-bit immediate into RBX, zero-extending upper 48 bits.

2. **Push Phase**:
   * `push rax`: Decrements RSP by 8 and writes 0x1122334455667788.
   * `push rbx`: Decrements RSP by 8 and writes 0x0000000000001234.

3. **Inspection Point (`nop`)**:
   * Stack holds two 64-bit quadwords. Top of stack `[RSP]` = 0x1234.

4. **Symmetric Pop Phase**:
   * `pop rbx`: Reads top of stack into RBX and increments RSP by 8.
   * `pop rax`: Reads next quadword into RAX and increments RSP by 8.

5. **Program Exit**:
   * Sets RAX = 60, RDI = 0, and executes `syscall`.

### Little-Endian In-Memory Byte Representation

| Byte Offset | Memory Address | Stored Byte Value (HEX) | Significance | 
| ----- | ----- | ----- | ----- | 
| RSP + 0 | `0x7FFFFFFFDE48` | `0x88` | LSB | 
| RSP + 1 | `0x7FFFFFFFDE49` | `0x77` | Byte 1 | 
| RSP + 2 | `0x7FFFFFFFDE4A` | `0x66` | Byte 2 | 
| RSP + 3 | `0x7FFFFFFFDE4B` | `0x55` | Byte 3 | 
| RSP + 4 | `0x7FFFFFFFDE4C` | `0x44` | Byte 4 | 
| RSP + 5 | `0x7FFFFFFFDE4D` | `0x33` | Byte 5 | 
| RSP + 6 | `0x7FFFFFFFDE4E` | `0x22` | Byte 6 | 
| RSP + 7 | `0x7FFFFFFFDE4F` | `0x11` | MSB | 

### Execution Observations

- LSB is stored at the lowest memory address (RSP + 0), while the most significant byte (`0x11`) resides at the highest offset (RSP + 7).
- Popping registers in the reverse order of pushing (`push RAX`, `push RBX` -> `pop RBX`, `pop RAX`) preserves the original register contents.
- Loading a 16-bit immediate into a 64-bit register zero-extends the upper 48 bits, ensuring clean 64-bit stack quadword writes.
