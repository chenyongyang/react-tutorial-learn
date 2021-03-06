### 划分UI的组件层次
- 单一功能原则

### 用React创建一个静态版本
- 静态版本不需要使用state，state只有在交互时使用

### 定义UI状态的最小的、完整的表示
- 原则为DRY，don't repeat yourself
- 一个数据不该为state的三个条件
  - 它是通过props从父组件传递下来的
  - 它不会随时间而改变
  - 它可以通过其他state或props计算得到

### 确定state应该位于哪里
- 判断哪个组件拥有state
- 判断方法：
  - 确定每一个需要state的组件
  - 找到包含它们的公共组件或更高层级的组件（它们应该拥有这个state）
  - 如果没有找到，那就创建一个

### 添加反向数据流
- 父组件将一个回调函数传递给子组件
- 子组件监听事件，触发父组件传递的回调函数
- 父组件的回调函数会调用setState()
- setState()调用render()，界面更新