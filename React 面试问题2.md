# React 面试问题2



## *Q1*： React 是如何工作的？



React 创建一个虚拟 DOM。当组件中的状态发生变化时，它首先运行一个“差异”算法，该算法识别虚拟 DOM 中发生了什么变化。第二步是协调，它使用 diff 的结果更新 DOM。



## Q2： 什么是*上下文*？



Context 提供了一种通过组件树传递数据的方法，而无需在每个级别手动传递 props。Context 旨在共享可被视为 React 组件树的“全局”数据，例如当前经过身份验证的用户、主题或首选语言。使用上下文，我们可以避免通过中间元素传递道具。

```js
// Context lets us pass a value deep into the component tree
// without explicitly threading it through every component.
// Create a context for the current theme (with "light" as the default).
const ThemeContext = React.createContext('light');

class App extends React.Component {
  render() {
    // Use a Provider to pass the current theme to the tree below.
    // Any component can read it, no matter how deep it is.
    // In this example, we're passing "dark" as the current value.
    return (
      <ThemeContext.Provider value="dark">
        <Toolbar />
      </ThemeContext.Provider>
    );
  }
}

// A component in the middle doesn't have to
// pass the theme down explicitly anymore.
function Toolbar() {
  return (
    <div>
      <ThemedButton />
    </div>
  );
}

class ThemedButton extends React.Component {
  // Assign a contextType to read the current theme context.
  // React will find the closest theme Provider above and use its value.
  // In this example, the current theme is "dark".
  static contextType = ThemeContext;
  render() {
    return <Button theme={this.context} />;
  }
}
```





## Q3： **`props`React 中有什么？**



**Props**是 React 组件的输入。它们是单个值或包含一组值的对象，这些值在创建时使用类似于 HTML 标记属性的命名约定传递给 React 组件。即，*它们是从父组件传递到子组件的数据。*

React 中 props 的主要目的是提供以下组件功能：

1. 将自定义数据传递给您的 React 组件。
2. 触发`state`变化。
3. 通过`this.props.reactProp`内部组件的`render()`方法使用。

例如，让我们创建一个带有 reactProp 属性的元素，

```js
<Element reactProp = "1" />
```

这个`reactProp`（或任何你想出来的）名称然后成为附加到 React 的本机 props 对象的属性，该对象最初已经存在于使用 React 库创建的所有组件上。

```js
props.reactProp;
```



## Q4： `Refs`有什么用？

**添加到 PDF** **入口** ![img](data:image/svg+xml,%3C%3Fxml version='1.0'%3F%3E%3Csvg fill='%23D3D3D3' xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' width='24px' height='24px'%3E%3Cpath d='M11,16.4l-4.7-4.7l1.4-1.4l3.3,3.3l8.4-8.4C17.5,3.3,14.9,2,12,2C6.5,2,2,6.5,2,12s4.5,10,10,10s10-4.5,10-10 c0-1.9-0.5-3.6-1.4-5.1L11,16.4z'/%3E%3C/svg%3E)

**回答**

**Refs**提供了一种访问在 render 方法中创建的 DOM 节点或 React 元素的方法。在大多数情况下应该避免使用它们，但是，当我们需要直接访问 DOM 元素或组件实例时，它们会很有用。

refs 有一些很好的用例：

- 管理焦点、文本选择或媒体播放。
- 触发命令式动画。
- 与第三方 DOM 库集成。

Refs 是使用属性创建并附加到 React 元素的。Refs 通常在构建组件时分配给实例属性，以便可以在整个组件中引用它们。`React.createRef()``ref`

```js
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.myRef = React.createRef();  }
  render() {
    return <div ref={this.myRef} />;  }
}
```



## Q5： 什么是**JEST**？

**Jest**是 Facebook 基于 Jasmine 制作的 JavaScript 单元测试框架，提供自动化的 mock 创建和 jsdom 环境。它通常用于测试 React 组件。



## Q6： ReactJS 的优点是什么？

 

1. 使用 Virtual DOM 提高应用程序的性能
2. JSX 让代码易读易写
3. 它在客户端和服务器端呈现
4. 易于与其他框架（Angular、BackboneJS）集成，因为它只是一个视图库
5. 易于编写 UI 测试用例并与 JEST 等工具集成。



## Q7： **你会如何在 React 中编写内联样式？**

 

```js
<div style={{ height: 10 }}>
```



## Q8： **什么是React**

 

React 是 Facebook 创建的一个开源 JavaScript 库，用于在 Web 和移动应用程序中构建复杂的交互式 UI。React 的核心目的是构建 UI 组件；它通常被称为“MVC”架构中的“V”（视图）。



## Q9： **ReactJS 的主要特点是什么？**

 

ReactJS 的主要特点如下，

- 考虑到 RealDOM 操作成本高昂，它使用**VirtualDOM而不是 RealDOM。**
- 支持**服务端渲染**
- 遵循**单向**数据流或数据绑定
- 使用**可重用/可组合**的 UI 组件来开发视图



## Q10： *class component*和*function component*有什么区别？

 

**class component**

- 基于类的组件使用 ES6 类语法。它可以利用生命周期方法。
- 类组件从 React.Component 扩展而来。
- 在这里，您必须使用此关键字来访问您在类组件中声明的道具和函数。

**function component**

- 与基于类的函数相比，函数式组件更简单。
- 功能组件主要关注应用程序的 UI，而不是行为。
- 更准确地说，这些基本上是类组件中的渲染函数。
- 功能组件可以使用 Reach Hooks 拥有状态和模拟生命周期事件

![q10](/Users/jerry/Desktop/面试/react面试宝典/react--interview-point/图库/q10.png)



## Q11： **使用 React 有什么好处？**

 

- 很容易知道一个组件是如何渲染的，你只需要看一下 render 函数。
- JSX 使阅读组件的代码变得容易。也很容易看到布局，或者组件是如何相互插入/组合的。
- 你可以在服务器端渲染 React。这可以提高 SEO 和性能。
- 这很容易测试。
- 您可以将 React 与任何框架（Backbone.js、Angular.js）一起使用，因为它只是一个视图层。



## Q12： **你应该在 React 组件的哪个位置发出 AJAX 请求？**

  

`componentDidMount`是应该在 React 组件中发出 AJAX 请求的地方。

该方法将在组件第一次“挂载”（添加到 DOM）时执行。此方法仅在组件的生命周期内执行一次。重要的是，您不能保证 AJAX 请求会在组件挂载之前得到解决。如果没有，那意味着您将尝试在未安装的组件上设置状态，这是行不通的。发出 AJAX 请求将保证有要更新的组件。`componentDidMount`



## Q13：`state` 和`props`有什么不一样？

 

- **state**是一个数据结构，当一个组件挂载时，它以一个默认值开始。它可能会随着时间而发生变化，主要是由于用户事件。
- **props**（properties的缩写）是组件的配置。它们是从上面接收的，并且就接收它们的组件而言是不可变的。一个组件不能改变它的 props，但是它负责把它的子组件的 props 放在一起。道具不必只是数据 - 回调函数可以作为道具传入。



## Q14： *展示组件*和*容器组件*有什么区别？

 

- **表示组件**关注*事物的外观*。他们通常只通过 props 接收数据和回调。这些组件很少有自己的状态，但当它们这样做时，通常会关注 UI 状态，而不是数据状态。
- **容器组件**更关心*事物是如何工作*的。这些组件向展示或其他容器组件提供数据和行为。他们调用 Flux 动作并将这些作为回调提供给演示组件。它们通常也是有状态的，因为它们用作数据源。

 

## Q15： React 中`refs`有什么用？

 

 **Refs**是一个逃生舱口，允许您直接访问 DOM 元素或组件的实例。为了使用它们，您向组件添加一个 ref 属性，其值是一个回调函数，它将接收底层 DOM 元素或组件的已安装实例作为其第一个参数。

```js
class UnControlledForm extends Component {
  handleSubmit = () => {
    console.log("Input Value: ", this.input.value)
  }
  render () {
    return (
      <form onSubmit={this.handleSubmit}>
        <input
          type='text'
          ref={(input) => this.input = input} />
        <button type='submit'>Submit</button>
      </form>
    )
  }
}
```

上面注意到我们的输入字段有一个 ref 属性，它的值是一个函数。该函数接收输入的实际 DOM 元素，然后我们将其放在实例上，以便在 handleSubmit 函数内部访问它。

人们经常误解为需要使用类组件才能使用 refs，但通过利用 JavaScript 中的闭包，refs 也可以与功能组件一起使用。

```js
function CustomForm ({handleSubmit}) {
  let inputElement
  return (
    <form onSubmit={() => handleSubmit(inputElement.value)}>
      <input
        type='text'
        ref={(input) => inputElement = input} />
      <button type='submit'>Submit</button>
    </form>
  )
}
```



## Q16： React 中*受控*组件和非*受控*组件有什么区别？

 

这与有状态的 DOM 组件（表单元素）有关，React 文档解释了其中的区别：

- [受控组件](https://facebook.github.io/react/docs/forms.html#controlled-components)是一种通过其当前值并通过回调（如. 父组件通过处理回调和管理自己的状态并将新值作为道具传递给受控组件来“控制”它。您也可以将其称为“哑组件”。`props``onChange`
- [不受控制的组件](https://facebook.github.io/react/docs/uncontrolled-components.html)是在内部存储自己的状态的组件，您可以在需要时使用 a 查询 DOM以找到其当前值。这有点像传统的 HTML。`ref`

大多数原生 React 表单组件都支持受控和不受控的使用：

```js
// Controlled:
<input type="text" value={value} onChange={handleChange} />

// Uncontrolled:
<input type="text" defaultValue="foo" ref={inputRef} />
// Use `inputRef.current.value` to read the current value of <input>
```

在大多数（或所有）情况下，您应该使用受控组件。



## Q17： 什么是*受控组件*？

 **受控组件**是一种通过其当前值并通过回调（如. 父组件通过处理回调和管理自己的状态并将新值作为道具传递给受控组件来“控制”它。您也可以将其称为“哑组件”。`props``onChange`

 ```js
 // Controlled:
 <input type="text" value={value} onChange={handleChange} />
 ```



## Q18： React 中有什么`state`？

 **组件的状态**是一个对象，它包含一些可能在组件的生命周期内发生变化的信息。我们应该始终尝试使我们的状态尽可能简单，并尽量减少有状态组件的数量。

考虑以下：

 ```js
 class User extends React.Component {
    constructor(props) {
       super(props);
 
       this.state = {
          message: "Welcome to React world",
       }
    }
    render() {
       return (
          <div>
             <h1>{this.state.message}</h1>
          </div>
       );
    }
 }
 ```



## Q19： 在 React中*挂载*组件意味着什么？

 它在 DOM 中创建了一个相应的元素并与之连接。



## Q20： 我们如何将 props 从父组件传递给子组件？

 例如：

 ```js
 <ChildComponent someProp={props.someProperty} />
 ```



## Q21： **什么是Fragment?**

这是 React 中的常见模式，用于组件*返回多个元素*。**Fragment**让您可以对子列表进行分组，而无需向 DOM 添加额外的节点。

```js
render() {
  return (
    <React.Fragment>
      <ChildA />
      <ChildB />
      <ChildC />
    </React.Fragment>
  );
}
```

 还有一个**更短的语法**：

```js
render() {
    return (
      <>
         <ChildA />
         <ChildB />
         <ChildC />
      </>
    );
  }
```



## Q22： 渲染列表时，什么是`key` ，它的目的是什么？

 **key**帮助 React 识别哪些项目已更改、添加或删除。应为数组内的元素提供键，以使元素具有稳定的标识。选择键的最佳方法是使用一个字符串，该字符串在其兄弟项中唯一标识一个列表项。

```js
render () {
  return (
    <ul>
      {this.state.todoItems.map(({task, uid}) => {
        return <li key={uid}>{task}</li>
      })}
    </ul>
  )
}
```



## Q23： 如何创建`refs`？

**refs**使用创建`React.createRef()`方法并通过 ref 属性附加到 React 元素。为了在整个组件中使用 refs，只需在构造函数中将 ref 分配给实例属性。

```js
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.myRef = React.createRef();
  }
  render() {
    return <div ref={this.myRef} />;
  }
}
```

和：

```js
class UserForm extends Component {
  handleSubmit = () => {
    console.log("Input Value is: ", this.input.value)
  }
  render () {
    return (
      <form onSubmit={this.handleSubmit}>
        <input
          type='text'
          ref={(input) => this.input = input} /> // Access DOM input in handle submit
        <button type='submit'>Submit</button>
      </form>
    )
  }
}
```

我们还可以在闭包的帮助下在**function component**中使用它。



## Q24： React Hooks：React 中什么是`useState()`？

 ```js
 ...
 const [count, setCounter] = useState(0);
 const [moreStuff, setMoreStuff] = useState(...);
 ...
 
 const setCount = () => {
     setCounter(count + 1);
     setMoreStuff(...);
     ...
 };
 ```

`useState`是内置的反应钩子之一。返回一个元组，其中第一个参数 count 是计数器的当前状态，而 setCounter 是允许我们更新计数器状态的方法。`useState(0)`

我们可以在任何地方使用该方法更新 count 的状态——在这种情况下，我们在 setCount 函数中使用它，我们可以做更多的事情；使用钩子的想法是，如果不需要/不需要，我们能够使我们的代码更具功能性并避免基于类的组件。`setCounter`

 

## Q25： 

 

## Q26： 

 

## Q27： 

 



## Q28： 

 

## Q29： 

 

## Q30： 

 

## Q31： 

 

## Q32： 

 

## Q33： 

 

## Q34： 

 

## Q35： 

 



## Q36： 

 

## Q37： 

 

## Q38： 

 

## Q39： 

 



## Q40： 

 

## Q41： 

 

## Q42： 

 

## Q43： 

 

## Q44： 

 

## Q45： 

 

## Q46： 

 

## Q47： 

 



## Q48： 

 

## Q49： 

 

## Q50： 

 

## Q51： 

 



## Q52： 

 

## Q53： 

 

## Q54： 

 

## Q55： 

 

## Q56： 

 

## Q57： 

 

## Q58： 

 

## Q59： 

 



## Q60： 

 

## Q61： 

 

## Q62： 

 

## Q63： 

 



## Q64： 

 

## Q65： 

 

## Q66： 

 

## Q67： 

 

## Q68： 

 

## Q69： 

 

## Q70： 

 

## Q71： 

 



## Q72： 

 

## Q73： 

 

## Q74： 

 

## Q75： 

 



## Q76： 

 

## Q77： 

 

## Q78： 

 

## Q79： 

 

## Q80： 

 

## Q81： 

 

## Q82： 

 

## Q83： 

 



## Q84： 

 

## Q85： 

 

## Q86： 

 

## Q87： 

 



## Q88： 

 

## Q89： 

 

## Q90： 

 

## Q91： 

 

## Q92： 

 

## Q93： 

 

## Q94： 

 

## Q95： 

 



## Q96： 

 

## Q97： 

 

## Q98： 

 

## Q99： 

 



## Q100： 

 

## Q101： 

 

## Q102： 

 

## Q103： 

 

## Q104： 

 

## Q105： 

 

## Q106： 

 

## Q107： 

 



## Q108： 

 

## Q109： 

 

## Q110： 

 

## Q111： 

 



## Q112： 

 

## Q113： 

 

## Q114： 

 

## Q115： 

 

## Q116： 

 

## Q117： 

 

## Q118： 

 

## Q119： 

 



## Q120： 

 

## Q121： 

 

## Q122： 

 

## Q123： 

 



## Q124： 

 

## Q125： 

 

## Q126： 

 

## Q127： 

 

## Q128： 

 

## Q129： 

 

## Q130： 

 

## Q131： 

 



## Q132： 

 

## Q133： 

 

## Q134： 

 

## Q135： 

 



## Q136： 

 

## Q137： 

 

## Q138： 

 

## Q139： 

 

## Q140： 

 

## Q141： 

 

## Q142： 

 

## Q143： 

 



## Q144： 

 

## Q145： 

 

## Q146： 

 

## Q147： 

 



## Q148： 

 

## Q149： 

 

## Q150： 