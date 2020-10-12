# leecode
给你一棵所有节点为非负值的二叉搜索树，请你计算树中任意两节点的差的绝对值的最小值。

 
示例：

输入：

   1
    \
     3
    /
   2

输出：
1

解释：
最小绝对差为 1，其中 2 和 1 的差的绝对值为 1（或者 2 和 3）。
 
 
 /**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    int getMinimumDifference(TreeNode* root) {
       int ans=INT_MAX;int pre=-1;
       dfs(root,pre,ans);
       return ans; 
    }
    void dfs(TreeNode *root,int& pre,int& ans){
        if(root==NULL)
        return;
        dfs(root->left,pre,ans);
        if(pre==-1){
            pre=root->val;
        }
        else{
            ans=min(abs(pre-root->val),ans);
            pre=root->val;
            }
            dfs(root->right,pre,ans);
    }
};