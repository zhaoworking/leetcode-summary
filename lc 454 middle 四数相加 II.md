https://leetcode-cn.com/problems/4sum-ii/
## 解题思路
* 因为涉及到了查找的问题，所以往 **哈希法** 去考虑，又因为涉及到出现的**次数**问题，所以 需要使用 unordered_map 数据类型，进行记录 count。
* 一开始想到的是累加前三个数组的和，放在 unordered_map 里面， key 记录出现的是哪三个数值的和， value 记录的是这些和出现的次数。但是，这样的话，时间复杂度会升级为O(n^3)。
* 答案中，则是先累加前两个数组的和，放在 unordered_map 里面， key 记录出现的是哪三个数值的和，value 记录的是这些和出现的次数。从而，在累加后两个数组的和的时候，进行查找 unordered_map 里面是否有对应的数据和。这样就将复杂度从O(n^3)降到了O(n^2)的 level(这一点需要注意).
## Tips
* 在对 unordered_map 进行查找的时候，需要注意到的是前两个数组和的负数
