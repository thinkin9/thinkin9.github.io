---
layout: post
title:  "Dijkstra and 0-1 BFS"
date:   2020-07-16 00:07:04 +0900
categories: Algorithm_and_Problem_Solving Data_Structure
---

<div style="text-align: center"><i><b>Last Updated on July 16th, 2020</b></i></div>

## Dijkstra, 다익스트라
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

* [[그래프] 다익스트라 알고리즘, JusticeHui](https://justicehui.github.io/medium-algorithm/2018/03/28/Dijkstra/)
* Find the shortest path from one vertex to the other vectices (All weight of edges must be positive)
* O(V&#178;) with Adjacent list
* O(E logV) with Priority queue (Binary heap)
* O(E + V logV) with Fibonacci heap
* Problem Solving
    * [1486 등산 (Platinum V)](https://www.acmicpc.net/problem/1486)   
    * [1854 Kth Shortest Path (Platinum V)](https://www.acmicpc.net/problem/1854)
    * [5719 Almost Shortest Path (Platinum V)](https://www.acmicpc.net/problem/5719)

## 0-1 BFS
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

* [[그래프] 0-1 BFS 알고리즘, JusticeHui](https://justicehui.github.io/medium-algorithm/2018/08/30/01BFS/)
* Optimize the Dijkstra algorithm if the weight of edges is only 0 or 1
* O(V + E) with deque
    * push_back if the weight of edge is 1 (Different level)
    * push_front if the weight of edge is 0 (Same leve)
* Problem Solving
    * [9376 Jailbreak (Platinum V)](https://www.acmicpc.net/problem/9376)