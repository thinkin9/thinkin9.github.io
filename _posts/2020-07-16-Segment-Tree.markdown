---
layout: post
title:  "Segment Tree"
date:   2020-07-16 12:39:55 +0900
categories: Data_Structure
---

<div style="text-align: center"><i><b>Last Updated on July 16th, 2020</b></i></div>

## Segment Tree, 세그먼트 트리
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

* [세그먼트 트리, BOJ](https://www.acmicpc.net/blog/view/9)
* [[구간쿼리] 세그먼트 트리, JusticeHui](https://justicehui.github.io/medium-algorithm/2018/08/24/Seg1/)
* Efficient method to find sum, multiplication, maximum, or minimum of specific range, rather than naive method
* O(logN) while naive method and array of sum method have O(MN) as time complexity
* Be implemented by using Binary Tree
* What value(data) is stored in each node depends on the circumstance of problem
    * Sum
    * Multiplication
    * Maximum
    * Minimum
* Problem Solving
    * [Tag: segtree @ Solved.ac](https://solved.ac/problems/tags/segtree)
    * [2042, 구간 합 구하기 (P5)](https://www.acmicpc.net/problem/2042)
    * [10999, 구간 합 구하기 2 (P4)](https://www.acmicpc.net/problem/10999)
    * [10868, 최솟값 (P5)](https://www.acmicpc.net/problem/10868)
    * [2357, 최솟값과 최댓값 (P5)](https://www.acmicpc.net/problem/2357)
    * [7578, 공장 (P5)](https://www.acmicpc.net/problem/7578) - [Inverse Counting](https://justicehui.github.io/koi/2018/11/20/BOJ7578/)