https://leetcode-cn.com/problems/remove-nth-node-from-end-of-list/
# Solution
* 一次遍历的方法具有技巧性，同样是双指针的方法，定义一个 **快指针** 和一个 **慢指针**。 快指针先走 n 个节点，然后 两个指针 一起走，当快指针达到尽头的时候，slow 指针指向的就是所要删除的节点的前一个。
# Tips
* 注意 fast 指针先跑的是 n 次
* 使用虚拟节点用来删除头节点
* fast 和 slow 指针共同向前走的时候的终止条件
