## 06.asm

### Program Execution Flow & Stack Behavior (Start to End)

1. **Initialization (`_start`)**:
   * `mov eax, 0x11223344`: Loads 32-bit immediate into EAX.
   * `mov ebx, 0x1234`: Loads 16-bit immediate into EBX, zero-extending upper 16 bits (EBX = 0x00001234).

2. **32-Bit Push Phase**:
   * `push eax`: Decrements ESP by 4 bytes and writes `0x11223344`.
   * `push ebx`: Decrements ESP by 4 bytes and writes `0x00001234`.

3. **Inspection Point (`nop`)**:
   * Stack contains two 4-byte dwords. Top of stack `[ESP]` = 0x00001234.

4. **Symmetric 32-Bit Pop Phase**:
   * `pop ebx`: Reads top dword into EBX and increments ESP by 4.
   * `pop eax`: Reads next dword into EAX and increments ESP by 4.

5. **32-Bit Exit Interrupt**:
   * `mov eax, 1` (`sys_exit`), `xor ebx, ebx`, `int 0x80`.

### 32-Bit Little-Endian

When EAX = 0x11223344 is pushed to address ESP:

| Byte Offset | Stored Byte Value (HEX) | Byte Significance | 
| ----- | ----- | ----- | 
| ESP + 0 | `0x44` | LSB | 
| ESP + 1 | `0x33` | Byte 1 | 
| ESP + 2 | `0x22` | Byte 2 | 
| ESP + 3 | `0x11` | MSB | 

### Stack Trace Table

| Step | Executed Instruction | delta ESP | Top of Stack [ESP] | Register State | 
| ----- | ----- | ----- | ----- | ----- | 
| **0** | `_start:` | baseline | `[OS Initial State]` | EAX=0, EBX=0 | 
| **1** | `mov eax, 0x11223344` | 0 bytes | `[OS Initial State]` | EAX=0x11223344 | 
| **2** | `mov ebx, 0x1234` | 0 bytes | `[OS Initial State]` | EBX=0x00001234 | 
| **3** | `push eax` | -4 bytes | `0x11223344` | EAX=0x11223344 | 
| **4** | `push ebx` | -4 bytes | `0x00001234` | EBX=0x00001234 | 
| **5** | `nop` | 0 bytes | `0x00001234` | Inspection point | 
| **6** | `pop ebx` | +4 bytes | `0x11223344` | EBX=0x00001234 | 
| **7** | `pop eax` | +4 bytes | `[OS Initial State]` | EAX=0x11223344 | 
| **8** | `int 0x80` | 0 bytes | `[OS Initial State]` | Exit | 

### Observations

- Each 32-bit push/pop alters ESP by 4 bytes (*ESP = +/- 4), compared to 8 bytes (RSP = +/- 8) in 64-bit mode (`05.asm`).
- `05.asm` pushes 64-bit quadwords to RSP using `syscall`, whereas `06.asm` pushes 32-bit doublewords to ESP using `int 0x80`.
