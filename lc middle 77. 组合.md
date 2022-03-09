https://leetcode-cn.com/problems/combinations/
# Code
    class Solution {
    public:
      vector<int> path;
      vector<vector<int>> res;
      void backtracing(int n, int k,int startindex){
          if(path.size() == k){
              res.push_back(path);
              return;
          }

          for(int i = startindex; i <= n; i++){
              path.push_back(i);
              backtracing(n,k,i+1);
              path.pop_back();
          }
      }
      vector<vector<int>> combine(int n, int k) {
          backtracing(n,k,1);
          return res;
  }
# Solution 
  * 本题使用的是 **回溯** 的方法，穷举 数组 的 组合
  * 回溯问题的三个条件
    * 入口参数和返回值
    * 终止条件
    * 单层逻辑

  * 模板

        void backtracking(参数) {
            if (终止条件) {
                存放结果;
                return;
            }

          for (选择：本层集合中元素（树中节点孩子的数量就是集合的大小）) {
              处理节点;
              backtracking(路径，选择列表); // 递归
              回溯，撤销处理结果
          }
# Extension
   * 剪枝操作
   * 组合的 子集 数目有要求，当子集的数目大于剩余元素的数目的时候，即可进行裁剪
   *  【1 2 3 4】 当 k = 3, n = 4  时，遍历到 2 的时候，就不应该往下遍历了，因为 `【3 4】` 并不满足 子集数目为 3 的要求
