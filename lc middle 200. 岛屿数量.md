# Code
    class Solution {
    public:
        void dfs(vector<vector<char>>& grid,int rows,int cols){
            // 终止条件
            if(rows >= grid.size() || rows < 0 || cols >= grid[0].size() || cols < 0)
            {
                return;
            }

            if(grid[rows][cols] == '2' || grid[rows][cols] == '0') return;
            // 单层逻辑
            grid[rows][cols] = '2';
            dfs(grid,rows-1,cols);
            dfs(grid,rows+1,cols);
            dfs(grid,rows,cols+1);
            dfs(grid,rows,cols-1);
        }
        int numIslands(vector<vector<char>>& grid) {
            int nums = 0;
            for(int i = 0;i< grid.size(); i++){
                for(int j = 0; j < grid[0].size();j++){
                    if(grid[i][j] == '1'){
                        dfs(grid,i,j);
                        nums++;
                    }
                }
            }
            return nums;
        }
    };
# Solution
  * 岛屿数量问题，使用的是 **深度遍历** 方法。这里是 **图** 的 **深度遍历** ，和二叉树的深度遍历相差不大
  * 深度遍历使用的仍然是递归
    * 终止条件
    * 返回值
    * 单层递归逻辑
# Summary
  * 深度优先遍历，同 二叉树 的深度优先遍历类似
  * 在遇到 ‘1’ 的时候，统计岛屿数量
