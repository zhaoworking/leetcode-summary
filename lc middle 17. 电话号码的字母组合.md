https://leetcode-cn.com/problems/letter-combinations-of-a-phone-number/
# Code
    class Solution {
    public:
        vector<string> res;
        string ss;
        string map[10] = {
            "",
            "",
            "abc",
            "def",
            "ghi",
            "jkl",
            "mno",
            "pqrs",
            "tuv",
            "wxyz"
        };
        void backtracing(string digits,int index){
            if(ss.size() == digits.size()){
                res.push_back(ss);
                return;
            }
            // std::cout << digits[index] << std::endl;
            int digit = digits[index] - '0';
            string letters = map[digit];
            for(int i = 0; i < letters.size(); i++){
                ss.push_back(letters[i]);
                backtracing(digits, index+1);
                ss.pop_back();
            }
        }
        vector<string> letterCombinations(string digits) {
            if(digits.size() == 0) return res;
            backtracing(digits,0);
            return res;
        }
    };
# Solution
  * 本题目考察的是 组合 问题，仍然使用 **回溯** 的方法
  * 因为需要组合里面包含每一个数字所对应的字母，所以需要对 数字 产生相应的字母映射
  * 入口参数
    * 这里的 index 不是开始的位置，而是字符串中字母的位置
  * 返回值 仍然是 void
  * 单层逻辑
    * for 循环表示的依然是 多叉树 的宽度，递归的次数是 **多叉树** 的深度
    * 这里的 string 包含 pop_back 函数
