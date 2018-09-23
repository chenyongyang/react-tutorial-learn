复用组件代码，用组合，不用继承

### 包含关系
- this.props.children，所有被包含的元素都会被渲染
- 一个组件有多个入口，使用自定义属性（有点类似于vue中的具名slot）
```js
function SplitPane(props) {
  return (
    <div className="SplitPane">
      <div className="SplitPane-left">
        {props.left}
      </div>
      <div className="SplitPane-right">
        {props.right}
      </div>
    </div>
  );
}

function App() {
  return (
    <SplitPane
      left={
        <Contacts />
      }
      right={
        <Chat />
      } />
  );
}
```

### 特殊实例
- 通过配置props，实现用特殊组件来渲染通用组件
- 下面这个例子中，通过对dialog通用组件传递特定的props，实现welcomedialog组件
```js
function WelcomeDialog() {
  return (
    <Dialog
      title="Welcome"
      message="Thank you for visiting our spacecraft!" />

  );
}
```

- 使用属性和组合来自定义组件的样式和行为