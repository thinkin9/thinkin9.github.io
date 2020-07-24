---
layout: post
title:  "Required Knowledge"
date:   2020-07-24 17:41:55 +0900
categories: Quantitative_Analysis
---

<div style="text-align: center"><i><b>Last Updated on July 24th, 2020</b></i></div>

## Contents
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

1. What is Quantitative Research?
2. Goal
3. Language
4. API
5. Reference

## What is Quantitative Research?
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

* Quantitative Research, [Wikipedia](https://en.wikipedia.org/wiki/Quantitative_research)

## Goal
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

* Quantitative analysis of company
    * Find the underrated company in stock market    
    저평가된 회사 발굴
    * Evaluate a proper stock price    
    주식의 적정가를 책정

* Automatic Trading Bot 
    * Develop machine which automatically buy and sell the stock based on the proper stock price    
    책정한 적정가를 바탕으로 자동 거래 BOT 개발
    * Detect buy and sell signal from pump-and-dump party based on chart, trading volume, tick data, etc. ([pump-and-dump, Wikipedia](https://en.wikipedia.org/wiki/Pump_and_dump))    
    차트, 거래량, 틱데이터를 기반으로 작전세력 매수 및 매도 신호 포착 후 대응 

## Programming Language
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

* Quantitative analysis with Python
    * It analyze the static data, not the dynamic one
    * Compatibiliy with [mongo DB](https://www.mongodb.com/https://www.mongodb.com/)
* Automatic Trading Bot with C++
    * It analyze the dynamic data, not the static one
    * More faster than Python
    * It can respond more quickly to the buy or sell signal
    
## Aplication Programming Interface, API
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

* There are a lot of brokerage firm in South Korea
* Some brokerage firms which want to expand there clients give free-commission event to clients who open a untact bank account
* Hence, I select [NH INVESTMENT & SECURITIES CO.,LTD.](https://www.nhqv.com/) which is the only firm servicing the API with C++
    * But, few clients use this API, then it is difficult to find information and build an application with it
    * That's why I have been writing these series of post :smile:

## Reference
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">