---
layout: post
title:  "Codeforces Round #689 (Div.2)"
date:   2020-12-26 12:00:00 +0900
categories: Records
---

<div style="text-align: center"><i><b>Last Updated on December 27th, 2020</b></i></div>

## [A. String Generation](http://codeforces.com/contest/1461/problem/A)
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

1. **Condition**
    * the string may only contain characters 'a', 'b', or 'c'
    * the maximum length of a substring of this string that is a palindrome does not exceed k
2. **Thinkin9**
    * There is no case that has a substring palindrome if the order of string is sequential repeated   
    Because the string is ordered repeatedly through three different characters, 'a', 'b', and 'c'   
3. **Code**   
    ```cpp
    #include<iostream>
    #include<string>
    using namespace std;

    char ch[3] = { 'a', 'b', 'c' };

    int main() {
        ios_base::sync_with_stdio(false); cin.tie(nullptr);

        int n;
        cin >> n;

        while (n--) {
            string str;
            int a, b;
            cin >> a >> b;
            for (int i = 0; i < a; i++) {
                str += ch[i % 3];
            } 
            cout << str << '\n';
        }

        return 0;
    }
    ```

## [B. Find the Spruce](http://codeforces.com/contest/1461/problem/B)
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

1. **Condition**
    * All cells in the set contain an "*" which denotes an origin point of spruce tree
    * For each 1 ≤ i ≤ k all cells with the row number x + i − 1 and columns in range [y − i + 1, y + i − 1] must be a part of the set

2. **Thinkin9**
    * Checking all entries from the given origin point of spruce tree is inefficient   
    How do I reduce the time to check entries of which row number is x + i - 1, where 1 ≤ i ≤ k
    * Need a new array or vector to mark what number of sequential cells are filled with '*'      
    In this way, we just have to check only one entry to determine whether or not to make a spruce tree   
3. **Code**   
    ```cpp
    #include<iostream>
    #include<vector>
    using namespace std;

    int main() {
        ios_base::sync_with_stdio(false);cin.tie(nullptr);

        int n;
        cin >> n;

        while (n--) {
            int n, m;
            cin >> n >> m;

            vector<vector<char>> data(n, vector<char>(m)); // Vector for data
            vector<vector<int>> seq(n, vector<int>(m)); // Vector for what number of sequential cells are filled with '*'

            //e.g.  .***. => 0 1 2 3 0   
            //      *****    1 2 3 4 5
            //      *****    1 2 3 4 5
            //      *.*.*    1 0 1 0 1

            // 위 경우에서 data[0][1]을 origin point로 하는 spruce tree를 찾기 위해서
            // seq[i + k - 1][j + k - 1]이 주어진 높이에 따라서 요구되는 "연속하는 '*'의 개수"를 충족하는지 확인하면 된다.

            for (int i = 0; i < n; i++) {
                for (int j = 0; j < m; j++) {
                    cin >> data[i][j];
                    if (data[i][j] == '*') {
                        if (j == 0) seq[i][j] = 1;
                        else seq[i][j] = seq[i][j - 1] + 1;
                    }
                    else seq[i][j] = 0;
                }
            }

            int ans = 0;
            for (int i = 0; i < n; i++) {
                for (int j = 0; j < m; j++) {
                    if (data[i][j] == '*') {
                        // k == 1 is trivial => Just increment
                        ans++;
                        // Start with k = 2
                        int k = 2;
                        while (i + k - 1 < n && data[i + k - 1][j] == '*') {
                            if (j + k - 1 < m && seq[i + k - 1][j + k - 1] >= 2 * k - 1) {
                                ans++;
                                k++;
                            }
                            else {
                                break;
                            }
                        }
                    }
                }
            }
            cout << ans << '\n';
        }
        return 0;
    }
    ```

## [C. Random Events](http://codeforces.com/contest/1461/problem/C)
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

1. **Condition**
    * A permutation of length n is an array consisting of n distinct integers from 1 to n in arbitrary order
    * Ron's permutation is subjected to m experiments of the following type: (ri, pi). This means that elements in range [1, ri] (in other words, the prefix of length ri) have to be sorted in ascending order with the probability of pi.
2. **Thinkin9**
    * Since the given permutation is from 1 to n in arbitrary order, we just need to know until which number we have to sort (Maximum index where the entry is not located in a proper location, for example, 4 1 3 2 5 6 ==> 4 1 3 2 is unsorted ==> 4) (Suppose that the index is starting from 1)
        * r < max_idx ==> It doesn't matter whether the experiment succeeds or not
        * r >= max_idx ==> Update the answer and remnant probability
        * max_idx == 0 means the given permutation have already been sorted
3. **Code**   
    ```cpp
    #include<iostream>
    #include<vector>
    #include<iomanip>
    using namespace std;

    int main() {
        ios_base::sync_with_stdio(false);cin.tie(nullptr);
        cout << fixed << setprecision(6);

        int n;
        cin >> n;

        while (n--) {
            int n, m;
            cin >> n >> m;
            vector<int> v(n + 1);
            int max_idx = 0;

            for (int i = 1; i <= n; i++) {
                cin >> v[i];
                if (v[i] != i) max_idx = i;
            }

            double ans = 0;
            double remain = 1;
            while (m--) {
                int r;
                double m;
                cin >> r >> m;
                if (r >= max_idx) {
                    ans += remain * m;
                    remain *= (1.0 - m);
                }
            }
            if (max_idx == 0) ans = 1.0;
            cout << ans << '\n';
        }
        return 0;
    }
    ```

## [D. Divide and Summarize](http://codeforces.com/contest/1461/problem/D)
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

1. **Condition**
    * An array has the ith prettiness if and only if a sum of elements is i
    * Likewise Quick Sort Algorithm, divide the given array and determine whether the subsequential array has the ith prettiness or not 

2. **Thinkin9**
    * Array division is akin to the Quick Sort Algorithm
    * Recursion
    * All possible prettiness into the unordered map
    * &lt;Algorithm&gt;   
    upper_bound(start, end, val): iterator to the position where val &lt; element   
    lower_bound(start, end, val): iterator to the position where element &le; val 
3. **Code**
    ```cpp
    #include<iostream>
    #include<algorithm>
    #include<unordered_map>
    using namespace std;

    typedef long long ll;
    const int N = 1e5 + 1;

    ll arr[N], sum[N];
    unordered_map <ll, int> unord_map;

    void qs(int start, int end) {
        // Update the unordered map
        unord_map[sum[end] - sum[start - 1]] = 1;
        
        if (start == end) return;

        // mid and the index of mid
        ll mid = (arr[start] + arr[end]) / 2; 
        int pos = upper_bound(arr + start, arr + end + 1, mid) - arr;
        
        if (pos > end) return;
        
        // Recursion
        qs(start, pos - 1);
        qs(pos, end);
    }

    int main() {
        ios_base::sync_with_stdio(false); cin.tie(nullptr);

        int t;
        cin >> t;
        while (t--) {
            unord_map.clear();
            int n, q;
            cin >> n >> q;
            for (int i = 1; i <= n; i++) {
                cin >> arr[i];
            }

            sort(arr + 1, arr + n + 1);
            
            for (int i = 1; i <= n; i++) {
                sum[i] = sum[i - 1] + arr[i];
            }

            qs(1, n);

            while (q--) {
                int num;
                cin >> num;
                if (unord_map[num]) cout << "Yes" << '\n';
                else cout << "No" << '\n';
            }
        }
        return 0;
    }
    ```