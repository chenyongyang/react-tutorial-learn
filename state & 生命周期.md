目前为止，更新UI有两种方法：
- 将新元素传入ReactDOM.render()
- 用state来更新

状态是私有的，受控于组件自身

state状态是类定义组件独有的特性

### 给类组件添加局部状态
- 类组件的基础构造函数只能通过props来调用
```js
constructor(props) {
super(props);
    this.state = {date: new Date()};
}
```

### 为类组件添加生命周期方法
- 挂载/卸载
- 类似于存储定时器的变量timer，不需要在render用到，就不要在state中声明

### 正确使用state
- 不要直接更新状态，应该用setState()
  - 唯一初始化state的只有构造函数
- state的更新可能是异步的
  - 因为react将多个setState()合并为一个调用，目的是为了提高性能
  - 产生的问题：无法在setState中立即对新的状态进行其他操作
  - 解决方法：让setState()接收的参数从对象改变为函数，这个函数接收两个参数，分别为prevState、props
- 状态更新合并
  - 浅合并（此处不太懂）

### 数据自顶向下流动（单向数据流）
- 组件可以将其状态作为属性传递给其子组件
- 将组件树想象为一个props的瀑布流，每个组件都可以获得外来的水源（state），也可以向下流动