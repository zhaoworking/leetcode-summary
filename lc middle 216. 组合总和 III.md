https://leetcode-cn.com/problems/combination-sum-iii/
# Code 
    class Solution {
    public:
        vector<int> vec;
        vector<vector<int>> res;
        void backtracing(int k, int n,int index){
            if(vec.size() == k){
                if(n == 0){
                    res.push_back(vec);
                    return;
                }
                return;
            }
            // if(vec.size() == k && n == 0){
            //     res.push_back(vec);
            //     return;
            // }
            // std::cout << index << std::endl;
            for(int i = index; i <= 9; i++){
                vec.push_back(i);
                backtracing(k,n-i,i+1);// i+1 为 index 而不是 index + 1
                vec.pop_back();
            }
        }
        vector<vector<int>> combinationSum3(int k, int n) {
            backtracing(k,n,1);
            return res;
        }
    };
# Solution
  * 本题目仍然是组合问题，使用的方法仍然是 **回溯** 
  * 入口参数
    * 集合数目 总和 开始位置
  * 返回值
    * void 
  * 终止条件
    * 当达到 k 个数目的时候
  * 需要注意的是 这里的回溯递归，需要写进去的是 i + 1，而不是 index + 1，因为 index 是不变化的，i 是变化的
