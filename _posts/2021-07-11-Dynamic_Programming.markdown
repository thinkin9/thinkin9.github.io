---
layout: post
title:  "Dynamic Programming"
date:   2021-07-11 00:00:00 +0900
categories: Algorithm_and_Problem_Solving
---

<div style="text-align: center"><i><b>Last Updated on July 11th, 2021</b></i></div>

## Dynamic Programming
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

* 큰 문제를 끝나는 특정 조건이 성립할 때까지 나누어서 푸는 알고리즘
* Dynamic Programming의 두 가지 속성
  1. Overlapping Subproblem - 문제의 정답을 작은 문제의 정답으로부터 구할 수 있다. (e.g. Fibonacci)
  2. Optimal Substructure - 문제의 크기에 상관없이 어떤 한 문제의 정답은 일정하다.
  * DP에서는 각 문제를 한 번만 풀어야한다 (2)
  * 작은 문제의 정답으로 정답을 구할 수 있다 (1)
  * 따라서, Memorization을 한다
* DP의 구현 방식
  1. Top-down (주로 Recursion으로)
  2. Bottom-up (주로 Loop로)

## Problem Solving
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

* [1463, 1로 만들기](https://www.acmicpc.net/problem/1463)
1. Bottom-up (부분에서의 최소 보장, 전역에서의 최소 보장)   
  ```cpp
  const int MAX = 1e6;
  int arr[MAX + 1];
  int n, ans, buf;

  void solve(){
  cin >> n;
  for(int i = 2; i <= n; i++){
  int temp = arr[i - 1] + 1;
  if(!(i % 2)) temp = min(arr[i / 2] + 1, temp);
  if(!(i % 3)) temp = min(arr[i / 3] + 1, temp);
  arr[i] = temp;
  }
  cout << arr[n];
  }

  int main(){
  ios_base::sync_with_stdio(false);
  cin.tie(0);
  solve();
  return 0;
  }
  ```
2. Top-bottom (Optimal Value of n가 solve(n / 2) + n % 2 + 1 또는 solve(n / 3) + n % 3 + 1)   
일반적인 상황에서 2 혹은 3의 배수가 되는 길을 찾는 게 수를 가장 빠르게 줄이기에 적합하다   
n이 그 자체로 2의 배수나 3의 배수일 수도 있고,   
1을 빼서 2의 배수나, 3의 배수가 될 경우도 있고,   
2를 빼서 3의 배수가 될 경우도 있다   
  ```cpp
  int n, ans, buf;

  int solve(int n){
  return (n > 2 ? min(solve(n / 2) + n % 2, solve(n / 3) + n % 3) + 1 : 0);
  }

  int main(){
  ios_base::sync_with_stdio(false);
  cin.tie(0);
  cin >> n;
  cout << solve(n);
  return 0;
  }
  ```

* [11726, 2 * n 타일링](https://www.acmicpc.net/problem/11726)
1. Bottom-up   
서로 겹치지 않기 위해서는 arr[i-2]에서 가로로 2개 + arr[i-1]에서 세로로 1개   
  ```cpp
  const int MAX = 1e3;
  ll arr[MAX + 1];
  int n, ans, buf;

  void solve(){
  cin >> n;
  arr[1] = 1;
  arr[2] = 2;
  for(int i = 3; i <= n; i++){
  arr[i] = (arr[i - 2] + arr[i - 1]) % 10007;
  }
  cout << arr[n];
  }

  int main(){
  ios_base::sync_with_stdio(false);
  cin.tie(0);
  solve();
  return 0;
  }
  ```

* [11727, 2 * n 타일링 2](https://www.acmicpc.net/problem/11727)
1. Bottom-up   
서로 겹치지 않기 위해서는 arr[i-2]에서 가로로 2개 큰거 하나 + arr[i-1]에서 세로로 1개   
  ```cpp
  const int MAX = 1e3;
  ll arr[MAX + 1];
  int n, ans, buf;

  void solve(){
  cin >> n;
  arr[1] = 1;
  arr[2] = 2;
  for(int i = 3; i <= n; i++){
  arr[i] = (arr[i - 2] * 2 + arr[i - 1]) % 10007;
  }
  cout << arr[n];
  }

  int main(){
  ios_base::sync_with_stdio(false);
  cin.tie(0);
  solve();
  return 0;
  }
  ```   
Time Limit   
  ```cpp
  int n, ans, buf;

  int solve(int n){
  if(n == 1) return 1;
  if(n == 2) return 3;
  return (solve(n - 2) * 2 + solve(n - 1)) % 10007;
  }

  int main(){
  ios_base::sync_with_stdio(false);
  cin.tie(0);
  cin >> n;
  cout << solve(n);
  return 0;
  }
  ```
