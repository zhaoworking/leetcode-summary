# Code
    class Solution {
    public: 
        vector<int> path;
        vector<vector<int>> res;
        void backtracing(vector<int> nums, vector<bool>& used){
            if(path.size() == nums.size()){
                res.push_back(path);
                return;
            }
            for(int i = 0; i < nums.size(); i++){
                if(used[i] == true) continue;
                path.push_back(nums[i]);
                used[i] = true;
                backtracing(nums,used);
                path.pop_back();
                used[i] = false;
            }       
        }
        vector<vector<int>> permute(vector<int>& nums) {
            vector<bool> used(nums.size(),0);
            backtracing(nums,used);
            return res;
        }
    };
# Solution
  * 回溯方法
    * 入口参数
    * 终止条件
    * 返回值 -- 一般为 void
    * 单层迭代逻辑
  * 排列问题，需要借助 used 数组来记录已经放入的元素
  * 不需要 startindex 来记录起始的位置
