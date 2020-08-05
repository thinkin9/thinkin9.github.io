---
layout: post
title:  "Application Programming Interface"
date:   2020-07-31 01:10:01 +0900
categories: Quantitative_Analysis
---

<div style="text-align: center"><i><b>Last Updated on July 31th, 2020</b></i></div>

## What's the Application Programming Interface
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

* Application Programming Interface, [Wikipedia](https://en.wikipedia.org/wiki/Application_programming_interface)
An application programming interface (API) is a computing interface which defines interactions between multiple software intermediaries.
* Developers have to design both backend and front

## OpenAPI Library Configuration
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

* wmca.dll: 통신 Library dll 함수 인터페이스를 제공하는 파일로서 서비스 주요파일 (필수)
* wmca.ini: 접속 서버 및 포트등을 지정할 수 있는 파일이며 지정할 내용이 없을 경우 이 파일은 사용하지 않아도 됨
* sk*.dll, nsldap32v11.dll: 공인인증을 위해 SignKorea(코스콤 공인인증센터)에서 제공하는 라이브러리이며 (필수)
* sha256w32.dll: 암호화 라이브러리 (필수)

## Function
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">