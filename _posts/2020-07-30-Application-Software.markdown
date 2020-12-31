---
layout: post
title:  "Application Software"
date:   2020-07-30 22:07:43 +0900
categories: Quantitative_Analysis
---

<div style="text-align: center"><i><b>Last Updated on December 30th, 2020</b></i></div>

## What's the Application Software
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

* Application Software, [Wikipedia](https://en.wikipedia.org/wiki/Application_software)

## Windows API
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

* [나무위키](https://namu.wiki/w/Windows%20API)
## Call Convention
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

* __stdcall 
* [__cdecl vs __stdcall vs __fastcall](https://wendys.tistory.com/22)
    * __cdecl: Stack-based, caller clear
    * __stdcall: Stack-based, callee clear
    * __fastcall: Register-First, callee clear

## Call Sequence
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

* Query: 데이터베이스에 정보를 요청하는 것
* Trading Query: wmcaConnect(1) &rarr; wmcaQuery(n) &rarr; wmcaDisConnect(1)
* Realtime value Query: wmcaConnect(1) &rarr; (wmcaAttach + wmcaDetach) (n) &rarr; wmcaDisconnect(1)
* 한 번의 wmcaConnect 후에 할 일 다 끝내고 한 번의 wmcaDisconnect

## Library
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

* Library, [Wikipedia](https://en.wikipedia.org/wiki/Library_(computing))
A library is also a collection of implementations of behavior, written in terms of a language, that has a well-defined interface by which the behavior is invoked
* Linking, [Wikipedia](https://en.wikipedia.org/wiki/Linker_(computing))
Computer programs typically are composed of several parts or modules; these parts/modules need not all be contained within a single object file, and in such cases refer to each other by means of symbols as addresses into other modules, which are mapped into memory addresses when linked for execution. When a program comprises multiple object files, the linker combines these files into a unified executable program, resolving the symbols as it goes along.   
    * Linking
        * Dynamic linking & Static linking
        * [정적 라이브러리(lib) vs 동적 라이브러리(dll)](https://hsunnystory.tistory.com/109)
        * [dll과 ocx의 차이](https://m.blog.naver.com/PostView.nhn?blogId=jaylin9083&logNo=221447296093&proxyReferer=https:%2F%2Fwww.google.com%2F)
    * Relocation   
* 하나의 객체 파일은, 하나의 소스코드를 컴파일한 결과   
프로그램이 여러 개의 객체 파일으로 이루어져 있을 때, 그러한 파일들을 하나의 프로그램으로 연결시켜주기 위한 장치가 필요 -> Library   
라이브러리를 Dynamic하게 연결시켜주는 것(dll)과 Static하게 연결시켜주는 것(lib)에 차이 존재

## Microsoft Foundation Classes Library (MFC)
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

* Microsoft MFC Desktop Application, [Official Website](https://docs.microsoft.com/en-us/cpp/mfc/mfc-desktop-applications?redirectedfrom=MSDN&view=vs-2019)
* Microsoft Foundation Classes Library, [Wikipedia](https://en.wikipedia.org/wiki/Microsoft_Foundation_Class_Library)
* MFC, WIN32 API를 C++언어의 클래스화한 라이브러리 (기존의 C언어로 이루어진 WIN32 API에 Object-oriented Paradigm을 적용)
* [나무위키](https://namu.wiki/w/MFC)
* [Visual Studio에서 C/C++ DLL 만들기](https://docs.microsoft.com/ko-kr/cpp/build/dlls-in-visual-cpp?view=vs-2019)
* [Visual Studio 외부 DLL 경로(path) 추가하기](https://m.blog.naver.com/PostView.nhn?blogId=sharonichoya&logNo=220817543315&proxyReferer=https:%2F%2Fwww.google.com%2F)

## Qt
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

* [나무위키](https://namu.wiki/w/Qt(%ED%94%84%EB%A0%88%EC%9E%84%EC%9B%8C%ED%81%AC)
* 개발 편의성 + 타 언어로의 Porting(계획은 아직 없음)
* 크로스 플랫폼이기는 하지만, 주어진 API가 WIN32 API 기반이라서 우선은 Windows기반의 프로그램 제작 예정

