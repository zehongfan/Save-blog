(18.12.26)   
# js的垃圾回收机制理解

长话短说：  
js的游览器不同机制不同主要有1。标记清除，2.引用计数   

1，标记清除   
大多数游览器都是标记清除。  
当变量进入执行环境，将其标记为“进入环境”，当变量离开环境时标记为“离开环境”。   
垃圾收集器在运行的时候会把内存中的变量都加上标记，然后去掉环境中的变量及被环境变量所引用的变量（即闭包），之后标记了的变量都是要回收的。
 
2，引用计数(主要用在IE游览器)

引用计数就是跟踪每个变量被引用的次数。当声明了一个变量并将一个引用类型赋值给它时引用次数就是1.当这个引用次数变为0时就回收内存。  
引用计数可能造成内存泄漏，因为循环引用变量。


---
垃圾回收器是周期性运行的，按照固定时间执行，IE6是按照内存分配执行的。