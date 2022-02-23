https://leetcode-cn.com/problems/intersection-of-two-linked-lists-lcci/
# Solution
* 此题重点在于检测 A 链表和 B 链表相交的节点，在分别遍历 A 链表和 B 链表的过程中，统计各自的长度。将长度差作为遍历的次数，使两链表在第二次遍历中处于相同的起始点，再共同进行遍历
# Tips
* 指针相等，而非指针所指的值相等
* 将两链表的起始点遍历到相同的位置
