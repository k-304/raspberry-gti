# Aarch64 Assembler

## Dokumentation

[ARMv8 A64 Quick Reference](https://courses.cs.washington.edu/courses/cse469/18wi/Materials/arm64.pdf)

[AArch64 Register and Instruction Quick Start](https://wiki.cdot.senecacollege.ca/wiki/AArch64_Register_and_Instruction_Quick_Start)

## Register
```assembly
/*
    r = x = w  
    r = "register"  
    x = "register 64 bit"  
    w = "register 32 bit (word)"  
*/


# mrs=move register system, x1=a general purpose register ->  mrs=move register system x1=a general purpose register
# https://andreasch.com/2019/01/29/introduction-aarch64/
# MPIDR_EL1, Multiprocessor Affinity Register, EL1 
# https://developer.arm.com/documentation/100403/0200/register-descriptions/aarch64-system-registers/mpidr-el1--multiprocessor-affinity-register--el1?lang=en
mrs     x1, mpidr_el1 
```

## Segment
```assembly
.section ".text.boot"            
.global _start                   

```

## Sprung Befehle
[Branch Instructions](https://www.cs.nmsu.edu/~hdp/cs273/notes/branches.html)

```assembly
main:                   /* label */
2:                      /* label */
cbz     x1, 2f          /* branch zero       [ if (x1 == null) jumpForward to 2: ]  */
cnbz    x0, 1b          /* branch not zero   [ if (x0 != null) jumpBackward to 1: ] */
bl      function_name   /* branch and link (call subroutine) */
bhi     label           /* branch higher */
bgt     label           /* branch greater than */
```

## System
```assembly
nop                      /* no operation */
wfe                      /* wait for event */
```

## Transport Befehle
```assembly
ldr x0,=0xFE200000       /* Load register */
mov x1,#0x1000000        /* Move */
str x1,[x0,#0x1c]        /* Store */
stp x1, x2, [sp, -22]!   /* Soring a pair */
ldp x1, x2, [sp], 32     /* Loading a pair */
```

## Logische Befehle
```assembly
# 1 = b00001
# 3 = b00011
# b = b00100
and x1, x1, #3           /* if bit 0 and 1 in x1 is set: b00011 */

```

## Arithmetic
```assembly
add x1, x1, #3           /* x1 = x1 + 3 */
```

## Adressing
- [x0] => content of address
- 4   => decimal number