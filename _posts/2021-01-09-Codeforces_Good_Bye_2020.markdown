---
layout: post
title:  "Codeforces Good Bye 2020"
date:   2021-01-09 12:00:00 +0900
categories: Records
---

<div style="text-align: center"><i><b>Last Updated on January 9th, 2021</b></i></div>

## Lesson
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

* 쉬운 문제를 복잡하게 생각하지 않고 간단한 Logic으로 풀어내는 연습이 필요
* 기술부채를 낮추기 위한 다양한 Solving method에 대한 학습이 필요

## [A. Bovine Dilemma](http://codeforces.com/contest/1466/problem/A)
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

3. **Code**
    ```cpp
    #include<iostream>
    #include<vector>
    #include<unordered_set>
    using namespace std;

    int T, N, X;

    void solve() {
        vector<int> v;
        unordered_set<int> unset;
        cin >> N;

        for (int i = 0; i < N; i++) {
            cin >> X;
            v.push_back(X);
        }

        for (int i = 0; i < N; i++) {
            for (int j = i + 1; j < N; j++) {
                unset.insert((v[i] - v[j] >= 0 ? v[i] - v[j] : v[j] - v[i]));
            }
        }

        cout << unset.size() << '\n';
    }
    int main() {
        ios_base::sync_with_stdio(false); cin.tie(nullptr);
        cin >> T;
        while (T--) {
            solve();
        }
        return 0;
    }
    ```

## [B. Last minute enhancements](http://codeforces.com/contest/1466/problem/B)
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

3. **Code**
    ```cpp
    #include<iostream>
    #include<vector>
    #include<unordered_set>
    using namespace std;

    int T, N, X;

    void solve() {
        vector<int> v;
        unordered_set<int> unset;
        cin >> N;

        v.push_back(0);
        for (int i = 0; i < N; i++) {
            cin >> X;
            v.push_back(X);
        }
        v.push_back(0);

        for (int i = 1; i <= N; i++) {
            if (v[i - 1] == v[i] && v[i] != v[i + 1]) {
                v[i]++;
            }
            unset.insert(v[i]);
        }

        cout << unset.size() << '\n';
    }

    int main() {
        ios_base::sync_with_stdio(false); cin.tie(nullptr);
        cin >> T;
        while (T--) {
            solve();
        }
        return 0;
    }
    ```

## [C. Canine poetry](http://codeforces.com/contest/1466/problem/C)
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

3. **Code**
    ```cpp
    #include<iostream>
    #include<vector>
    #include<string>
    using namespace std;

    int T;

    void solve() {
        string str;
        cin >> str;
        int n = str.size();
        vector<bool> check(n);

        int ans = 0;

        for (int i = 0; i < n; i++) {
            if (!check[i]) {
                if (i + 1 <= n && str[i] == str[i + 1]) check[i + 1] = true, ans++;
                if (i + 2 <= n && str[i] == str[i + 2]) check[i + 2] = true, ans++;
            }
        }
        cout << ans << '\n';
    }

    int main() {
        ios_base::sync_with_stdio(false); cin.tie(nullptr);
        cin >> T;
        while (T--) {
            solve();
        }
        return 0;
    }
    ```

## [D. 13th Labour of Heracles](http://codeforces.com/contest/1466/problem/D)
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

3. **Code**
    ```cpp
    ```