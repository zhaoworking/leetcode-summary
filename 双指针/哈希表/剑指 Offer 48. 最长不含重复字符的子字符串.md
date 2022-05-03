# Link
https://leetcode-cn.com/problems/zui-chang-bu-han-zhong-fu-zi-fu-de-zi-zi-fu-chuan-lcof/
# Code
        class Solution {
        public:
            int lengthOfLongestSubstring(string s) {
                unordered_set<int> myset;
                int slow = 0;
                int res = INT_MIN;
                for(int fast = 0; fast < s.size();fast++){
                    while(myset.count(s[fast]) != 0){
                        myset.erase(s[slow]);
                        slow++;
                    }
                    myset.insert(s[fast]);
                    res = max(res, (fast - slow + 1));
                }
                return res == INT_MIN ? 0 : res;
            }
        };
# Solution
  * 使用双指针加哈希数组的方法
  * low 指针用来记录两个重复字符中的前一个索引，fast 指针用来遍历整个字符串，其中主要是不断的更新 low 指针，然后计算当前的 不重复长度。
