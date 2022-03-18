# Code
    class Solution {
    public:
        int integerBreak(int n) {
            vector<int> dp(n+1,0);
            dp[1] = 1;
            for(int i = 2; i <= n; i++){
                for(int j = i-1; j > 0; j--){
                    dp[i] = max(dp[i],max( dp[j] * (i-j), j*(i-j) ));
                }
            }  
            return dp[n];
        }
    };
# Solution
  * 对于整数的拆分，可以是拆成 2 个，也可以拆成 2 个以上，仍然是想到的五部曲
    * 五部曲
      * dp 数组的含义 -- 这里的 dp[i] 表示的是拆解完后最大的值
      * 初始化 -- dp[0] 没有含义，dp[1] 可以初始化
      * 状态转移方程 -- dp[i] = max(j * (i-j), max(dp[j]*(i-j) ))
      * 迭代的顺序，从前往后
      * 验证 dp 输出
# Summary
  * 这里在写状态转移方程的时候，容易把 j * (i-j) 这个组合忘掉，dp[j] * (i-j) 中的 dp[j]拆解不成 单独的 j，所以要写出来 j*(i-j) 这个组合。
