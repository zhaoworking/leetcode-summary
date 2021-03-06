# Solution
* 二叉树的层序遍历，等同于 二叉树的 **广度遍历**，与二叉树的 **深度遍历** 不同的是，这里的 广度遍历 使用的是 队列 进行遍历，利用了其先进先出的特性。而 深度遍历 使用递归的方式或者栈迭代的方式。
* 广度遍历 需要按照先后的顺序输出每一层的孩子节点，而深度遍历则是到树的底层，然后一层一层的返回输出

# Tips
* root 节点是 nullptr 的情况，立即返回
* 队列 先进先出， 当 pop 出去某个节点的时候，把节点 val 放入 vec ，然后把 他的 孩子节点都加进来
* 每次需要循环的次数是此时队列的 size 个数，所以要提前固定 size 
