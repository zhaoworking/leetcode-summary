# Code
    class Solution {
    public:
        int uniquePaths(int m, int n) {
            vector<vector<int>> dp(m,vector<int>(n,0));
            for(int i = 0; i< dp.size();i++) dp[i][0] = 1;
            for(int j = 0; j< dp[0].size();j++) dp[0][j] = 1; 
            for(int i = 1; i < dp.size(); i++){
                for(int j = 1; j < dp[0].size();j++){
                    dp[i][j] = dp[i-1][j] + dp[i][j-1];
                } 
            }
            return dp[m-1][n-1];
        }
    };
    
# Solution
  * 此题既可以 **图论中的深度搜索** 也可以是 **动态规划** ，其中动态规划中需要注意初始化的问题
  * 动态规划 五部曲
    * dp 数组的含义
    * dp 数组的初始化
    * 状态转换方程
    * 遍历顺序
    * 带入求解
  * 图论
    * 深度优先那一套，但是要注意 **边界条件** 和 **时间复杂度**
# Summary
  * 这里在 写动规的时候，状态转移方程很容易就能想到，但是这个初始化不容易想。我在开始的时候只想到了初始化单个元素，而没有想到整个 **行** 或者 **列** 都是需要初始化的，导致递推的时候出错
  *  
