---
title: "AVL Tree"
date: 2020-09-05T23:10:08+08:00
draft: false
categories: ["筆記"]
tags: ["BST",]
---


# AVL Tree
## Def
* Height Balance BST
1. Root 之左右子樹高度差 1 <=> $|{H_L-H_R}|\leq1$
2. 左右子樹皆為AVL Tree
> Node Balance Factor  
> Node 的 左子樹高度-右子樹高度   
> Note: 只有 0,-1,1
## Unbalance Situation
1. LL
2. LR
3. RL
4. RR  
* 由Insert New Node之後，向上看最近一個 Balance Factor不為 0,-1,1的點在往New Node前進兩層(LL,LR,RL,RR)  

![](https://upload.wikimedia.org/wikipedia/commons/c/c7/Tree_Rebalancing.png)

## 操作
1. Delete X
    1. [以BST方式刪除](http://alrightchiu.github.io/SecondRound/binary-search-tree-sortpai-xu-deleteshan-chu-zi-liao.html)
    2. 調整(由下而上)

## Theorem
* 形成高 h 之AVL Tree  
$Minimal\ Node=F_{h+2}-1$