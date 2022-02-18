https://leetcode-cn.com/problems/two-sum/
## 解题思路：
这个同样是哈希方法，只不过这里需要返回的是元素的下标，不能使用 set 进行操作，这里使用 map 具有 key 和 value 的数据结构进行操作。又因为这里返回的元素下标并非有序，使用 unordered_map 效率更高。
std::unordered_map 底层实现为哈希表，std::map 和std::multimap 的底层实现是红黑树。

**Tips :**
因为，map 中的 find 方法使用通过查找 key 来返回迭代器指针的，j即: Get iterator to element. Searches the container for an element with a key equivalent to k and returns an iterator to it if found, otherwise it returns an iterator to map::end.
所以，这里将 **数组元素的值** 放入下表中，每次查找 总和 targert 的值减去遍历的元素值，从而返回 下标索引。
