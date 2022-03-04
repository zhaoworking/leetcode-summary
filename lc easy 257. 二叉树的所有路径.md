# Solution 
  * 本题既可以用递归方法，也可以使用迭代的方法做。
  * 递归方法：

    1. 因为从根节点开始计算路径，所以采用先序遍历的方式。
    2. 参数入口： root 节点 path(用于回溯) res
    3. 终止条件： 左右孩子节点全是 nullptr ，装填 res
    4. 单层递归逻辑：左孩子递归，回溯；右孩子递归，回溯

  * 迭代方法：

    1. 用栈模拟先序遍历，先装右孩子节点，在装填左孩子节点

# Link
https://leetcode-cn.com/problems/binary-tree-paths/
