React是一个前端UI库。我对React的理解主要就两点：

1. **[组件化](https://zhida.zhihu.com/search?content_id=131308202&content_type=Article&match_order=1&q=%E7%BB%84%E4%BB%B6%E5%8C%96&zhida_source=entity)**
2. **数据驱动**

**在React基础上**，周边生态提供了更多强大功能：[状态管理](https://zhida.zhihu.com/search?content_id=131308202&content_type=Article&match_order=1&q=%E7%8A%B6%E6%80%81%E7%AE%A1%E7%90%86&zhida_source=entity)、[路由](https://zhida.zhihu.com/search?content_id=131308202&content_type=Article&match_order=1&q=%E8%B7%AF%E7%94%B1&zhida_source=entity)、[React Native](https://zhida.zhihu.com/search?content_id=131308202&content_type=Article&match_order=1&q=React+Native&zhida_source=entity)等。

### 一、组件化

这里就有了第一个抽象概念：​**组件**​。

> 什么是组件？组件是对逻辑的封装。对于前端 UI 层来说，组件就是将 UI 封装起来。供任意组装和调用。

太抽象了？我提炼成三个点，帮助大家理解：

1. 写React就是写组件。将一个**界面**分成若干个**组件**，**组合**包装成完整页面
2. 写每一个组件的时候：每个组件有自己的**生命周期**，在组件不同的周期里做自己想要做的逻辑
3. 子组件**接受**父组件的**参数(Props)** 、 以及维护组件**内部的状态(State)**

#### 最简单的组件 **HelloWorld**

下面我们看一个最简单的**类组件 HelloWorld**：

```js
// HelloWorld.jsx
class HelloWorld extends React.Component {
  componentDidMount () {
    console.log('HelloWorld 第一次挂载到界面上');
  }
  componentWillUnmount () {
    console.log('HelloWorld 即将移除（销毁）');
  }
  render() {
    return (
      <div>Hello World！</div>
    );
  }
}
```

这样就完成了一个简单的 ​**HelloWorld​ 组件**。

1. **componentDidMount**、**componentWillUnmount**是两个常用的[生命周期函数](https://zhida.zhihu.com/search?content_id=131308202&content_type=Article&match_order=1&q=%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F%E5%87%BD%E6%95%B0&zhida_source=entity)，传送门：[更多生命周期](https://link.zhihu.com/?target=https%3A//www.runoob.com/react/react-component-life-cycle.html)。
2. **render** 函数在每次渲染时调用，**返回的内容就是组件最终的界面，**示例中return 了一个Hello World 的 div。

#### 子组件调用示例

再写一个 按钮组件 ​**HelloButton**​

```text
// HelloButton.jsx
class HelloButton extends React.Component {
  render() {
    return (
      <button>我是一个按钮</button>
    );
  }
}
```

写一个父组件 把 HelloWorld 和 HelloButton 两个组件包裹进来

```text
// Wrap.jsx
class Wrap extends React.Component {
  render() {
    return (
      <div>
        <HelloWorld></HelloWorld>
        <HelloButton></HelloButton>
      </div>
    );
  }
}
```

可以看到 React 调用子组件其实就是把**子组件当做一个标签**，跟 div 这些标签一样。

Wrap 组件**最终的展示**就是，一个HelloWord 组件 + 一个HelloButton 组件，如下图。

![](https://pic1.zhimg.com/v2-d046a8e93e917bba2fe7469385b99108_1440w.jpg)

Wrap组件效果图

#### 组件化小结

基于对组件化的理解：**写 React 就是写一个个组件**，再组装起来。所以如果用**分治**的思想，我们**只要关注每个组件**怎么实现就好了。

### 二、数据驱动

现在来讲我的另一个理解——**​数据驱动**​，那么组件有哪些数据呢？

组件有两种数据：**父组件传递的参数 Props**和**组件内部的状态State**，先来分别看一个例子。

#### 组件的状态 State

先来看效果：

![](https://pic4.zhimg.com/v2-6b83a8b6dccf4257ca086034ca626091_1440w.jpg)

组件 State 示例，效果图

完整代码如下：

```text
// App.jsx 
class App extends React.Component {
  constructor () {
    super()
    this.state = {
      count: 0
    }
  }
  onIncrease = () => {
    this.setState({ count: this.state.count + 1 })
  }
  onDecrease = () => {
    this.setState({ count: this.state.count - 1 })
  }
  render() {
    return (
      <div>
        <div>当前数值：{this.state.count}</div>
        <button onClick={this.onIncrease}>点我-1</button>
        <button onClick={this.onDecrease}>点我+1</button>
      </div>
    );
  }
}
```

解析：

1. constructor方法中，设置了一个 State 属性 ​**count**​，初始值为 0；
2. 声明了两个方法 ​**onIncrease**​ 和 ​**onDecrease**​，方法里对 count 设置了 +-1 的操作；
3. render 函数里渲染了一行文字 + 两个按钮，这里有两个注意点：

4. return里面的内容是 jsx 模板，大括号内的内容是一个 js 变量或者表达式，React 会自动渲染。例如 ​**{this.state.count}​** 渲染时就会渲染成count的值
5. 给 button 指定了属性(Props) ​**onClick**​，即当 button 点击时，会自动调用 指定的函数。

建议没看到上面例子的同学，带着上面的解析，重新尝试能否看懂。

上面的例子中，​**count**​ 就是 **App组件** 的一个 State

1. 用来直接将 count 显示在界面上；
2. 当接收到点击事件时，改变了 count 这个 State。

#### 父组件传递的属性 Props

从语义上理解：Props 是父组件传递给子组件的属性，与 State 不同的是子组件不能修改，只有父组件才能修改。

先看看如何使用 Props：

```text
// HelloMessage.jsx
class HelloMessage extends React.Component {
  render() {
    return (
      <div>
        <div>Hello {this.props.username}</div>
      </div>
    );
  }
}
```

上述例子，**使用的示例**、效果如下：

`<HelloMessage username="秦书羽" />`

![](https://pic4.zhimg.com/v2-d83a27b6a1df2d023c0ac53a8e16c321_1440w.jpg)

Props 使用效果图

解析：子组件在使用Props时，使用 **​this.props​** 直接调用即可，父组件在使用子组件时，应将需要的数据传给子组件。

#### 数据驱动的理解

**上面两个例子中，界面都是根据数据来渲染，且随着数据变化，自动更新，这就是数据驱动渲染。**

再说下数据驱动的理解：

1. 界面的渲染，由数据(State和Props)决定，数据变更**驱动**页面更新；
2. 人机交互(点击、按钮操作等)驱动**数据变更**，界面根据数据自动更新；
3. 对于开发者，开发一个组件，需要分成两部分：数据 和 视图，再根据用户行为，修改数据即可

从这个方面去理解，React 是一个 **Model -> View** 的一个框架。

![](https://pic2.zhimg.com/v2-d6019ee0846f87b8615b58a8cf6de77b_1440w.jpg)

“数据驱动”的理解图

#### 数据驱动模式带来的收益

个人见解：

1. 数据和视图分层，逻辑解耦清晰，优雅的多；
2. 人机交互的行为太多、先点哪个按钮、再点哪个按钮，传统开发方式需要判断的东西太多，数据驱动的话，只需要根据当前的数据，修改对应的数据，大大简化；
3. 利于单元测试。

### 三、总结

1. 在**开发模式上**，React 给我们带来了 **组件化和数据驱动**。其内部也基于此做了大量的性能优化；
2. React 是一个**基础的 UI 库**，作者和社区提供了更多配套，如React-Router(路由)、[Redux](https://zhida.zhihu.com/search?content_id=131308202&content_type=Article&match_order=1&q=Redux&zhida_source=entity)(全局状态管理)，同学们可以在 React 的理解基础上 **向上扩展；**
3. 本文都是在讲 React 的 **组件化和数据驱动。**但我认为不是因为有了 React 才有 **组件化和数据驱动**，而是**先**有 **组件化和数据驱动** 的想法，为了达到这样的设计，最终实现了 React 。本文没有涉及原理，有兴趣的同学可以自行学习。