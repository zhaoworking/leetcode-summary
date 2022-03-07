https://leetcode-cn.com/problems/path-sum/
# code
    class Solution {
    public:
        bool traverse(TreeNode* root ,int& count){
            if(root == nullptr) return false;
            count -= root->val; // zhong
            if(!root->left && !root->right && count == 0){
                return true;
            }
            if(!root->left  && !root->right) return false;
            if(root->left) { 
                if(traverse(root->left,count)) 
                    return true;
                count += root->left->val; // **这里注意回溯到是 root->left 的 val ，而不是 root 的 val**
            } 
            if(root->right) { 
                if(traverse(root->right,count)) 
                    return true; 
                count += root->right->val;
            }
            return false;
        }
        bool hasPathSum(TreeNode* root, int targetSum) {
            if(root == nullptr) return false;
            return traverse(root,targetSum);
# Solution
  * 本题目考察的是递归的 返回值和回溯法
  * 使用 深度优先遍历的方式，先序遍历
  * 因为搜索的是二叉树的某一条路径，所以递归函数需要返回值
  * 终止条件是 叶子节点，且 count 为 0 。这里采用的是递减的方式，省去了传入 target 的麻烦
  * 因为要 返回 成立条件，而不是拿 **返回值** 进行计算，所以，这里的 返回值 不参与运算，为 布尔类型

# Tips
  * 回溯的时候，是对 **递归参数** 的回溯，不是对 中间 节点的 回溯
