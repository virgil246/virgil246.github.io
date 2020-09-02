---
title: "Double Ended Priority Queue"
date: 2020-09-02T21:37:54+08:00
draft: false
tags: ["Data Structure","Heap"]
categories: ["筆記"]
---

# Min-Max Heap
## Def
* 一種Complete B.T.
1. Min-level Max-level交錯
2. Root為min-level
3. 若Node X為 Min-level 代表以X為Root的子樹中，X最小
4. 若Node X為 Max-level 代表以X為Root的子樹中，X最大
* 操作
  * Insert X
    1. 將X置於 last Node的下一個
    2. X的parent P
    * Case:
       1. X位於 Min-level
           1. `X.val < P.val`
              1. 挑戰上面的Min-level
           2. `X.val > P.val`
              1. `Swap(X,P)`
              2. 挑戰上面的Max-level
       2. X位於 Max-level
           1. `X.val > P.val`
              1. 挑戰上面的Max-level
           2. `X.val > P.val`
              1. `Swap(X,P)`
              2. 挑戰上面的Min-level        
  * Delete Max
  * Delete Min
    1. 移除Root
    2. 刪除Last Node X
    3. X插入Root
    * Case
       1. X 無child 停止
       2. X 有child 無 grandchild 
          1. 找出child中最小值 k
                ```go
                if k.val < X.val {
                    Swap(k,X)
                }
                ```
              
      1. 有grandchild  
          1. 找出grandchild中最小 k ，p為k之parent
            ```go
            if k.val < X.val { //與 min-level 比較
                Swap(k,X) 
                if X.val > p.val {// 換下去之後要跟 max-level 比較
                    Swap(X,p)
                }
                //以K的原位作為ROOT再次判斷case
                goto(Switch)
            }
            ```
            
   
# Deap
## Def
* Complete B.T.
1. Dummy Root(No Data)
2. Root 左子樹為Min-Heap
3. Root 右子樹為Max-Heap
4. 若i為Min-Heap中某Node，令j為i在Max-Heap中對應的Node，則`Deap[i]<=Deap[j]`  
>$j=i+(i 的上一層最多Node數)$  
$=i+2^{(i的level - 1)}-1$  
$=i+2^{(i的level - 2)}$

> 求i的level  
> $2^{(k-1)}=i$  
> $k=\lceil log_2{(i+1)}\rceil$
* 操作
  * Insert X
    1. 將X置於Last Node的下一個位置
    2. Case:
        1. X在 Min-Heap j為其在 Max-Heap對應位置
            ```go
            if x > Deap[j]{
                Deap[n]=Deap[j]
                MAX-Heap-Insert(Deap,j,X)
            } else {
                Min-Heap-Insert(Deap,n,x)
            }
            ```
        2. X在 Max-Heap j為其在 Min-Heap對應位置
            ```
            if x < Deap[j]{
                Deap[n]=Deap[j]
                Min-Heap-Insert(Deap,j,X)
            } else {
                Max-Heap-Insert(Deap,n,x)
            }
            ```

            ```
  * Delete min  
    1. 移除左子樹Root
    2. 刪除Last Node X
    3. 左子樹Root的空格，由子點min{Ltree,Rtree}向上遞補
    4. Insert X
# SMMH(Symmetric Min-Max Heap)
## Def
* Complete B.T. & Dummy Root
1. `Left Sibling <= Right Sibling`
2. 若 node X 有Grandparent 則Grandparent的Left child<=X
3. 則Grandparent的Right child>=X
* 操作
  * Insert X
  * Delete Min