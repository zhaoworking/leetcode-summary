https://leetcode-cn.com/problems/implement-queue-using-stacks/
# Solution
* 本题是用 stack 来模拟 队列，stack 是容器适配器，可以用 deque 或者 list 容器来实现。其中，这里的 deque 和 list 只能是使用 栈 的最基本的操作。
* 此题可以使用两个 栈 来模拟-- 进栈和出栈，当 出栈 为空的时候，将 进栈 的所有数据都塞到 出栈 中，从而实现了 先进先出 的规则。
# Tips
* 在删除元素的时候，不能使用 for 循环的方式去遍历 stackIn 里面的数据，因为 stackIn 的大小一直在变化。
