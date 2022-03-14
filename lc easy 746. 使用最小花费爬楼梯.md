# Code
    class Solution {
    public:
        int minCostClimbingStairs(vector<int>& cost) {
            vector<int> dp(cost.size()+1,0);
            dp[0] = 0;
            dp[1] = 0;
            for(int i = 2; i <= cost.size();i++){
                dp[i] = min(dp[i-1] + cost[i-1],dp[i-2] + cost[i-2]);
            }
            return (dp[cost.size()]);
        }
    };
# Solution
  * 本题目主要考察的是 动态规划 
  * 五个部分
    * dp 数组表示的是什么意思
    * 状态转移方程
    * 初始化
    * 遍历顺序
    * 带入数组检查
# Summary 
  * 这道题在开始的时候，写出了状态转移方程，但是在初始化的时候出错了，导致后面没写出来
  * 我在初始化的时候，要不然是第一步就需要 收费 ，最后一步不收费；要不然就是第一步不需要 收费，最后一步再收费。
  * 我使用的是第一种情况，但初始化的时候，应该把 dp[0] 和 dp[1] 初始化为 0；
