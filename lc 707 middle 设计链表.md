https://leetcode-cn.com/problems/design-linked-list/

## 解题思路：

这里是常用的链表几种方法，分别是 get addhead addtail addatindex 和 deleteindex。
**Tips:**需要注意的是，在所有的有关链表的算法中，设计一个dummy头节点都是最方便的方法，因为在添加或者删除 **头节点** 的时候，不用多种判断方法。

* 定义一个 **ListNode** 的 数据类型

* 临界条件的判断 分别是 index < 0 和 index  > size -1

* 不能直接使用dummy指针进行遍历，另外初始化一个指针，作用和dummy指针相同
* get 方法中初始化的指针为 dummy->next 更为直观
* delete 方法中要释放内存
