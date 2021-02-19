---
layout: post
title:  "Codeforces Round #690 (Div.2)"
date:   2020-12-28 12:00:00 +0900
categories: Records
---

<div style="text-align: center"><i><b>Last Updated on December 28th, 2020</b></i></div>

## [A. Favorite Sequence](http://codeforces.com/contest/1462/problem/A)
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

1. **Condition**
    * Sequence : a1 a2 a3 ... an-1 an (consisting of n)
    * Favorite Sequence : a1 a3 a5 ... a6 a4 a2 (consisting of n)
    * Infer the original sequence from the given favorite sequence
2. **Thinkin9**
    * Fisrt n/2 sequence to queue
    * Last n/2 sequence to stack
3. **Code**   
    ```cpp
    #include<iostream>
    #include<queue>
    #include<stack>
    #include<string>
    using namespace std;

    int main() {
        ios_base::sync_with_stdio(false); cin.tie(nullptr);

        int t;
        cin >> t;

        while (t--) {
            int n;
            cin >> n;

            queue<int> q;
            stack<int> s;

            for (int i = 0; i < n; i++) {
                int num;
                cin >> num;
                if (i < n / 2) q.push(num);
                else s.push(num);
            }
            
            for (int i = 0; i < n; i++) {
                if (i % 2 == 0 && !q.empty()) {
                    cout << q.front() << ' ';
                    q.pop();
                }
                else {
                    cout << s.top() << ' ';
                    s.pop();
                }
            }
            cout << '\n';
        }
        return 0;
    }
    ```

## [B. Last Year's Substring](http://codeforces.com/contest/1462/problem/B)
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

1. **Condition**
    * string consisting of n decimal digits: s1 s2 s3 ... sn-1 sn
    * At most once he can perform the operation that removes from the ith digit to jth digit
    * Determine whether the given string can be converted to the "2020"
2. **Thinkin9**
    * Classification
        * 2020
        * 2 + 020
        * 20 + 20
        * 202 + 0
    * He only can perform the operation once   
    Case matching have to happen to the first digit(s) or the last digit(s)
3. **Code**   
    ```cpp
    #include<iostream>
    #include<string>
    using namespace std;

    int main() {
        ios_base::sync_with_stdio(false); cin.tie(nullptr);

        int t;
        cin >> t;

        while (t--) {
            int n;
            cin >> n;

            string str;
            cin >> str;

            if (str.substr(0, 4) == "2020" || str.substr(str.size() - 4, 4) == "2020") {
                cout << "YES" << '\n';
                continue;
            }

            if (str.substr(0, 1) == "2") {
                if (str.substr(str.size() - 3, 3) == "020") {
                    cout << "YES" << '\n';
                    continue;
                }
            }

            if (str.substr(0, 2) == "20") {
                if (str.substr(str.size() - 2, 2) == "20") {
                    cout << "YES" << '\n';
                    continue;
                }
            }

            if (str.substr(0, 3) == "202") {
                if (str.substr(str.size() - 1, 1) == "0") {
                    cout << "YES" << '\n';
                    continue;
                }
            }

            cout << "NO" << '\n';
        }
        return 0;
    }
    ```

## [C. Unique Number](http://codeforces.com/contest/1462/problem/C)
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

1. **Condition**
    * Find the smallest positive integer number that has the sum of digits equal to x and all digits are distinct (unique)
2. **Thinkin9**
    * Maximum number of x is 45 (1+2+3+4+5+6+7+8+9)
    * 1 Match with the largest possible number, k
    * 2 push k to the stack
    * 3 subtract k from x, then goto 1 
3. **Code**   
    ```cpp
    #include<iostream>
    #include<string>
    #include<stack>
    #include<cstring>
    using namespace std;

    int check[10];

    int main() {
        ios_base::sync_with_stdio(false); cin.tie(nullptr);

        int t;
        cin >> t;

        while (t--) {
            memset(check, 0, sizeof(check));
            int num;
            cin >> num;

            stack<int> s;

            if (num > 45) {
                cout << -1 << '\n';
                continue;
            }
            else if (1 <= num && num < 10) {
                cout << num << '\n';
                continue;
            }

            while (num != 0) {
                for (int i = 9; i > 0; i--) {
                    if (!check[i] && num - i >= 0) {
                        s.push(i);
                        check[i] = 1;
                        num -= i;
                    }
                }
            }

            while (!s.empty()) {
                cout << s.top();
                s.pop();
            }
            cout << '\n';
        }
        return 0;
    }
    ```