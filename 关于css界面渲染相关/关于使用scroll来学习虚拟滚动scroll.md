# 关于使用scroll来学习虚拟滚动scroll



比如一个固定的窗口显示数组dom，每一个dom等高，而且需要scroll表示

滚动条所在位置，可以使用以下方法。





首先设置通过当前scrollTop利用scroll事件。



​      

1. scrollTop第一次用来执行更新操作，获取当前展示元素的起点和终点下标。再计算顶部和底部支撑层的高度。之后更新视图，展示元素，修改支撑层，这样scroll就到合适的位置。



2. 当上下滑触发scroll事件scrollTop改变，触发重新计算回到1。