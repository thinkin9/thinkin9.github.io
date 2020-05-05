---
layout: post
title:  "How to use Git (Ongoing)"
date:   2020-05-05 15:03:24 +0900
categories: Basic
---
## Abstract
0. Reference: [https://rogerdudler.github.io/git-guide/](https://rogerdudler.github.io/git-guide/index.ko.html)
1. What's the Git?
2. Location
3. Branch
4. Merge

### 1. What's the Git?

### 2. Location
1. Local storage (e.g. Our computer)
2. Virtual storage (e.g. Github)
Since both storages are seperated, we can build up in local storage first then in virtual storage second.

To use branch process is effective in building up the prototype of program      
1. First Draft   
    * git clone /&lt;PATH&gt;   
    * git clone &lt;USERNAME&gt;@&lt;HOST&gt;:/&lt;PATH&gt;   
2. Debugging with branch   
    * &lt;PATH&gt; bundle exec jekyll serve   
      [http://127.0.0.1:4000/](http://127.0.0.1:4000/)
    * git checkout -b &lt;branch&gt; (-b: branch)
    * git checkout &lt;branch&gt;
    * git branch -d &lt;branch&gt; (-d: delete)
    * git add &lt;FILENAME&gt; or git add *   
    * git commit -m "Explanation"   
3. Final Draft   
    * git push origin &lt;branch&lt; (e.g. master, branch_1, etc.)
    * git remote add origin &lt;VIRTUAL_STORAGE_PATH&gt;
    * git pull
    * git merge &lt;branch&gt;   

### 3. Branch
### 4. Merge