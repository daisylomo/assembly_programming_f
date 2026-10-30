daisylomo@daisylomo:~/Projects/assembly_programming_f/07_stack$ nasm -f elf64 01.asm -o 01.o
daisylomo@daisylomo:~/Projects/assembly_programming_f/07_stack$ ld 01.o -o 01
daisylomo@daisylomo:~/Projects/assembly_programming_f/07_stack$ ./01
daisylomo@daisylomo:~/Projects/assembly_programming_f/07_stack$ nasm -f elf64 02.asm -o 02.o
daisylomo@daisylomo:~/Projects/assembly_programming_f/07_stack$ ld 02.o -o 02
daisylomo@daisylomo:~/Projects/assembly_programming_f/07_stack$ ./02
daisylomo@daisylomo:~/Projects/assembly_programming_f/07_stack$ nasm -f elf64 03.asm -o 03.o
daisylomo@daisylomo:~/Projects/assembly_programming_f/07_stack$ ld 03.o -o 03
daisylomo@daisylomo:~/Projects/assembly_programming_f/07_stack$ ./03
daisylomo@daisylomo:~/Projects/assembly_programming_f/07_stack$ nasm -f elf64 04.asm -o 04.o
daisylomo@daisylomo:~/Projects/assembly_programming_f/07_stack$ ld 04.o -o 04
daisylomo@daisylomo:~/Projects/assembly_programming_f/07_stack$ ./04
Segmentation fault (core dumped)
daisylomo@daisylomo:~/Projects/assembly_programming_f/07_stack$ nasm -f elf64 05.asm -o 05.o
daisylomo@daisylomo:~/Projects/assembly_programming_f/07_stack$ ld 05.o -o 05
daisylomo@daisylomo:~/Projects/assembly_programming_f/07_stack$ ./05
daisylomo@daisylomo:~/Projects/assembly_programming_f/07_stack$ nasm -f elf64 06.asm -o 06.o
daisylomo@daisylomo:~/Projects/assembly_programming_f/07_stack$ ld 06.o -o 06
daisylomo@daisylomo:~/Projects/assembly_programming_f/07_stack$ ./06
daisylomo@daisylomo:~/Projects/assembly_programming_f/07_stack$ ./04
Segmentation fault (core dumped)
daisylomo@daisylomo:~/Projects/assembly_programming_f/07_stack$ cd ..
daisylomo@daisylomo:~/Projects/assembly_programming_f$ cd 08_macros/
daisylomo@daisylomo:~/Projects/assembly_programming_f/08_macros$ nasm -f elf64 m1.asm -o m1.o
daisylomo@daisylomo:~/Projects/assembly_programming_f/08_macros$ ld m1.o -o m1
daisylomo@daisylomo:~/Projects/assembly_programming_f/08_macros$ ./m1
Welcome to Assembly!
Learning NASM macros.
One macro, multiple messages.
daisylomo@daisylomo:~/Projects/assembly_programming_f/08_macros$ nasm -f elf64 m2.asm -o m2.o
daisylomo@daisylomo:~/Projects/assembly_programming_f/08_macros$ ld m2.o -o m2
daisylomo@daisylomo:~/Projects/assembly_programming_f/08_macros$ ./m2
Addition: 40
Subtraction: 30
daisylomo@daisylomo:~/Projects/assembly_programming_f/08_macros$ nasm -f elf64 m3.asm -o m3.o
daisylomo@daisylomo:~/Projects/assembly_programming_f/08_macros$ ld m3.o -o m3
daisylomo@daisylomo:~/Projects/assembly_programming_f/08_macros$ ./m3
Number is zero.
Number is not zero.
Number is not zero.
daisylomo@daisylomo:~/Projects/assembly_programming_f/08_macros$ nasm -f elf64 m4.asm -o m4.o
daisylomo@daisylomo:~/Projects/assembly_programming_f/08_macros$ ld m4.o -o m4
daisylomo@daisylomo:~/Projects/assembly_programming_f/08_macros$ ./m4
Hello!
Hello!
Hello!
Hello!
Hello!
daisylomo@daisylomo:~/Projects/assembly_programming_f/08_macros$ nasm -f elf64 m5.asm -o m5.o
daisylomo@daisylomo:~/Projects/assembly_programming_f/08_macros$ ld m5.o -o m5
daisylomo@daisylomo:~/Projects/assembly_programming_f/08_macros$ ./m5
Register operations completed.
daisylomo@daisylomo:~/Projects/assembly_programming_f/08_macros$ nasm -f elf64 m6.asm -o m6.o
daisylomo@daisylomo:~/Projects/assembly_programming_f/08_macros$ ld m6.o -o m6
daisylomo@daisylomo:~/Projects/assembly_programming_f/08_macros$ ./m6
Program completed successfully.
daisylomo@daisylomo:~/Projects/assembly_programming_f/08_macros$ nasm -f elf64 m7.asm -o m7.o
daisylomo@daisylomo:~/Projects/assembly_programming_f/08_macros$ ld m7.o -o m7
daisylomo@daisylomo:~/Projects/assembly_programming_f/08_macros$ ./m7
First line
Second line
daisylomo@daisylomo:~/Projects/assembly_programming_f/08_macros$ nasm -f elf64 macros.asm -o macros.o
daisylomo@daisylomo:~/Projects/assembly_programming_f/08_macros$ ld macros.o -o macros
daisylomo@daisylomo:~/Projects/assembly_programming_f/08_macros$ ./macros
start ...
stop ...
daisylomo@daisylomo:~/Projects/assembly_programming_f/08_macros$ nasm -f elf64 procedures.asm -o procedures.o
daisylomo@daisylomo:~/Projects/assembly_programming_f/08_macros$ ld procedures.o -o procedures
daisylomo@daisylomo:~/Projects/assembly_programming_f/08_macros$ ./procedures
start ...
stop ...
daisylomo@daisylomo:~/Projects/assembly_programming_f/08_macros$ 