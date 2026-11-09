## 02.asm

### Execution Steps
1. **Caller Execution (`_start`)**:
   * `call work`: Decrements RSP by 8 bytes, pushes the 8-byte return address (`&_start` post-call label) onto the stack, and transfers execution to `work`.

2. **Subroutine (`work`)**:
   * `push rbp`: Decrements RSP by 8 bytes and saves the caller's base pointer.
   * `mov rbp, rsp`: Anchors RBP to the current stack address, forming the frame baseline.
   * `sub rsp, 16`: Subtracts 16 bytes from RSP to allocate space for two 64-bit local variables.

3. **Local Variable Writes & Reads**:
   * `mov qword [rbp - 8], 100`: Stores 100 into local variable slot 1.
   * `mov qword [rbp - 16], 200`: Stores 200 into local variable slot 2.
   * `mov rax, [rbp - 8]`: Loads 100 into RAX.
   * `mov rbx, [rbp - 16]`: Loads 200 into RBX.
   * `nop`: Debug inspection point for frame state.

4. **Subroutine (`work`)**:
   * `mov rsp, rbp`: Deallocates local variable stack space by resetting RSP to RBP.
   * `pop rbp`: Restores caller's base pointer, incrementing RSP by 8 bytes.
   * `ret`: Pops the 8-byte return address into RIP, incrementing RSP by 8 bytes and returns to `_start`.

5. **Caller Termination (`_start`)**:
   * Executes `mov rax, 60`, `xor rdi, rdi`, `syscall` to exit cleanly.

### Observations

- Using RBP allows referencing local variables (`[rbp - 8]`) regardless of push/pop operations adjusting RSP.
- Reserving local stack memory via `sub rsp, 16` is faster than executing multiple `push` instructions.
- `mov rsp, rbp` guarantees that all allocated local stack memory is reclaimed before `ret` executes.