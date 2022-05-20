# Link 
    https://leetcode.cn/problems/kth-largest-element-in-an-array/
# Code
    class Solution {
    public:
        int partition(vector<int>& nums,int l, int r){
            int p = nums[l];
            int i = l + 1, j = r;
            while(1){
                while(i < r && nums[i] <= p){
                    i++;
                }
                while(l < j && nums[j] >= p){
                    j--;
                }
                if(i >= j) break;
                swap(nums[i],nums[j]);
            }
            swap(nums[l],nums[j]);
            return j;
        }
        int findKthLargest(vector<int>& nums, int k) {
            int target = nums.size() - k;
            int l = 0, r = nums.size() -1;
            while(l < r){
                int mid = partition(nums,l,r);
                if(mid < target){
                    l = mid + 1;
                }
                if(mid > target){
                    r = mid - 1;
                }
                if(mid == target)
                    return nums[mid];
            }
            return nums[l];
        }
    };
# Solution
  * 在快排中间，返回 第 k 个中枢，因为每次返回的 中枢 是不会再更改的位置。所以，第 K 大个数，就是倒数第 nums.size() - K 个数字
