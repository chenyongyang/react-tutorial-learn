组件约等于函数，接收任何的输入（props），返回React元素

### 函数定义组件
- 接收props对象，返回React元素
```jsx
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
```

### 类定义组件
```jsx
class Welcome extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}
```

### 组件渲染
- 组件名必须以大写字母开头
```jsx
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

const element = <Welcome name="Sara" />;
ReactDOM.render(
  element,
  document.getElementById('root')
);
```
组件渲染的过程：
- <Welcome name="Sara" />这个react元素调用ReactDOM.render()
- react将{name: 'sara'}传入Welcome组件
- Welcome组件返回<h1>Hello, sara</h1>元素
- React DOM将其渲染到页面上


### 组合组件
- 组件的返回值只能有一个根元素
```jsx
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

function App() {
  return (
    <div>
      <Welcome name="Sara" />
      <Welcome name="Cahal" />
      <Welcome name="Edite" />
    </div>
  );
}

ReactDOM.render(
  <App />,
  document.getElementById('root')
);
```

### 提取组件
- 不断将组件划分得更小
- props的命名从组件的功能出发

### props的只读性
- 组件不能改变自己的props
- 纯函数/非纯函数