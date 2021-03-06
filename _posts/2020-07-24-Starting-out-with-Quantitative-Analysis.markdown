---
layout: post
title:  "Starting out with Quantitative Analysis"
date:   2020-07-24 17:41:55 +0900
categories: Quantitative_Analysis
---

<div style="text-align: center"><i><b>Last Updated on July 30th, 2020</b></i></div>

## What is Quantitative Research?
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

* Quantitative Research, [Wikipedia](https://en.wikipedia.org/wiki/Quantitative_research)

## Goal
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

1. Quantitative analysis of company
    1. Find the underrated company in stock market    
    저평가된 회사 발굴
    2. Evaluate a proper stock price    
    주식의 적정가를 책정

2. Automatic Trading Bot
    1. Develop automatic machine   
    책정한 적정가를 바탕으로 자동 매매
    2. Short-term (1 ~ 5 Day) swing trading, (Swing trading, [Wikipedia](https://en.wikipedia.org/wiki/Swing_trading))    
    1일 ~ 5일 이내의 단기 저점 및 단기 고점을 파악하여 Swing trading
    3. Detect buy and sell signals based on chart, trading volume, tick data, etc.     
    차트, 거래량, 틱데이터 등을 기반으로 외인, 기관, 세력의 매수 및 매도 신호 포착 후 대응

## Programming language
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

1. Quantitative analysis with Python
    * It analyze the static data, not the dynamic one
    * Compatibiliy with [mongo DB](https://www.mongodb.com/https://www.mongodb.com/)
2. Automatic Trading Bot with C++
    * More faster than Python
    * It analyze the dynamic data, not the static one
    * It can respond more quickly to the buy or sell signal
    
## Aplication Programming Interface(API) Selection
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

* There are a lot of brokerage firm in South Korea
* Some brokerage firms which want to expand there clients currently give free-commission event to clients who open a untact bank account
* Since I want to programming with C++ API, I select [NH INVESTMENT & SECURITIES CO.,LTD.](https://www.nhqv.com/) which is the only firm serving C++ API
    * But, few clients use this API, then it is difficult to find information and build an application with it
    * That's why I have been writing these series of post :D

## Module Configuration
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

* Quantitative analysis with Python 
    <img src="/img/QA.JPG">   

* Automatic Trading Bot with C++    
    <img src="/img/ATB.JPG">   