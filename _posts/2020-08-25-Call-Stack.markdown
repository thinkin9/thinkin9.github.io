---
layout: post
title:  "Call Stack"
date:   2020-08-25 21:12:05 +0900
categories: System_Programming
---
<div style="text-align: center"><i><b>Last Updated on August 25th, 2020</b></i></div>

## Macro
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

* Macro (Computer Science), [Wikipedia](https://en.wikipedia.org/wiki/Macro_(computer_science))
* A rule of pattern that specifies how process the given sequence according to a defined procedures
* Before doing the compile, there is an replacement process from macros to original codes

## Subroutine
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

* Subroutine, [Wikipedia](https://en.wikipedia.org/wiki/Subroutine#Call_stack)
* A subroutine is a sequence of program instructions that performs a specific task
* Reduce the cost of developing ans maintaining a large program, while increasing its quality and reliability
* Not directly replaced
* Store them via call stack

## Call Stack
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

* Call Stack, [Wikipedia](https://en.wikipedia.org/wiki/Call_stack#Stack_and_frame_pointers)
* A call stack is a stack data structure that stores information about the active subroutines of a computer program
* Main reason for having one is to keep track of the point to which each active subroutine should return control when it finishes executing (Return Address).
* 어떤 작업을 하는 Procedure를 코드를 직접 치환하지 않고 재사용을 하는 방식인데, 원래의 Routine으로 돌아가기 위해서 Return Address를 Call stack에 push 해놓고 끝나면 사용