---
layout: post
title:  "Learn about Technical Indicators"
date:   2020-07-31 10:10:37 +0900
categories: Quantitative_Analysis
---

<div style="text-align: center"><i><b>Last Updated on July 31th, 2020</b></i></div>

## Movement Indicator
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

## Momentum Indicator
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

1. Stochastic Oscillator
    * Stochastic oscillator, [Wikipedia](https://en.wikipedia.org/wiki/Stochastic_oscillator)   
    [Fast Stochastic vs Slow Stochastic](https://www.diffen.com/difference/Fast_Stochastic_vs_Slow_Stochastic)
    * Concept
    Stochastic oscillator is a momentum indicator that uses support and resistance levels.
    * Meaning
        * The term stochastic refers to the point of a current price in relation to its price range over a period of time   
        * The current security's price is then expressed as a percentage of this range with 0% indicating the bottom of the range and 100% indicating the upper limits of the range over the time period covered. The idea behind this indicator is that prices tend to close near the extremes of the recent range before turning points.
    * Fundamental Formula (N = 5 and m = 3)
        <img src="/img/STF.svg">
        <img src="/img/STS.svg">
    * Parameter
        * N, last N days
        * m, m-period SMA of Fast %K == Fast %D
        * t, t-period SMA of Fast %K == Slow %K   
        t-period SMA of Fast %D == Slow %D
    * Type
        * Fast Stochastic(N, m)   
        Fast %K = %K basic calculation for last N days   
        Fast %D = m-period SMA of Fast %K   
        그래프의 변동성이 크고 노이즈가 많아 거의 사용하지 않음
        * Slow Stochastic(N, m, t)   
        Slow %K = Fast %K for last N days smoothed with t-period SMA   
        Slow %D = t-period SMA of Fast %D   
        Fast Stochastic에 Simple Moving Average (SMA)를 적용함
    * Analysis
        * 매수세가 증가할 경우(%K 증가) %K의 이동평균선인 %D를 뚫고 올라오는 형태 == 골든크로스 == 매수 신호
        * 매도세가 증가할 경우(%K 감소) %K의 이동평균선인 %D를 뚫고 내려가는 형태 == 데드크로스 == 매도 신호

## Volume Indicator
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

1. Bollinger Bands
    * Bollinger Bands, [Wikipedia](https://en.wikipedia.org/wiki/Bollinger_Bands)