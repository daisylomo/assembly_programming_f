## 01.asm

### Syscalls & Registers Used

| Purpose | Register / Value | Description |
| :--- | :--- | :--- |
| Register Setup | RAX = 100, RBX = 200 | Initial values pushed onto the stack |
| Swapped Registers | RCX = 200, RDX = 100 | Values popped from the stack in reverse order |
| Program Exit | RAX = 60, RDI = 0 | `sys_exit` system call with exit code 0 |

### Execution & Stack Flow

1. `mov rax, 100` and `mov rbx, 200` initialize source registers.
2. `push rax` subtracts 8 from RSP and writes 100 to memory at address RSP.
3. `push rbx` subtracts 8 from RSP and writes 200 to memory at address RSP.
4. `pop rcx` reads 200 from address RSP into RCX and adds 8 to RSP.
5. `pop rdx` reads 100 from address RSP into RDX and adds 8 to RSP.
6. `mov rax, 60`, `xor rdi, rdi`, and `syscall` execute `sys_exit(0)`.

### Stack Pointer Trace

| Step | Instruction | $RSP$ Shift (bytes) | Top of Stack ($[RSP]$) | Register State |
| :--- | :--- | :--- | :--- | :--- |
| Initial | `_start:` | 0 | `[OS Data]` | RAX=0, RBX=0 |
| Load RAX | `mov rax, 100` | 0 | `[OS Data]` | RAX=100 |
| Load RBX | `mov rbx, 200` | 0 | `[OS Data]` | RBX=200 |
| Push RAX | `push rax` | -8 | 100 | RAX=100, RBX=200 |
| Push RBX | `push rbx` | -8 | 200 | RAX=100, RBX=200 |
| Pop RCX | `pop rcx` | +8 | 100 | RCX=200 |
| Pop RDX | `pop rdx` | +8 | `[OS Data]` | RDX=100 |

### Observations
- Because the hardware stack is LIFO, pushing RAX(100) followed by RBX(200) and popping into RCX and RDX reverses the assignment (RCX=200, RDX=100).
- In 64-bit mode, `push` and `pop` automatically adjust RSP by exactly 8 bytes.
- Popping increments RSP but does not zero out memory; popped data remains in memory as stale data until overwritten.