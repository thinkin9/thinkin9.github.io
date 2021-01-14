---
layout: post
title:  "Codeforces Educational Round #101 (Div.2)"
date:   2021-01-10 12:00:00 +0900
categories: Records
---

<div style="text-align: center"><i><b>Last Updated on January 10th, 2021</b></i></div>

## Lesson
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

## [A. Regular Bracket Sequence](http://codeforces.com/contest/1469/problem/A)
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

3. **Code**
    ```cpp
    #include<iostream>
    #include<string>
    using namespace std;

    int T;
    string str;

    void solve() {
        cin >> str;
        if (str[0] == ')' || str[str.size() - 1] == '(') {
            cout << "NO" << '\n';
        }
        else if (str.size() % 2 == 1) {
            cout << "NO" << '\n';
        }
        else {
            cout << "YES" << '\n';
        }
        return;
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

## [B. Red and Blue](http://codeforces.com/contest/1469/problem/B)
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

3. **Code**
    ```cpp
    #include<iostream>
    #include<vector>
    #include<algorithm>
    using namespace std;

    int T, N, M;

    void solve() {
        cin >> N;
        vector<int> r(N + 1);
        int num;
        for (int i = 1; i <= N; i++) {
            cin >> num;
            r[i] = r[i - 1] + num;
        }

        cin >> M;
        vector<int> b(M + 1);
        for (int i = 1; i <= M; i++) {
            cin >> num;
            b[i] = b[i - 1] + num;
        }

        cout << *max_element(r.begin(), r.end()) + *max_element(b.begin(), b.end()) << '\n';
        return;
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