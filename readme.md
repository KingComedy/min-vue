## Vue2的响应式实现流程
+ Vue初始化时，会把data里的所有数据通过Object.defineProperty进行数据劫持，即重写数据的get和set。所以只有初始化时的属性才有响应式，新增的属性得通过$set,才会进行响应式处理
+ data里的每个属性，都会有属于自己的依赖收集的实例，new Dep。属性get时，进行收集观察者，属性set时，通知所有观察者执行更新函数
+ 对数据做响应式处理后，执行编译。当编译到指令执行dom更新时，同时创建观察者，传入更新函数
+ 观察者初始化时，通过触发属性的get，将观察者添加到相对应属性的 依赖收集里。
+ 在对属性重新设值的时候，dep会同时触发所有观察者的更新函数

## 源码实现

## 关键点
### 观察者怎么与属性依赖收集建立关系
### 属性更新时，怎么让dom重新渲染
### 数组怎么做响应式