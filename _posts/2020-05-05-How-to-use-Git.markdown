---
layout: post
title:  "How to use Git"
date:   2020-05-05 15:03:24 +0900
categories: Basic
---

<div style="font-family: Times; text-align: center"><i><b>Last Updated on July 6th, 2020</b></i></div>

## Abstract
0. Reference: [https://rogerdudler.github.io/git-guide/](https://rogerdudler.github.io/git-guide/index.ko.html)
1. What's the Git?
2. Location
3. Command

### 1. What's the Git?
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

### 2. Location
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

1. Local storage (e.g. Our computer)
2. Virtual storage (e.g. Github)
Since both storages are seperated, we can build up in local storage first then in virtual storage second.

### 3. Command
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

To use branch process is effective in building up the prototype of program      
1. Download Virtual storage to Local storage   
    1. Make current directory to git storage
        * git init
    2. Virtual storage to Local storage   
        * git clone /&lt;URL&gt;
        * git clone &lt;USERNAME&gt;@&lt;HOST&gt;:/&lt;URL&gt; 
<br>

2. Debugging
    1. With Jekyll Server **(Not recommended)**
        * &lt;PATH&gt; bundle exec jekyll serve
        and then browse to [http://127.0.0.1:4000/](http://127.0.0.1:4000/)
<br>

3. With branch
    1. See the branch
        * git branch (Current branch is marked with *)
    2. See the status of branch
        * git status (List of Modified, added files)
    3. Create the branch and Move to the branch 
        * git branch &lt;branch&gt; (Create)
        * git checkout &lt;branch&gt; (Move)
        * git checkout -b &lt;branch&gt; (Create and then Move)
    4. Delete the branch
        * git branch -d &lt;branch&gt; (-d: delete)
    5. Create directory or file
        * git add &lt;FILENAME&gt; or git add *   
    6. Save all changes
        * git add .(dot)
    7. Commit to the Local Storage
        * git commit -m "Explanation"  
    8. Push the Local Storage to the Virtual Storage
        * git remote add origin &lt;VIRTUAL_STORAGE_PATH&gt;
        * git push origin &lt;branch&gt; (e.g. master, branch_1, etc.)
    9. Pull the branch of Virtual Storage
        Move to the branch which I want to pull
        * git pull
    10. Merge the branch
        Move to the Parent branch (usually, master)
        * git merge &lt;branch&gt;
        Push the Local Storage to the Virtual Storage