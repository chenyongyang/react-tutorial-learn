BrowserRouter/HashRouter的区别和应用场景
- 前者服务器需要能够处理动态请求
- 后者提供静态文件的服务

Router
- 只希望接收一个子元素

Route
- only care about the pathname of a location

Route关于render的三个属性
- component
- render
  - inline rendering
  - pass the extra props to the element
- children
  - 总是被渲染，不管path是否匹配当前路径
- 没有额外的属性传递给组件的话，一般就用component来渲染
```js
<Route path='/page' component={Page} />
const extraProps = { color: 'red' }
<Route path='/page' render={(props) => (
  <Page {...props} data={extraProps}/>
)}/>
<Route path='/page' children={(props) => (
  props.match
    ? <Page {...props}/>
    : <EmptyPage {...props}/>
)}/>
```

Path params
- 产生一个包含参数和参数值的对象
- 对象值是字符串类型

Link
- to参数可以接受字符串或者一个对象
- 对象拥有的属性：pathname / search / hash / state
- pathname must be absolute
```js
// a basic location object
{ pathname: '/', search: '', hash: '', key: 'abc123' state: {} }
```

pathless Route
- match every location
