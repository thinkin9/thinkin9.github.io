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
  
  ```cpp
  // 1. Bottom-up (부분에서의 최소 보장, 전역에서의 최소 보장)
  
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
  
  // 2. Top-bottom (Optimal Value of n가 solve(n / 2) + n % 2 + 1 또는 solve(n / 3) + n % 3 + 1)   
  // 일반적인 상황에서 2 혹은 3의 배수가 되는 길을 찾는 게 수를 가장 빠르게 줄이기에 적합하다   
  // n이 그 자체로 2의 배수나 3의 배수일 수도 있고,   
  // 1을 빼서 2의 배수나, 3의 배수가 될 경우도 있고,   
  // 2를 빼서 3의 배수가 될 경우도 있다   
  
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
  
  ```cpp
  // 1. Bottom-up   
  // 서로 겹치지 않기 위해서는 arr[i-2]에서 가로로 2개 + arr[i-1]에서 세로로 1개 
  
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
  
  ```cpp
  // 1. Bottom-up   
  // 서로 겹치지 않기 위해서는 arr[i-2]에서 가로로 2개 큰거 하나 + arr[i-1]에서 세로로 1개 
  
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
  
  // Time Limit   
  
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
  
* [9095, 1, 2, 3 더하기](https://www.acmicpc.net/problem/9095)   

  ```cpp
  int arr[11];
  int n, ans, buf;

  int main(){
    ios_base::sync_with_stdio(false);
    cin.tie(0);
    arr[1] = 1;
    arr[2] = 2;
    arr[3] = 4;
    for(int i = 4; i <= 10; i++){
      arr[i] = arr[i - 3] + arr[i - 2] + arr[i - 1];
    }
    cin >> n;
    while(n--){
      cin >> buf;
      cout << arr[buf] << '\n';
    }
    return 0;
  }
  ```
* [10844, 쉬운 계단수](https://www.acmicpc.net/problem/10844)  

  ```cpp
  const int MOD = 1e9;
  int arr[101][10];
  int n, ans, buf;
  ll nll, ansll, bufll;

  int main(){
    ios_base::sync_with_stdio(false);
    cin.tie(0);
    cin >> n;
    for(int& i : arr[1]){
      i = 1;
    }
    arr[1][0] = 0;
    for(int i = 1; i < n; i++){
      for(int j = 0; j < 10; j++){
        // 위로 올라갈 수 있는 digit 0 ~ 8
        if(j <= 8) {
          arr[i + 1][j + 1] += arr[i][j];
          arr[i + 1][j + 1] %= MOD;
        }
        // 아래로 내려갈 수 있는 digit 1 ~ 9
        if(j >= 1) {
          arr[i + 1][j - 1] += arr[i][j];
          arr[i + 1][j - 1] %= MOD;
        }
      }
    }
    for(int i = 0; i <= 9; i++){
      ansll += arr[n][i];
      ansll %= MOD;
    }
    cout << ansll;
  }
  ```
  
* [11057, 오르막수](https://www.acmicpc.net/problem/11057)  
  ```cpp
  const int MOD = 1e4 + 7;
  int arr[1001][10];
  int n, ans, buf;
  ll nll, ansll, bufll;

  int main(){
    ios_base::sync_with_stdio(false);
    cin.tie(0);
    cin >> n;
    for(int& i : arr[1]){
      i = 1;
    }
    for(int i = 2; i <= n; i++){
      for(int j = 0; j < 10; j++){
        for(int k = 0; k <= j; k++){
          arr[i][j] += arr[i - 1][k];
          arr[i][j] %= MOD;
        }
      }
    }
    for(int i = 0; i < 10; i++){
      ansll += arr[n][i];
      ansll %= MOD;
    }
    cout << ansll;
  }
  ```
* [2193, 이친수](https://www.acmicpc.net/problem/2193) 
  ```cpp
  ll arr[91][2];
  int n, ans, buf;
  ll nll, ansll, bufll;

  int main(){
    ios_base::sync_with_stdio(false);
    cin.tie(0);
    cin >> n;
    arr[1][0] = 0;
    arr[1][1] = 1;
    for(int i = 2; i <= n; i++){
      // n번째가 0으로 끝나면 n-1번째는 무조건 0 or 1
      arr[i][0] = arr[i - 1][0] + arr[i - 1][1];
      // n번째가 1으로 끝나면 n-1번째는 무조건 0
      arr[i][1] = arr[i - 1][0];
    }
    cout << arr[n][0] + arr[n][1];
  }
  
  ll arr[91];
  int n, ans, buf;
  ll nll, ansll, bufll;

  int main(){
    ios_base::sync_with_stdio(false);
    cin.tie(0);
    cin >> n;
    arr[1] = 1;  // 1
    arr[2] = 1;  // 10
    for(int i = 3; i <= n; i++){
      // n번째 수가 0인 수열을 만드는 방법은 n-1번째 수가 0 or 1일 경우이므로(+ 0), arr[n-1]과 같다.
      // n번째 수가 1인 수열을 만드는 방법은 n-2번째 수가 0 or 1일 경우이므로(+ 01), arr[n-2]과 같다
      arr[i] = arr[i - 1] + arr[i - 2];
    }
    // Fibonacci는 47번째부터 int 범위를 초과한다
    cout << arr[n];
    return 0;
  }
  ```
* [9465, 스티커](https://www.acmicpc.net/problem/9465)  
  ```cpp
  const int MAX = 1e5;
  int a[MAX + 1][2];
  int a2[MAX + 1][3];
  int n, ans, buf;
  ll nll, ansll, bufll;

  void solve(){
    cin >> buf;
    for(int i = 0; i < 2; i++){
      for(int j = 0; j < buf; j++){
        cin >> a[j][i];
      }
    }
    a2[0][0] = 0;
    a2[0][1] = a[0][0];
    a2[0][2] = a[0][1];

    for(int i = 1; i < buf; i++){
      a2[i][0] = max({a2[i - 1][0], a2[i - 1][1], a2[i - 1][2]});
      a2[i][1] = max({a2[i - 1][0], a2[i - 1][2]}) + a[i][0];
      a2[i][2] = max({a2[i - 1][0], a2[i - 1][1]}) + a[i][1];
    }
    buf--;
    cout << max({a2[buf][0], a2[buf][1], a2[buf][2]}) << '\n';
    return;
  }

  int main(){
    ios_base::sync_with_stdio(false);
    cin.tie(0);
    cin >> n;
    while(n--){
      solve();
    }
    return 0;
  }
  ```
* [](https://www.acmicpc.net/problem/) 
* [](https://www.acmicpc.net/problem/) 
* [](https://www.acmicpc.net/problem/) 
