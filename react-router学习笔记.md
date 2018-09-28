## react-router学习笔记
### react-router和react-router-dom的区别
- react-router提供了router route switch等接口，但没有提供dom操作进行跳转的api
- react-router-dom提供了browserRouter link等接口，我们可以通过dom的事件控制路由，例如点击按钮进行跳转
- 因此开发中更多地是使用react-router-dom

### react-router-dom用法
- hashRouter
  - 它是通过hash值来对路由进行控制
- browserRouter
  - 使用HTML5 history API (pushState, replaceState, popState)来使你的内容随着url动态改变的
  - 基础api，basename
- route
  - 控制路径对应显示的组件
  - 经常用的是exact、path以及component属性
- link
  - 主要api是to，to可以接受string或者一个object，来控制url
- navLink
  - 可以为当前选中的路由设置类名、样式以及回调函数
- match
  - 使用router之后被放入props中的一个属性
  - 通过this.props.match来获取
  - 常常会获取id进行使用
- switch
  - 用来包裹route，不能放其他元素，用来只能显示一个路由
