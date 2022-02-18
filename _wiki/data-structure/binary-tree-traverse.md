---
layout  : wiki
title   : 이진트리 순회
summary : 
date    : 2022-02-18 22:42:40 +0900
updated : 2022-02-18 22:53:25 +0900
tags    : 
toc     : true
public  : true
parent  : [[data-structure/index]]
latex   : false
---
* TOC
{:toc}

## 소개 
'루트 노드를 언제 방문하느냐'에 따라 각각 전위, 중위, 후위 순위로 나뉨.
- 전위 순회(Preorder Traversal) : 루트 노드를 먼저!
- 중위 순회(Inorder Traversal) : 루트 노드를 중간에!
- 후위 순회(Postorder Traversal) : 루트 노드를 마지막에!

## main.c
```c
#include <stdio.h>
#include "BinaryTree.h"

void ShowIntData(int data);

int main(void) {
    BTreeNode *bt1 = MakeBTreeNode();
    BTreeNode *bt2 = MakeBTreeNode();
    BTreeNode *bt3 = MakeBTreeNode();
    BTreeNode *bt4 = MakeBTreeNode();
    BTreeNode *bt5 = MakeBTreeNode();
    BTreeNode *bt6 = MakeBTreeNode();

    SetData(bt1, 1);
    SetData(bt2, 2);
    SetData(bt3, 3);
    SetData(bt4, 4);
    SetData(bt5, 5);
    SetData(bt6, 6);

    MakeLeftSubTree(bt1, bt2);
    MakeRightSubTree(bt1, bt3);
    MakeLeftSubTree(bt2, bt4);
    MakeRightSubTree(bt2, bt5);
    MakeRightSubTree(bt3, bt6);

    PreorderTraverse(bt1, ShowIntData);
    printf("\n");
    InorderTraverse(bt1, ShowIntData);
    printf("\n");
    PostorderTraverse(bt1, ShowIntData);
    printf("\n");

    return 0;
}

void ShowIntData(int data) {
    printf("%d ", data);
}
```

## BinaryTree.h
```c
#ifndef __BINARY_TREE_H__
#define __BINARY_TREE_H__

typedef int BTData;

typedef struct _bTreeNode {
    BTData data;
    struct _bTreeNode *left;
    struct _bTreeNode *right;
} BTreeNode;

BTreeNode *MakeBTreeNode(void);

BTData GetData(BTreeNode *bt);

void SetData(BTreeNode *bt, BTData data);

BTreeNode *GetLeftSubTree(BTreeNode *bt);

BTreeNode *GetRightSubTree(BTreeNode *bt);

void MakeLeftSubTree(BTreeNode *main, BTreeNode *sub);

void MakeRightSubTree(BTreeNode *main, BTreeNode *sub);

typedef void (*VisitFuncPtr)(BTData data);

void PreorderTraverse(BTreeNode *bt, VisitFuncPtr action);

void InorderTraverse(BTreeNode *bt, VisitFuncPtr action);

void PostorderTraverse(BTreeNode *bt, VisitFuncPtr action);

#endif
```

## BinaryTree.c
```c
#include <stdio.h>
#include <stdlib.h>
#include "BinaryTree.h"

BTreeNode *MakeBTreeNode(void) {
    BTreeNode *nd = (BTreeNode *) malloc(sizeof(BTreeNode));
    nd->left = NULL;
    nd->right = NULL;
    return nd;
}

BTData GetData(BTreeNode *bt) {
    return bt->data;
}

void SetData(BTreeNode *bt, BTData data) {
    bt->data = data;
}

BTreeNode *GetLeftSubTree(BTreeNode *bt) {
    return bt->left;
}

BTreeNode *GetRightSubTree(BTreeNode *bt) {
    return bt->right;
}

void MakeLeftSubTree(BTreeNode *main, BTreeNode *sub) {
    if (main->left != NULL)
        free(main->left);

    main->left = sub;
}

void MakeRightSubTree(BTreeNode *main, BTreeNode *sub) {
    if (main->right != NULL)
        free(main->right);

    main->right = sub;
}

void PreorderTraverse(BTreeNode *bt, VisitFuncPtr action) {
    if (bt == NULL)
        return;

    action(bt->data);
    PreorderTraverse(bt->left, action);
    PreorderTraverse(bt->right, action);
}

void InorderTraverse(BTreeNode *bt, VisitFuncPtr action) {
    if (bt == NULL)
        return;

    InorderTraverse(bt->left, action);
    action(bt->data);
    InorderTraverse(bt->right, action);
}

void PostorderTraverse(BTreeNode *bt, VisitFuncPtr action) {
    if (bt == NULL)
        return;

    PostorderTraverse(bt->left, action);
    PostorderTraverse(bt->right, action);
    action(bt->data);
}
```
