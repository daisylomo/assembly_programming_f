## 03.asm

### Program Execution

1. **Initialization (`_start`)**:
   * `mov rax, 10`: Loads initial value 10 into RAX. Stack pointer remains at baseline RSP.

2. **Subroutine Call**:
   * `call calculate`: Hardware automatically decrements RSP by 8 bytes and pushes the 64-bit address of `after_call` onto the stack. Execution transfers to `calculate`.

3. **Subroutine Execution (`calculate`)**:
   * `add rax, 5`: Increments RAX by 5 (RAX = 15). Stack pointer remains unchanged at RSP_0 - 8.
   * `ret`: Hardware pops the 64-bit return address from `[RSP]` into instruction pointer RIP and increments RSP by 8 bytes. Execution jumps to `after_call`.

4. **Post-Call Execution (`after_call`)**:
   * `nop`: Debug point confirming RAX = 15 and RSP = RSP_0.
   * `mov rax, 60`, `xor rdi, rdi`, `syscall`: System exit with code 0.

### Stack Trace Table

| Phase | Executed Instruction | delta RSP | Top of Stack [RSP] | Register State | 
| ----- | ----- | ----- | ----- | ----- | 
| **Entry** | `_start:` | baseline | `[OS Initial State]` | RAX=0 | 
| **Setup** | `mov rax, 10` | 0 bytes | `[OS Initial State]` | RAX=10 | 
| **Call** | `call calculate` | -8 bytes | Address of `after_call` | RAX=10 | 
| **Compute** | `add rax, 5` | 0 bytes | Address of `after_call` | RAX=15 | 
| **Return** | `ret` | +8 bytes | `[OS Initial State]` | RAX=15 | 
| **Post-Call** | `nop` | 0 bytes | `[OS Initial State]` | RAX=15 | 
| **Exit** | `syscall` | 0 bytes | `[OS Initial State]` | Exit code 0 | 

### Observations

- Functions that do not require local variables or preserved registers avoid frame setup overhead, minimizing instruction count.
- If a subroutine alters RSP without restoring it prior to `ret`, `ret` will pop corrupted data into RIP, causing a segmentation fault.