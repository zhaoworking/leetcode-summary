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
    class Solution {
    public:
        int quick_sort(vector<int>& nums,int left, int right,int k){
            if(left < 0 || right >= nums.size() || right < left)
                return -1;
            int pivote = rand() % (right - left + 1) + left;
            int pivote_val = nums[pivote];

            swap(nums[pivote],nums[right]);

            int pivote_cnt = left;
            for(int i = left; i < right; i++){
                if(nums[i] < pivote_val){
                    swap(nums[i],nums[pivote_cnt]);
                    pivote_cnt++;
                }
            }
            swap(nums[pivote_cnt],nums[right]);
            if(pivote_cnt < k)
                return quick_sort(nums,pivote_cnt + 1,right,k);
            else if(pivote_cnt > k)
                return quick_sort(nums,left,pivote_cnt - 1,k);
            else if(pivote_cnt == k)
                return nums[k];
            return -1;
        }
        int findKthLargest(vector<int>& nums, int k) {
            return quick_sort(nums,0,nums.size()-1,nums.size() - k);
        }
    };
# Solution
  * 在快排中间，返回 第 k 个中枢，因为每次返回的 中枢 是不会再更改的位置。所以，第 K 大个数，就是倒数第 nums.size() - K 个数字
