## LC 285
Given the root and a node p in a BST. Find the in-order successor of p.
``` cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
/*
    Ref: https://leetcode.com/problems/inorder-successor-in-bst/discuss/72741/C%2B%2B-iterative
    If p has a right subtree, then, its successor is the left-most node in that subtree. 
    Otherwise, successor of p, should have p in its sub-tree
*/
class Solution {
public:
    TreeNode* inorderSuccessor(TreeNode* root, TreeNode* p) {
        
        if(p->right)    //find the left-most node in the right sub-tree
        {
            TreeNode* cur = p->right;
            while(cur->left)
                cur = cur->left;
            return cur;
        }
        
        else
        {
            TreeNode* suc = NULL;
            while(root)
            {
                if(root->val < p->val)
                    root = root->right;
                else if(root->val > p->val)
                {
                    suc = root;
                    root = root->left;
                }
                else
                    break;
            }
            return suc;
        }
    }
    
};
```
