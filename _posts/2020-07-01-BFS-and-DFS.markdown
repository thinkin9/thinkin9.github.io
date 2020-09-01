---
layout: post
title:  "BFS and DFS"
date:   2020-07-01 15:37:22 +0900
categories: Algorithm_and_Problem_Solving Data_Structure
---

<div style="text-align: center"><i><b>Last Updated on July 9th, 2020</b></i></div>

참고: 13. Graph Algorithms, Data Structures and Algorithms in C++ - Michael T. Goodrich, Roberto Tamassia, David M. Mount (2011) [(Amazon)](https://www.amazon.com/Data-Structures-Algorithms-Michael-Goodrich/dp/0470383275)

## Graph
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

* A graph is a way of representing relationships that exist between pairs of objects

## Components
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

* *V, Vertex or Node*
* *E, Edge or Arc*
* *G, A set of vertices and collection of edges between pairs of vertices*
* *deg(v), the number of incident edges of v*
* *indeg(v), the number of incoming edges of v*
* *outdeg(v), the number of outgoing edges of v*

## Type
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

* Directed graph
* Undirected graph
* Mixed graph

## Operations
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

* Vertex object
    * operator*(): Return the element associated with u
    * incidentEdges(): Return an edge list of the edges incident on u
    * isAdjacentTo(v): Test whether vertices u and v are adjacent

* Edge object
    * operator*(): Return the element associated with e.
    * endVertices(): Return a vertex list containing e’s end vertices.
    * opposite(v): Return the end vertex of edge e distinct from vertex v; an error occurs if e is not incident on v.
    * isAdjacentTo(f): Test whether edges e and f are adjacent.
    * isIncidentOn(v): Test whether e is incident on v.

* Full graph ADT
    * vertices(): Return a vertex list of all the vertices of the graph.
    * edges(): Return an edge list of all the edges of the graph.
    * insertVertex(x): Insert and return a new vertex storing element x.
    * insertEdge(v,w,x): Insert and return a new undirected edge with end vertices v and w and storing element x.
    * eraseVertex(v): Remove vertex v and all its incident edges.
    * eraseEdge(e): Remove edge e.

## How to represent the graph?
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

The number of Vertices and Edges are V and E, respectively
* Adjacency-Matrix (인접행렬)
    * 2-dimensional array (Size: V X V)
    * a[i][j] = 1/ a[i][j] = *w*    
    <img src="/img/Adjacency_Matrix_1.JPG">   
    ```cpp
    #include <vector>
    vector<vector<int>> a(row, vector<int>(col));
    for (int i = 0; i < row; i++){
        for (int j = 0; j < col; j++){
        c   in >> a[i][j];
        }
    }
    ```
    ```cpp
    #include <vector>
    vector<vector<int>> a(row, vector<int>(col));
    for (int i = 0; i < row; i++){
        for (int j = 0; j < col; j++){
            cin >> a[i][j];
        }
    }
    ```
    * Operation and Time
    vertices *O(n)*   
    edges *O(m)*   
    endVertices, opposite *O(1)*   
    incidentEdges, isAdjacentTo *O(m)*   
    isIncidentOn *O(1)*   
    insertVertex, insertEdge, eraseEdge *O(1)*   
    eraseVertex *O(m)*   
    
<hr style="height: 2px; border:none; margin-bottom:0.5em; margin-left: 1em; padding: 0; background:black">

* Adjacency-List (인접리스트)
    * 연결된 정점을 리스트로 표현한다. 
    * 주로 크기를 동적으로 변경할 수 있는 vector (C++), list (Python)을 사용
    * a[i] = *v* or *(v,w)*    
    <img src="/img/Adjacency_List_1.JPG">   
    ```cpp
    #include <vector>
    vector<vector<int>> a(row, vector<int>());
    for (int i = 0; i < numofedges; i++){
        int x, y;
        cin >> x >> y;
        a[x].push_back(y);
        a[y].push_back(x);
    }
    ```
    ```cpp
    #include <vector>
    vector<vector<pair<int, int>>> a(row, vector<pair<int, int>>());
    for (int i = 0; i < numofedges; i++){
        int x, y, val;
        cin >> x >> y >> val;
        a[x].push_back(make_pair(y, val));
        a[y].push_back(make_pair(x, val));
    }
    ```
    * Operation and Time
    vertices *O(n)*   
    edges *O(n<sup>2</sup>)*   
    endVertices, opposite *O(1)*   
    isAdjacentTo, isIncidentOn *O(1)*   
    incidentEdges *O(n)*   
    insertEdge, eraseEdge *O(1)*   
    insertVertex, eraseVertex *O(n<sup>2</sup>)*   
        
<hr style="height: 2px; border:none; margin-bottom:0.5em; margin-left: 1em; padding: 0; background:black">

* Edge-List (간선리스트)
    * 간선을 모두 저장    
    <img src="/img/Edge_List_1.JPG">   
    ```cpp
    #include <vector>
    vector<pair<int, int>> a;
    vector<int> e(numofvertices);
    for (int i = 0; i < numofedges; i++){
        int x, y;
        cin >> x >> y;
        a.push_back(make_pair(x, y));
    }
    sort(a.begin(), a.end());
    for (int i = 0; i < numofedges; i++){
        cnt[e[i][0]]++;
    }
    for (int i = 1; i <= numofvertices; i++){
        cnt[i] += cnt[i - 1];
    }
    ```
    * Operation and Time
    vertices *O(n)*   
    edges *O(m)*   
    endVertices, opposite *O(1)*   
    incidentEdges, isAdjacentTo *O(m)*   
    isIncidentOn *O(1)*   
    insertVertex, insertEdge, eraseEdge *O(1)*   
    eraseVertex *O(m)*   

## Graph Traversals
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

1. Depth First Search, DFS   
	Non-Queue
    * *V×O(V)=O(V<sup>2</sup>)*
        ```cpp
        check[x] = true;
        for (int i = 1; i <= n; i++) {
            if (a[x][i] == 1 && check[x] == false) {
                dfs(i);
            }
        }
        ```

    * *O(V+E)=O(E)*
        ```cpp
        check[x] = true;
        for (int i = 0; i < a[x].size(); i++) {
            int y = a[x][i];
            if (check[y] == false) {
                dfs(y);
            }
        }
        ```

2. Breadth First Search, BFS   
	Queue
    * *O(V<sup>2</sup>)*
        ```cpp
        queue<int> q;
        check[x] = true;
        q.push(x);
        while (!q.empty()) {
            int x = q.front();
            q.pop();
            for (int i = 0; i < n; i++) {
                if (a[x][i] == 1 && check[i] == false) {
                check[i] = true;
                    q.push(i)
                }
            }
        }
        ```

    * *O(V+E)=O(E)*
        ```cpp
        queue<int> q;
        check[x] = true;
        q.push(x);
        while (!q.empty()) {
            int x = q.front();
            q.pop();
            for (int i = 0; i < a[x].size(); i++) {
                int y = a[x][i];
                if (check[y] == false) {
                    check[y] = true;
                    q.push(y);
                }
            }
        }  
        ```
    
## Cautions
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

* Selecting which traversal method to implement is based on the understanding of problem   
문제의 조건을 생각하며, BFS와 DFS 중 어느 방법으로 최적화할 수 있는지 생각해야한다

* Deciding where traversal method is implemented is also based on the understanding of problem   
Function으로 구현하여 사용하는 것과 Main에서 바로 구현하여 사용하는 것에는 미묘한 차이가 있다
