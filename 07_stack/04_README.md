## 04.asm

### Program Execution

1. **Caller Execution (`_start`)**:
   * `call work`: Pushes 4-byte return address onto the stack and branches to `work`.

2. **32-Bit Subroutine Prologue (`work`)**:
   * `push ebp`: Saves 32-bit caller frame pointer.
   * `mov ebp, esp`: Anchors EBP frame base.
   * `sub esp, 8`: Allocates 8 bytes for local variables.

3. **32-Bit Local Memory Access**:
   * `mov dword [ebp - 4], 100`: Stores 100 at `[EBP - 4]`.
   * `mov dword [ebp - 8], 200`: Stores 200 at `[EBP - 8]`.
   * `mov eax, [ebp - 4]`: Reads 100 into EAX.
   * `mov ebx, [ebp - 8]`: Reads 200 into EBX.

4. **32-Bit Epilogue (`work`)**:
   * `mov esp, ebp`: Collapses local stack allocation.
   * `pop ebp`: Restores caller's EBP.
   * `ret`: Pops 4-byte return address into EIP.

5. **Caller Termination (`_start`)**:
   * Sets EAX = 1 (`sys_exit`), EBX = 0 (exit code), and executes.

### 32-Bit vs 64-Bit Stack

| Parameter | 32-Bit Execution (`04.asm`) | 64-Bit Execution (`02.asm`) | 
| ----- | ----- | ----- | 
| **Stack Pointer Register** | ESP (32-bit) | RSP (64-bit) | 
| **Base Pointer Register** | EBP (32-bit) | RBP (64-bit) | 
| **Default Word Size** | 4 bytes (dword) | 8 bytes (qword) | 
| **Push / Pop Pointer Shift** |  *ESP = +/- 4 bytes | *RSP = +/- 8 bytes | 
| **Return Address Size** | 4 bytes | 8 bytes | 
| **Local Space Allocation** | `sub esp, 8` (2 dwords) | `sub rsp, 16` (2 qwords) | 
| **Kernel Interface** | `int 0x80` (EAX = 1) | `syscall` (RAX = 60) | 