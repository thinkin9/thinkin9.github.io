---
layout: post
title:  "Valgrind and Ghidra"
date:   2020-09-03 08:14:42 +0900
categories: C/C++
---

<div style="text-align: center"><i><b>Last Updated on September 3rd, 2020</b></i></div>

## Valgrind
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

* [Official Website](https://valgrind.org/)
* Valgrind is an instrumentation framework for building dynamic analysis tools. There are Valgrind tools that can automatically detect many memory management and threading bugs, and profile your programs in detail.

## Usage
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

* [The Valgrind Quick Start Guide](https://www.valgrind.org/docs/manual/quick-start.html#quick-start.intro)
* $ valgrind ./main <img src="/img/val1.jpg">
* $ valgrind --leak-check=yes ./main (More detailed with compile option '-g') <img src="/img/val2.jpg">
* $ valgrind --leak-check=full --trace-children=yes ./main
    * 기본적으로 로드한 동적 라이브러리의 메모리 누수는 확인하지 않는다
    * 위와 같은 Option을 적어주어야한다

## Ghidra
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

* [Official Website](https://ghidra-sre.org/)
* Ghidra is a software reverse engineering (SRE) framework created and maintained by the National Security Agency Research Directorate. This framework includes a suite of full-featured, high-end software analysis tools that enable users to analyze compiled code on a variety of platforms including Windows, macOS, and Linux. Capabilities include disassembly, assembly, decompilation, graphing, and scripting, along with hundreds of other features. Ghidra supports a wide variety of processor instruction sets and executable formats and can be run in both user-interactive and automated modes. Users may also develop their own Ghidra plug-in components and/or scripts using Java or Python.
* In support of NSA's Cybersecurity mission, Ghidra was built to solve scaling and teaming problems on complex SRE efforts, and to provide a customizable and extensible SRE research platform. NSA has applied Ghidra SRE capabilities to a variety of problems that involve analyzing malicious code and generating deep insights for SRE analysts who seek a better understanding of potential vulnerabilities in networks and systems.

## Usage
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

* [기드라(Ghidra) 디버깅 툴 설치 및 기본 사용 방법 written by ndb796](https://ndb796.tistory.com/323)


