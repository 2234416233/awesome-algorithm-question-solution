# Symmetric Tree （是否是镜像树）



## From



[LeetCode 101](https://leetcode.com/problems/symmetric-tree/description/)





## Question

Given a binary tree, check whether it is a mirror of itself (ie, symmetric around its center).

For example, this binary tree `[1,2,2,3,4,4,3]` is symmetric:

```
    1
   / \
  2   2
 / \ / \
3  4 4  3

```

But the following `[1,2,2,null,3,null,3]` is not:

```
    1
   / \
  2   2
   \   \
   3    3

```

**Note:**
Bonus points if you could solve it both recursively and iteratively.



## Solution  



### C++

```c++
// Definition for a binary tree node.
struct TreeNode {
  int val;
  TreeNode *left;
  TreeNode *right;
  TreeNode(int x) : val(x), left(NULL), right(NULL) {}
};

class Solution {
public:
    bool isSymmetric(TreeNode* root) {
        
        if (root == NULL){
            return true;
        }
        
        return checkLeftAndRightNodes(root->left,root->right);
    }
    
    bool checkLeftAndRightNodes(TreeNode *leftNode, TreeNode *rightNode){
        
        if (leftNode == NULL && rightNode == NULL){
            return true;
        }
        
        if (leftNode == NULL || rightNode == NULL){
            return false;
        }
        
        if (leftNode->val !=  rightNode -> val){
            return false;
        }else {
            return checkLeftAndRightNodes(leftNode -> left, rightNode->right)
            &&  checkLeftAndRightNodes(leftNode -> right, rightNode->left);
        }
    }
};

```



### Java

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    
    public boolean isSymmetric(TreeNode root) {
        
        if ( root == null ){
            return true;
        }
        
        return checkLeftAndRightNodes(root.left, root.right);
        
        
    }
    
    public boolean checkLeftAndRightNodes(TreeNode leftNode, TreeNode rightNode){
        
        if (leftNode == null && rightNode == null){
            return true;
        }
        
        if (leftNode == null || rightNode == null){
            return false;
        }
        
        if (leftNode.val != rightNode.val){
            return false;
            
        }else{
            
            return checkLeftAndRightNodes(leftNode.left, rightNode.right) &&  checkLeftAndRightNodes(leftNode.right,rightNode.left);
            
        }
    }
}
```


