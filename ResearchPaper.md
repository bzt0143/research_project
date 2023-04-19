# Research Paper
Name: Zitong Bao


Semester: 2023 Spring


Topic: AVLtree Implement


Link The Repository: 

## Introduction

The datastructure I choose for this research is AVL tree and I use C to implement it. AVL is a special kind of tree data structure and it is used in many fileds. In this research paper, I will focus on the analysis of AVL tree performance in terms of time complexity, space complexity and give the empiricla analysis to prove it, also, as the part of my rearch, I will compare bineary search tree and AVL to find the differences between its performances. The third part of my reaserch will focus on the real-world application of AVL tree and how I impemented in C. 

-- What is AVL Tree


An AVL tree is named after its inventor, Adelson-Velskii and Landis. The AVL tree is a self-balancing binary search tree. Self-balance means that the difference of heights of the left and right subtrees of any is at most one. In other words, the height difference of the subtrees is always one or zero. This character leads to efficient search, insertion, and deletion operations for the AVL tree. In general, the time complexity of operations in an AVL tree is O(log n) and the space complexity is O(N), where n is the number of nodes in the tree. 

-- Brief History of AVL Tree


AVL tree is named after its inventors, Georgy Adelson-Velsky and Evgenii Landis, who introduced it in 1962. They were interested in developing a data structure that had guaranteed worst-case performance for all operations. The first AVL tree algorithm was published in Russian in 1962, and later, in English in 1964. The paper describing the algorithm was titled "An algorithm for the organization of information" and was published in the Journal of Soviet Mathematics.(source from wikepidia)


Nowadays, becauses of the efficient performance of AVL tree, it has been used in many fields of computer science such as database, machine learning and complier stytem, etc. Besides AVL tree, there are many complex tree data structure such as red-black tree, Trie tree, B tree or segment tree. All of these tree has its own strengths. In this paper, I will only focus on AVL tree to exlplore this self-balancing tree.


## Analysis of Algorithm/Datastructure


The AVL tree , a balanced binary search tree, is a relatively efficient method compared with an ordinary tree data structure. In this part, I will provide basic introduction for the time and space compleixty analysis and in the empirical analysis part, I will run the test case and prove the complexity analysis.

--Time complexity

For AVL tree, in general, the time complexity is $O(logN)$ and the N is the number of nodes in the tree. For searching the certain nodes in the tree, the search operation will traverse the height of the tree, which is logarithmic in the number of nodes due to the self-balancing property of AVL Trees, so the time compexity is also be the $O(logN)$. However, the constant balancing operations during insertion and deletion can make AVL Trees a little bit slowever.For the inserting the nodes in the tree, the AVL tree will find the position of the new node and rotate the tree to maintain the balance and the time complexity is $O(logN)$. As for the deletion, the process is also finding the node, delete it and rotation the tree,  similar to the insertion, it takes $O(logN)$.


Compared with the ordinary bineary search tree, because the AVL tree's height difference is always be 0 or 1, the worst case's time complexity for AVL tree is also $O(logN)$. This is because the height of the AVL Tree is always maintained to be logarithmic, ensuring that the tree remains balanced. For the ordinary BST, when the worst case happens, the BST will be a linked list, and the time complexity is $O(logN)$.

--Space complexity

For AVL tree, the space complexity is O(n), abd N is the number of nodes in the tree, because each node in the tree needs a constant amount of space to store its data which is N. However, the AVL needs extra memory storage  for the height balance factor, which increases the space complexity compared to a regular binary search tree.


Overall,a  AVL Tree is an efficient data structure of maintaining a balanced binary search tree, ensuring logarithmic time complexity $O(logN)$ for searching, insertion, and deletion operations and it needs extra space to store the height balance factor.

## Empirical Analysis
- What is the empirical analysis?
- Provide specific examples / data.


## Application
- What is the algorithm/datastructure used for?
- Provide specific examples
- Why is it useful / used in that field area?
- Make sure to provide sources for your information.


## Implementation

In this research project, I choose C to implement the AVL tree. All the method I have are:
```c
void AVLfreeHelper(avlNode *node);

void free_AVL(AVL *tree);

avlNode *newNode(int key);

AVL *create_avl();

void freeHelper(avlNode *node);

void free_AVL(AVL *tree);

int getHeight(avlNode *node);

bool avlSearch(avlNode *node, int key);

int max(int a, int b);

avlNode *rightRotate(avlNode *root);

int getBalanceFac(avlNode *root);

avlNode *insert(avlNode *root, int key);

avlNode *delete(avlNode *root, int key);

void print_inorder(avlNode *root);
```

First, I define the node of the tree and tree itself as following:
```c
typedef struct avlNode {
    int key;
    int height;
    struct avlNode *left;
    struct avlNode *right;
} avlNode;

typedef struct avlTree {
    unsigned int size;
    avlNode *root;
} AVL;
```
avlNode is a structure representing a node in an AVL Tree, which contains the following members. The element of this node: key is an integer value representing the key stored in the node, height is an integer value representing the height of the node in the AVL Tree, left is pointer to the left child of the node and right is pointer to the right child of the node. avlTree  A structure representing an AVL Tree, which contains the following members:
size is an unsigned integer value representing the number of nodes in the AVL Tree, and root is pointer to the root node of the AVL Tree.


There is an one important function in the AVL implementation, which is calculatingthe balance factor of a node. The balance factor is the difference between the height of the node's left subtree and the height of the node's right subtree. For the AVL tree, it can provide whether the tree is balanced or not to determine whether the tree is needed the rotation.


If the tree is not balanced, then we need to rotated the tree to the balance status by using the recursive. There are four condtions to rotate the tree and make it balanced:
- Left Rotation (LL)
- Right Rotation (RR)
- Left-Right Rotation (LR)
- Right-Left Rotation (RL)

The basic condition is left rotation and right rotation. Left rotation will be called when its left subtree is taller than its right subtree, so the basic process is the left child becomes the new parent node, and the original parent node becomes the right child of the new parent. After doing the this, the tree will be balanced again, and I use the recursion to achieve this:
```c
//leftrote the Node and return the node
avlNode *leftRotate(avlNode *root) {

    if (root == NULL){
        return NULL;
    }
    avlNode *originRight = root->right;
    root->right = originRight -> left;
    originRight -> left = root;

    // Update the height
    updateHeight(root);
    updateHeight(originRight);
    return originRight;
}
```



Right Rotation (RR): This rotation is performed when a node is right-heavy (its right subtree is taller than its left subtree) and its right child is also right-heavy or balanced. The right child becomes the new parent node, and the original parent node becomes the left child of the new parent.

AVL trees are typically implemented using recursive algorithms that maintain the balance property by performing rotations on the tree when necessary. A rotation is an operation that changes the structure of the tree by moving nodes from one position to another, while maintaining the ordering of the nodes.


- What language did you use?
- What libraries did you use?
- What were the challenges you faced?
- Provide key points of the algorithm/datastructure implementation, discuss the code.
- If you found code in another language, and then implemented in your own language that is fine - but make sure to document that.


## Summary

In this semester, I learned about tree and especially the bineary search tree. When I looked up the 
tree 
- Provide a summary of your findings
- What did you learn?
