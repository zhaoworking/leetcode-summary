# Code 
    class Solution {
    public:
        int uniquePathsWithObstacles(vector<vector<int>>& obstacleGrid) {
            int rows = obstacleGrid.size();
            int cols = obstacleGrid[0].size();
            vector<vector<int>> dp(rows,vector<int>(cols,0));
            // 初始化的时候，容易造成迷惑。这里是在 遇到障碍之后的 路径全为 0
            for(int i = 0; i < rows && obstacleGrid[i][0] != 1; i++) {
                dp[i][0] = 1;
            }
            for(int j = 0; j < cols && obstacleGrid[0][j] != 1; j++){
                dp[0][j] = 1;
            }
            // 当遇到障碍的时候，该路径为 0
            for(int i = 1; i < rows; i++){
                for(int j = 1;j < cols; j++){
                    dp[i][j] = dp[i-1][j] + dp[i][j-1];
                    if(obstacleGrid[i][j] == 1)
                    {
                        dp[i][j] = 0;
                    }
                }
            }
            return dp[dp.size()-1][dp[0].size()-1];
        }
    };
# Solution 
  * 动态规划问题，解决的方法同样是 五部曲
    * 五部曲
      * dp 数组的含义
      * 初始化
      * 状态转移方程
      * 遍历顺序
      * 验证 dp 的结果
# Summary
  * 这里在进行初始化的时候，在遇到障碍的时候应该设置这条路径之后的 dp 数组值全为 0 ，而不是只将当前的值设为 0 
  * 当遍历所有的空格过程中，如果遇到空格里面有障碍物的情况，那么就要把此空格设置为 0 
