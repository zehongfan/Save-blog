(18.12.27)

# js的事件模型理解

今天来讲一讲js的事件模型。   
有三大类：  

（1）原始事件模型（DOM0级）   
事件发生后没有传播的概念，没有事件流。事件发生，立即处理。     

（2）IE事件模型：只有两步，执行事件的监听函数，接下来