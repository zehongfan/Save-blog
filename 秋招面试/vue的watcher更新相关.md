## vue的一些学习

### vue的异步
当你同步时若将数据改变3次显然不合理，可以直接改变最后一次。


### watcher中触发queue队列的排序
因为watcher执行update后是将要执行的watcher放入queue队列中，等异步执行。
排序是因为要按照initcomputed，initwatcher的id排序，如果不按照这样排序，假如更新视图放第一个，那当数据改变又要执行一次视图改变。


### 当queue队列触发新的watcher的插入位置

当触发新的watcher跟据当前位置开始，将新的watcherid插入到相应位置


### cleanupDeps清除依赖收集

因为vue每一次更新视图，都会执行render函数，并再次触发getter去摸一下。所以watcher会有newDeps和旧的deps，依赖清空就是当旧的数据改变时不会通知相应的watcher去执行，这样提高效率。

考虑到一种场景，我们的模板会根据 v-if 去渲染不同子模板 a 和 b，当我们满足某种条件的时候渲染 a 的时候，会访问到 a 中的数据，这时候我们对 a 使用的数据添加了 getter，做了依赖收集，那么当我们去修改 a 的数据的时候，理应通知到这些订阅者。那么如果我们一旦改变了条件渲染了 b 模板，又会对 b 使用的数据添加了 getter，如果我们没有依赖移除的过程，那么这时候我去修改 a 模板的数据，会通知 a 数据的订阅的回调，这显然是有浪费的。