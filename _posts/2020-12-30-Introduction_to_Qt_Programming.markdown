---
layout: post
title:  "Introduction to Qt Programming"
date:   2020-12-30 12:00:00 +0900
categories: Quantitative_Analysis
---

<div style="text-align: center"><i><b>Last Updated on December 31th, 2020</b></i></div>

## Temporarily cease this project because analyzing charts will be bringing more opportunities to earn the money than this :D 
## Qt
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

* 오픈 소스 C++ 개발 크로스 플랫폼 프레임워크
* Qt Creator: Qt 프레임워크 개발을 위한 IDE
* QML (Qt Modeling Language): Interface 구현을 위한 언어
* [Qt 처음 시작하기 (Official Website)](https://doc.qt.io/qt-5/gettingstarted.html)
* [Qt reference documentation (Official Website)](https://doc.qt.io/qt-5/reference-overview.html)
* [Introduction to Qt Programming (Youtube)](https://www.youtube.com/watch?v=6KtOzh0StTc&list=PL2D1942A4688E9D63)
* 20201230 01강 시작   
    * Console Application vs GUI Application
    * main.cpp vs mainwindow.cpp & .h & .ui
    * namespace Ui
    * Q_OBJECT: Every thing in Qt stems from Q_OBJECT
    * Qt makes pointers insanely easy to work with
    * F1 &rarr; Reference Documentation
    * Ui Design에서 Toolbar (Edit widget, Edit signals and slots, Horizontal or Vertical Adjust, etc.)
    * QObject::connect(const QObject *sender, const char* signal, const QObject *receiver, const char* method, Qt::ConnectionType type = Qt::AutoConnection), QObject::disconnect도 동일하게 적용
    * 5강까지 시청완료
* 이정도 UI는 구현가능하긴한데,   
    <img src="/img/example_qt.JPG">   
1. 계획하는 Program의 수준이 그렇게 높은 게 아니라, 혹자들이 말하는 "Qt를 사용함으로써 얻는 개발의 편의성"을 아직 못 느끼겠다   (MFC로 위 사진정도의 UI는 구현해봤을 때 ㅇㅇ) &#128514;&#128514; 
2. Shared library를 어떻게 Dynamically link하는 지 잘 모르겠다 &rarr; API를 쓰지를 못한다
Visual Studio에서는 환경변수 쪽 Path를 수정해주면 됐었는데 [(link)](https://m.blog.naver.com/PostView.nhn?blogId=sharonichoya&logNo=220817543315&proxyReferer=https:%2F%2Fwww.google.com%2F), 분명 쓰는 방법은 있을텐데 구글링해봐도 진전이 없다   
3. MFC기반 예제다보니, dll 내에서 afx관련 함수가 쓰이면 runtime error가 날 거 같다
4. MFC기반이라 Connect, Disconnect, Query, Request 등등 서버에 Query를 날리는 함수의 경우 현재의 HWND(Event를 처리)를 인자로 사용하는데, Qt에서는 QObject가 Event를 처리하니 HWND에 넣을 인자를 뭘 써야하는 지 모르겠다
HWND를 정의하자니 비효율적인 거 같고, Reference Documentation에서 QObject member function 찾아봐도 마땅한 대안을 찾지 못하겠고   
5. 굳이 Qt를 써야하는 이유를 누군가가 묻는다면, 대답할 말이 없다
&rarr; MFC를 기반으로 Dialog를 수정하면서 개발해보자 &#128293;&#128293;