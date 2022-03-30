# Link
https://leetcode-cn.com/problems/zui-chang-bu-han-zhong-fu-zi-fu-de-zi-zi-fu-chuan-lcof/
# Code
    class Solution {
    public:
        int lengthOfLongestSubstring(string s) {
            int hash_table[128]={};
            fill(hash_table,hash_table+128,-1);
            int i = -1;
            int res = 0;

            for(int j = 0; j < s.size();j++){
                if(hash_table[s[j]] != -1){
                    i = max(i,hash_table[s[j]]);
                    cout << hash_table[s[j]] << endl;
                }
                hash_table[s[j]] = j;
                res = max(res,j-i);
            }
            return res;
        }
    };
# Solution
  * 使用双指针加哈希数组的方法
  * low 指针用来记录两个重复字符中的前一个索引，fast 指针用来遍历整个字符串，其中主要是不断的更新 low 指针，然后计算当前的 不重复长度。
