https://leetcode-cn.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/
# Code 
    class Solution {
    public:
        TreeNode* traverse(vector<int>& preorder, vector<int>& inorder){
            if(preorder.size() == 0) return nullptr; // 防止 两个 节点的时候，preorder 为空，preorder[0] 越界
            TreeNode* root = new TreeNode(preorder[0]);
            // std::cout << root->val << std::endl;
            if(preorder.size() == 1 ) return root;
            int delimiter = 0;
            for(;delimiter < inorder.size(); delimiter++){ // 在中序遍历中 寻找 前序遍历的头节点
                if(inorder[delimiter] == root->val) break;
            }
            vector<int> leftinorder(inorder.begin(),inorder.begin() + delimiter); // 中序遍历分割
            vector<int> rightinorder(inorder.begin()+delimiter+1,inorder.end());
            vector<int> leftpreorder(preorder.begin()+1,preorder.begin()+1+delimiter); // 先序遍历分割
            vector<int> rightpreorder(preorder.begin()+1+delimiter,preorder.end());

            root->left = traverse(leftpreorder,leftinorder);
            root->right = traverse(rightpreorder,rightinorder);
            return root;
        }
        TreeNode* buildTree(vector<int>& preorder, vector<int>& inorder) {
            return traverse(preorder,inorder);
        }
    };
# Solution
  * 同 后序和中序 构造二叉树 方法相同，由前序遍历分割中序，然后由得到的中序数组再去分割前序
  * 递归的三部曲
    * 终止条件
      * 这里需要注意的是 当二叉树只有两个节点的时候，会分割出空数组，那么就需要在开头判断数组是否为空。如果为空，则需要返回 nullptr
      * 当 前序数组大小为 1 的时候，不可再进行分割，直接返回 root
    * 返回类型 
      * 指向根节点的指针
    * 入口参数
      * 前序遍历 和 中序遍历
