# Introduction to Binary Search Tree


## What is Binary Search Tree?

**Binary Search Tree (BST)** is a special type of **binary tree** in which the **left child** of a node has a value **less** than the node’s value and the **right child** has a value **greater** than the node’s value. This property is called the **BST** property and it makes it possible to **efficiently search, insert, and delete** elements in the tree.


![loading...](../../images/dsa/bst/Binary-Search-Tree.webp)


---


## Properties of Binary Search Tree:

* The left subtree of a node contains only nodes with values lesser than the node’s value.

* The right subtree of a node contains only nodes with values greater than the node’s value.

* This means everything to the left of the root is less than the value of the root and everything to the right of the root is greater than the value of the root. Due to this performing, a binary search is very easy.

* The left and right subtree each must also be a binary search tree.  



## Basic Operations on Binary Search Tree:


### 1. Searching a node in BST

Searching in BST means to locate a specific node in the data structure. In Binary search tree, searching a node is easy because of its a specific order.


```cpp

Node* search(Node* root, int key){

    if (root == NULL || root->key == key)
        return root;

    // Key is greater than root's key
    if (root->key < key)
        return search(root->right, key);

    // Key is smaller than root's key
    return search(root->left, key);
}


```


### 2. Insert a node into a BST


A new key is always inserted at the leaf. Start searching a key from the root till a leaf node. Once a leaf node is found, the new node is added as a child of the leaf node.



```cpp

Node* search(Node* root, int key){

     if (node == NULL)
        return new Node(key);

    // Otherwise, recur down the tree
    if (key < node->key){
        node->left = insert(node->left, key);
    }
    else if (key > node->key){
        node->right = insert(node->right, key);
    }

    // Return the node pointer
    return node;
}


```



