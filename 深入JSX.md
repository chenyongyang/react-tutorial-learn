- JSX本质上是React.createElement(component, props, ...children)的语法糖
- 两者可以通过babel进行转换，代码如下：
```js
<MyButton color="blue" shadowSize={2}>
  Click Me
</MyButton>
React.createElement(
  MyButton,
  {color: 'blue', shadowSize: 2},
  'Click Me'
)
```

## 指定React元素类型
- JSX标签名决定React元素的类型
- JSX标签会被编译成同名变量被引用

### React必须声明
- 编译JSX会用到React.createElement()，因此需要先引入React

### 点表示法
```js
import React from 'react';
const MyComponents = {
  DatePicker: function DatePicker(props) {
    return <div>Imagine a {props.color} datepicker here.</div>;
  }
}
function BlueDatePicker() {
  return <MyComponents.DatePicker color="blue" />;
}
```

### 首字母大写

### 在运行时选择类型
- 不能用表达式作为JSX的标签，下面为错误代码：
```js
function Story(props) {
  // 错误！JSX 标签名不能为一个表达式。
  return <components[props.storyType] story={props.story} />;
}
```
- 正确写法：
```js
function Story(props) {
  // 正确！JSX 标签名可以为大写开头的变量。
  const SpecificStory = components[props.storyType];
  return <SpecificStory story={props.story} />;
}
```

## JSX指定属性的几种方式
- javascript表达式
```js
<MyComponent foo={1 + 2 + 3 + 4} />
```
- 字符串常量
```js
<MyComponent message="hello world" />

<MyComponent message={'hello world'} />
```
- 默认为true
```js
<MyTextBox autocomplete />
<MyTextBox autocomplete={true} />
```
- 扩展属性
  - 会导致很多不相关的属性传递到组件中
```js
function App2() {
  const props = {firstName: 'Ben', lastName: 'Hector'};
  return <Greeting {...props} />;
}
```

## 子代
- JSX标签之间的内容通过props.children来传递
- 子代的几种类型：
  - 字符串常量
  - JSX
  - JavaScript表达式
  - 函数
  - 布尔值、null、undefined被忽略