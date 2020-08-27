---
layout: post
title:  "Why do I need dynamic memory allocation"
date:   2020-08-27 22:34:11 +0900
categories: C/C++
---

<div style="text-align: center"><i><b>Last Updated on August 27th, 2020</b></i></div>

## Memory
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

* We have strived to archieve better utilization of resources at all times
* Memory has to be allocated to the variables that we create, so that actual variables can be brought to existence

## Memory Allocation
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

* Memory allocation is a process by which computer programs and services are assigned with physical or virtual memory space
* The memory allocation is done either before or at the time of program execution
* [Difference between static and dynamic memory allocation in C/ geeksforgeeks](https://www.geeksforgeeks.org/difference-between-static-and-dynamic-memory-allocation-in-c/?ref=rp)

## Static Memory Allocation
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

* Static Memory is allocated for declared variables by the compiler during compile time
* The address can be found using the address of operator and can be assigned to a pointer

## Dynamic Memory Allocation
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

* Dynamic Memory is allocated at the time of execution(run time)
* calloc() and malloc() in C or new in C++
* free() in C or delete in C++
* In the Dynamic allocation of memory space is allocated by using these functions when the value is returned by functions and assigned to pointer variables

## So what?!
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

* [When do I need dynamic memory?/ stackoverflow](https://stackoverflow.com/questions/12161774/when-do-i-need-dynamic-memory)
    1. When you need a lot of memory. Typical stack size is 1 MB, so anything bigger than 50-100KB should better be dynamically allocated, or you're risking crash. Some platforms can have this limit even lower.
    2. When the memory must live after the function returns. Stack memory gets destroyed when function ends, dynamic memory is freed when you want.
    3. When you're building a structure (like array, or graph) of size that is unknown (i.e. may get big), dynamically changes or is too hard to precalculate. Dynamic allocation allows your code to naturally request memory piece by piece at any moment and only when you need it. It is not possible to repeatedly request more and more stack space in a for loop.
* Worth to remember
    1. When I need a lots of memory
    2. When I use an array without constant value of size and vector
    3. When the memory must live after the function returns
    4. When I efficiently manage a memory
