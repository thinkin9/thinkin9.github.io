---
layout: post
title:  "Difference between MOV and LEA"
date:   2020-10-05 00:12:02 +0900
categories: System_Programming
---

<div style="text-align: center"><i><b>Last Updated on October 5th, 2020</b></i></div>

## MOV
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

* **MOV**ement
* Copy data from a source location to a destination location, differing in their source and destination types, without any transformation
* General Form: **MOV S, D** which is same as D &larr; S 
    * movb
    * movw
    * movl
    * movq
    * movabsq I, R which is same as R &larr; I
* Source: IMM, R, M
* Destination: R, M
    * M &nrarr; M
    * Only update the specified register bytes or memory locations indicated by the destination operand
    * Only exception is that when movl has a register as te destination, it will also set the high-order 4 bytes of the register to 0
* Regular movq instruction can only have immediate source operands that can be represented as 320bits 2's complement numbers
* **MOVZ S, R** which is same as R &larr; Zeroextended S
    * movzbw
    * movzbl
    * movzwl
    * movzbq
    * movzwq
    * ~~movzlq~~ == movl
* **MOVS S, R** which is same as R &larr; Signextended S
    * movsbw
    * movsbl
    * movswl
    * movsbq
    * movswq
    * movslq
    * cltq which is same as %rax &larr; Signextended(%eax)


## MOV Usage
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

* **L**oad **E**ffective **A**ddress
* Unique form: **leaq S, D** which is same as D &larr; &S
* Copy the effectuve address to the destination, rather than reading from the designated location

## MOV versus LEA
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

* movq 8(%rdx, %rdx, 4), %rax is same as %rax == M[%rdx + 4 * %rdx + 8]
    * Assume that %rdx == 0x10, M[%rax] == x, and M[0x58] == 0x08    
    movq 8(%rdx, %rdx, 4), %rax == M[0x10 + 4 * 0x10 + 8] == M[0x58] == 0x08

* leaq 8(%rdx, %rdx, 4), %rax is same as %rax == M[%rax] + 4*M[%rax] + 8
    * Assume that %rdx == 0x10, M[%rax] == x, and M[0x58] == 0x08    
    leaq 8(%rdx, %rdx, 4), %rax == 0x10 + 4 * 0x10 + 8 == 0x58
    * Even though the source is enclosed with parenthesis which means referencing the memory location, it does not reference memory at all