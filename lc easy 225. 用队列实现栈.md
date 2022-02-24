https://leetcode-cn.com/problems/implement-stack-using-queues
# Solution
* 这题不能像 用栈实现队列 的方式一样去实现，因为 队列 是先进先出，从而两个队列也是先进先出的形式。因此，使用两个队列，一个队列是为了存储相关的数据，另一个队列为了输出
*  queue2 存储 queue1 除最后一个元素前面的所有元素， queue1 输出队列的最后一个元素

# Tips
* queue 可以直接 访问 末尾的元素
* queue 的 pop 方法，返回值为 void
