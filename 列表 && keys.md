### 渲染多个组件
- 通过map方法遍历数组，将数组元素和标签结合起来，从而实现数组渲染成列表

### 基础列表组件
- 将列表渲染封装成一个组件，组件接受数组，返回无序列表
- 渲染列表时，每个元素要包含一个key属性
```js
function NumberList(props){
    const numbers = props.numbers;
    const listItems = numbers.map(number=>{
        return (
            <li key={number.toString()}>
                number
            </li>
        )
    });
    return(
        <ul>{listItems}</ul>
    );
}
```

### keys
- 一般用数组中每一项的id来作为key的值
- 如果没有id，则用index
  - 在列表需要重新排序的场景下，index一般不作为key值
```js
const todoItems = todos.map((todo, index) =>
  <li key={index}>
    {todo.text}
  </li>
);
```

### 用keys提取组件
- 主要强调一个key属性绑定的位置
  - key属性应该绑定在map方法中渲染的元素上

### key的唯一性
- 并不是全局唯一，而是在兄弟元素之间的唯一
- 渲染两组不同的列表，可以用同一组id
```js
const sidebar = (
<ul>
    {props.posts.map((post) =>
    <li key={post.id}>
        {post.title}
    </li>
    )}
</ul>
);
const content = props.posts.map((post) =>
<div key={post.id}>
    <h3>{post.title}</h3>
    <p>{post.content}</p>
</div>
);
```
- 以上的key属性都是给react渲染时使用的，组件并不能读取props.key
- 如果需要组件读取到key值，则需定义新的数组属性，并将id赋值给它

### 在jsx中嵌入map()
- 本质上就是在jsx中嵌入js代码，用{}包围起来
```js
function NumberList(props) {
  const numbers = props.numbers;
  return (
    <ul>
      {numbers.map((number) =>
        <ListItem key={number.toString()}
                  value={number} />

      )}
    </ul>
  );
}
```