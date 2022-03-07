https://leetcode-cn.com/problems/path-sum-ii/
# Code
    class Solution {
    public:
        vector<int> res;
        void traverse(TreeNode* root,vector<vector<int>>& path,int& count){

            count -= root->val; // 终止条件在 变化 之后
            res.push_back(root->val); 
            if(!root->left && !root->right && count == 0){
                path.push_back(res);
                return ;
            }

            if(root->left){
                traverse(root->left,path,count);
                count += root->left->val;
                res.pop_back();
            }
            if(root->right){
                traverse(root->right,path,count);
                count += root->right->val;
                res.pop_back();
            }
        }
        vector<vector<int>> pathSum(TreeNode* root, int targetSum) {
            vector<vector<int>> res1;
            if(root == nullptr) return res1;
            traverse(root,res1,targetSum);
            return res1;
        }
    };
# Solution
  * 题目同 路经综合，同样使用的是迭代的方式，先序遍历，然后回溯
  * 终止条件
    * 终止的条 件选择是 **叶子节点** 且 count 减到 0
  * 单层逻辑
    * 在遍历的过程不仅要更新 count 还要更新 res
  * 返回值
    * 由于是遍历整个二叉树，且不用提前返回，不需要返回值
  * 先序遍历 终止条件放在 中间节点 的后面
