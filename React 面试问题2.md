### React 面试问题2



## Entry



### Q1： **什么是React**

 

React 是 Facebook 创建的一个开源 JavaScript 库，用于在 Web 和移动应用程序中构建复杂的交互式 UI。React 的核心目的是构建 UI 组件；它通常被称为“MVC”架构中的“V”（视图）。



### Q2： **ReactJS 的主要特点是什么？**

 

ReactJS 的主要特点如下，

- 考虑到 RealDOM 操作成本高昂，它使用**VirtualDOM而不是 RealDOM。**
- 支持**服务端渲染**
- 遵循**单向**数据流或数据绑定
- 使用**可重用/可组合**的 UI 组件来开发视图



### Q3： React 是如何工作的？



React 创建一个虚拟 DOM。当组件中的状态发生变化时，它首先运行一个“差异”算法，该算法识别虚拟 DOM 中发生了什么变化。第二步是协调，它使用 diff 的结果更新 DOM。

### Q4： ReactJS 的优点是什么？

 

1. 使用 Virtual DOM 提高应用程序的性能
2. JSX 让代码易读易写
3. 它在客户端和服务器端呈现
4. 易于与其他框架（Angular、BackboneJS）集成，因为它只是一个视图库
5. 易于编写 UI 测试用例并与 JEST 等工具集成。



### Q5： **React 中的`props`是什么？**



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



### Q6： **你会如何在 React 中编写内联样式？**

 

```js
<div style={{ height: 10 }}>
```



### Q7： 什么是*上下文*？



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



### Q8： `Refs`有什么用？



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



### Q9： 什么是**JEST**？

**Jest**是 Facebook 基于 Jasmine 制作的 JavaScript 单元测试框架，提供自动化的 mock 创建和 jsdom 环境。它通常用于测试 React 组件。



## Junior

### Q10： *class component*和*function component*有什么区别？

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



### Q11： **使用 React 有什么好处？**

 

- 很容易知道一个组件是如何渲染的，你只需要看一下 render 函数。
- JSX 使阅读组件的代码变得容易。也很容易看到布局，或者组件是如何相互插入/组合的。
- 你可以在服务器端渲染 React。这可以提高 SEO 和性能。
- 这很容易测试。
- 您可以将 React 与任何框架（Backbone.js、Angular.js）一起使用，因为它只是一个视图层。



### Q12： **你应该在 React 组件的哪个位置发出 AJAX 请求？**

  

`componentDidMount`是应该在 React 组件中发出 AJAX 请求的地方。

该方法将在组件第一次“挂载”（添加到 DOM）时执行。此方法仅在组件的生命周期内执行一次。重要的是，您不能保证 AJAX 请求会在组件挂载之前得到解决。如果没有，那意味着您将尝试在未安装的组件上设置状态，这是行不通的。发出 AJAX 请求将保证有要更新的组件。`componentDidMount`



### Q13：`state` 和`props`有什么不一样？

 

- **state**是一个数据结构，当一个组件挂载时，它以一个默认值开始。它可能会随着时间而发生变化，主要是由于用户事件。
- **props**（properties的缩写）是组件的配置。它们是从上面接收的，并且就接收它们的组件而言是不可变的。一个组件不能改变它的 props，但是它负责把它的子组件的 props 放在一起。道具不必只是数据 - 回调函数可以作为道具传入。



### Q14： *展示组件*和*容器组件*有什么区别？

 

- **表示组件**关注*事物的外观*。他们通常只通过 props 接收数据和回调。这些组件很少有自己的状态，但当它们这样做时，通常会关注 UI 状态，而不是数据状态。
- **容器组件**更关心*事物是如何工作*的。这些组件向展示或其他容器组件提供数据和行为。他们调用 Flux 动作并将这些作为回调提供给演示组件。它们通常也是有状态的，因为它们用作数据源。

 

### Q15： React 中`refs`有什么用？

 

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



### Q16： React 中*受控*组件和非*受控*组件有什么区别？

这与有状态的 DOM 组件（表单元素）有关，React 文档解释了其中的区别：

- [受控组件](https://facebook.github.io/react/docs/forms.html#controlled-components)是一种通过`props`获取其当前值并通过`onChange` 等回调通知更改的组件。父组件通过处理回调和管理自己的状态并将新值作为props传递给受控组件来“控制”它。 您也可以将其称为“哑组件”。
- [不受控制的组件](https://facebook.github.io/react/docs/uncontrolled-components.html)是在内部存储自己的状态的组件，您可以在需要时使用 `ref` 查询 DOM 以找到其当前值。 这有点像传统的 HTML。

This relates to stateful DOM components (form elements) and the React docs explain the difference:

- A [Controlled Component](https://facebook.github.io/react/docs/forms.html#controlled-components) is one that takes its current value through `props` and notifies changes through callbacks like `onChange`. A parent component "controls" it by handling the callback and managing its own state and passing the new values as props to the controlled component. You could also call this a "dumb component".
- A [Uncontrolled Component](https://facebook.github.io/react/docs/uncontrolled-components.html) is one that stores its own state internally, and you query the DOM using a `ref` to find its current value when you need it. This is a bit more like traditional HTML.

大多数原生 React 表单组件都支持受控和不受控的使用：

```js
// Controlled:
<input type="text" value={value} onChange={handleChange} />

// Uncontrolled:
<input type="text" defaultValue="foo" ref={inputRef} />
// Use `inputRef.current.value` to read the current value of <input>
```

在大多数（或所有）情况下，您应该使用受控组件。



### Q17： 什么是*受控组件*？

**受控组件**是通过`props`获取其当前值并通过`onChange`之类的回调通知更改的组件。父组件通过处理回调和管理自己的状态并将新值作为props传递给受控组件来“控制”它。您也可以将其称为“哑组件”。

A **Controlled Component** is one that takes its current value through `props` and notifies changes through callbacks like `onChange`. A parent component "controls" it by handling the callback and managing its own state and passing the new values as props to the controlled component. You could also call this a "dumb component".

 ```js
 // Controlled:
 <input type="text" value={value} onChange={handleChange} />
 ```



### Q18： React 中`state`是什么？

**组件的状态**是一个对象，它包含一些可能在组件的生命周期内发生变化的信息。我们应该始终尝试使我们的状态尽可能简单，并尽量减少有状态组件的数量。

**State** of a component is an object that holds some information that may change over the lifetime of the component. We should always try to make our state as simple as possible and minimize the number of stateful components.

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



### Q19： 在 React中*挂载*组件意味着什么？

 它在 DOM 中创建了一个相应的元素并与之连接。



### Q20： 我们如何将 props 从父组件传递给子组件？

 例如：

 ```js
 <ChildComponent someProp={props.someProperty} />
 ```



### Q21： **什么是Fragment?**

这是 React 中的常见模式，用于组件*返回多个元素*。**Fragment**让您可以对子列表进行分组，而无需向 DOM 添加额外的节点。

It's common pattern in React which is used for a component to *return multiple elements*. **Fragments** let you group a list of children without adding extra nodes to the DOM.

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



### Q22： 渲染列表时，什么是`key` ，它的目的是什么？

**key**帮助 React 识别哪些项目已更改、添加或删除。应为数组内的元素提供键，以使元素具有稳定的标识。选择键的最佳方法是使用一个字符串，该字符串在其兄弟项中唯一标识一个列表项。

*Keys* help React identify which items have changed, are added, or are removed. Keys should be given to the elements inside the array to give the elements a stable identity. The best way to pick a key is to use a string that uniquely identifies a list item among its siblings.

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



### Q23： 如何创建`refs`？

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



### Q24： React Hooks：React 中什么是`useState()`？

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

`useState`是内置的react hooks之一。`useState(0)`返回一个元组，其中第一个参数 count 是计数器的当前状态，而 setCounter 是允许我们更新计数器状态的方法。

我们可以使用`setCounter`在任何地方该方法更新 count 的状态——在这种情况下，我们在 setCount 函数中使用它，我们可以做更多的事情；使用钩子的想法是，如果不需要/不需要，我们能够使我们的代码更具功能性并避免基于类的组件。

`useState` is one of build-in react hooks. `useState(0)` returns a tuple where the first parameter count is the current state of the counter and setCounter is the method that will allow us to update the counter's state.

We can use the `setCounter` method to update the state of count anywhere - In this case we are using it inside of the setCount function where we can do more things; the idea with hooks is that we are able to keep our code more functional and avoid class based components if not desired/needed.



### Q25：  **React Native 和 React 有什么区别？**

- **ReactJS**是一个 JavaScript 库，支持前端 Web 并在服务器上运行，用于构建用户界面和 Web 应用程序。
- **React Native**是一个编译成原生应用程序组件的移动框架，允许您使用 JavaScript 构建原生移动应用程序（iOS、Android 和 Windows），允许您使用 ReactJS 构建您的组件，并在后台实现 ReactJS。

- **ReactJS** is a JavaScript library, supporting both front end web and being run on the server, for building user interfaces and web applications.
- **React Native** is a mobile framework that compiles to native app components, allowing you to build native mobile applications (iOS, Android, and Windows) in JavaScript that allows you to use ReactJS to build your components, and implements ReactJS under the hood.

### Q26： **你将如何防止组件在 React 中呈现？**

 从渲染方法返回`null`。



### Q27： **什么是 JSX？**

 JSX 是**JavaScript XML**的语法表示法（ECMAScript 的类似 XML 的语法扩展）。它代表 JavaScript XML。它提供了 JavaScript 的表现力以及类似 HTML 的模板语法。例如，下面的 h1 标签内的文本作为 javascript 函数返回给 render 函数，

JSX is a syntax notation for **JavaScript XML**(XML-like syntax extension to ECMAScript). It stands for JavaScript XML. It provides expressiveness of JavaScript along with HTML like template syntax. 

```js
render(){
    	return(
         <div>
            <h1> Welcome to React world!!</h1>
         </div>
    	);
     }
```



### Q28： **React 的局限性是什么？**

1. **React 只是一个视图库，而不是一个成熟的框架**
2. **对于刚接触 Web 开发的初学者来说，有一个学习曲线。**
3. **将 React.js 集成到传统的 MVC 框架中需要一些额外的配置**
4. **内联模板和 JSX 会增加代码复杂性。**
5. **太多较小的组件导致过度设计或样板**

1. React is just a view library, not a full-blown framework
2. There is a learning curve for beginners who are new to web development.
3. Integrating React.js into a traditional MVC framework requires some additional configuration
4. The code complexity increases with inline templating and JSX.
5. Too many smaller components leading to over-engineering or boilerplate

### Q29：**什么是有状态组件？**

如果组件的行为依赖于组件的状态，那么它可以称为*有状态组件*。这些有状态的组件始终是类组件，并且具有在构造函数中初始化的状态。

If the behaviour of a component is dependent on the state of the component then it can be termed as *stateful component*. These Stateful components are always class components and have a state that gets initialized in the constructor.

```js
class App extends Component {
 constructor(props) {
  super(props);
  this.state = { count: 0 };
 }

 render() {
    // omitted for brevity
  }
}
```



### Q30： 什么是*无状态组件*？

如果行为独立于其状态，那么它可以是**无状态组件**。您可以使用函数或类来创建无状态组件。但除非您需要使用生命周期挂钩在组件中，否则您应该选择无状态功能组件。

If the behaviour is independent of its state then it can be a **stateless component**. You can use either a function or a class for creating stateless components. But unless you need to use a lifecycle hook in your components, you should go for stateless functional components.

**有状态/容器/智能组件**：

```js
class Main extends Component {
 constructor() {
   super()
   this.state = {
     books: []
   }
 }
 render() {
   <BooksList books={this.state.books} />
 }
}
```

**无状态/演示/哑组件：**

```js
const BooksList = ({books}) => {
 return (
   <ul>
     {books.map(book => {
       return <li>book</li>
     })}
   </ul>
 )
}
```

如果您决定在这里使用无状态功能组件，会有很多好处；他们是：

- 易于编写、理解和测试，并且

- 您可以完全避免使用 this 关键字

  

### Q31： **React 与 AngularJS (1.x) 有何不同？**

例如，AngularJS (1.x) 通过扩展 HTML 标记和在运行时注入各种结构（例如指令、控制器、服务）来构建应用程序。因此，AngularJS 对应用程序的更大架构非常固执己见——这些抽象在某些情况下当然有用，但它们是以灵活性为代价的。

相比之下，React 只专注于组件的创建，并且对应用程序的架构几乎没有（如果有的话）意见。这使得开发人员在选择他们认为“最佳”的架构时具有难以置信的灵活性——尽管它也将选择（或构建）这些部分的责任放在了开发人员身上。

For example, AngularJS (1.x) approaches building an application by extending HTML markup and injecting various constructs (e.g. Directives, Controllers, Services) at runtime. As a result, AngularJS is very opinionated about the greater architecture of your application — these abstractions are certainly useful in some cases, but they come at the cost of flexibility.

By contrast, React focuses exclusively on the creation of components, and has few (if any) opinions about an application’s architecture. This allows a developer an incredible amount of flexibility in choosing the architecture they deem “best” — though it also places the responsibility of choosing (or building) those parts on the developer.

### Q32：`state` 和`props` 和有什么不一样？

**props**和**state**都是纯 JavaScript 对象。虽然它们都持有影响渲染输出的信息，但它们在组件方面的功能不同。例如，

- **props传递给**类似于函数参数的组件
- **状态**在组件内进行管理，类似于在函数中声明的变量。

Both **props** and **state** are plain JavaScript objects. While both of them hold information that influences the output of render, they are different in their functionality with respect to component. i.e,

- **Props** get passed to the component similar to function parameters
- **State** is managed within the component similar to variables declared within a function.

### Q33： **什么是Flow？**

**Flow**是一个静态类型检查器，旨在查找 JavaScript 程序中的类型错误，由 Facebook 创建。Flow类型可以表达比传统类型系统更细粒度的区别。例如，与大多数类型系统不同，Flow 可以帮助您捕获涉及 null 的错误。

**Flow** is a static type checker, designed to find type errors in JavaScript programs, created by Facebook. Flow types can express much more fine-grained distinctions than traditional type systems. For example, Flow helps you catch errors involving null, unlike most type systems.



### Q34： **如何在 ReactJS 中创建组件？**

 有两种可能的方式来创建 ReactJS 组件。

1. **function component**：这是创建 ReactJS 组件的最简单方法。它接受 props 作为 Object 并返回 ReactJS 元素。我们称其为“函数式”，因为它们是纯 JavaScript 函数。

   **Functional components:** This is the simplest way to create ReactJS components. It accepts props as an Object and returns ReactJS elements. We call it as “functional” because those are pure JavaScript functions.

   ```js
   function Greeting(props) {
      	   return <h1> Hello, {props.message}</h1> 
   	}
   ```

2. **class component：**也可以使用 Es6 类来定义组件。上面的功能组件可以写成如下，

   **Class components:** You can also use Es6 class to define component. The above functional component can be written as below,

   ```
   class Greeting extends React.Component {
     	    render() {
       		    return <h1>Hello, {this.props.message}</h1>;
     	        }
   	    }
   ```



### Q35： 回调函数作为`setState`参数的目的是什么？

回调函数被调用时`setState`完成并渲染组件。自从`setState`是**异步**回调函数用于任何发布操作。

**笔记：**建议使用生命周期方法而不是这个回调函数。

The callback function is invoked when `setState` finished and the component gets rendered. Since `setState` is **asynchronous** the callback function is used for any post action.

**Note:** It is recommended to use lifecycle method rather this callback function.

```js
setState({name: 'sudheer'}, () => console.log('The name has updated and component re-rendered'));
```



### Q36： *React 中的portals*是什么，我们什么时候需要它们？

**Portals**提供了一种一流的方式来将子级渲染到存在于父组件的 DOM 层次结构之外的 DOM 节点中。

有时将子元素插入 DOM 中的不同位置很有用：

**Portals** provide a first-class way to render children into a DOM node that exists outside the DOM hierarchy of the parent component.

Sometimes it’s useful to insert a child into a different location in the DOM:

```js
render() {
  // React does *not* create a new div. It renders the children into `domNode`.
  // `domNode` is any valid DOM node, regardless of its location in the DOM.
  return ReactDOM.createPortal(
    this.props.children,
    domNode  );
}
```



### Q37： **如何将参数传递给事件处理程序或回调？**

您可以使用箭头函数来包装事件处理程序并传递参数：

```js
<button onClick={() => this.handleClick(id)} />
```

 这相当于调用 .bind 如下，

```js
<button onClick={this.handleClick.bind(this, id)} />
```



### Q38： 在 React 组件的生命周期中会发生什么？

 在最高级别，React 组件具有分为三大类的生命周期事件：

1. 初始化
2. State/Props 更新
3. 销毁

At the highest level, React components have lifecycle events that fall into three general categories:

1. Initialization
2. State/Property Updates
3. Destruction

![q38](/Users/jerry/Desktop/面试/react面试宝典/react--interview-point/图库/q38.png) 

### Q39： Redux 中的*组件*和*容器*有什么区别？

- **组件**是 React API 的一部分。组件是描述 React UI 的一部分的类或函数。
- **容器**是连接到 redux store的 React 组件的非正式术语。容器接收 Redux 状态更新和分发actions，它们通常不渲染 DOM 元素；他们将渲染委托给展示性子组件。

- **Component** is part of the React API. A Component is a class or function that describes part of a React UI.
- **Container** is an informal term for a React component that is connected to a redux store. Containers receive Redux state updates and dispatch actions, and they usually don't render DOM elements; they delegate rendering to presentational child components.

### Q40： **什么是*内联条件表达式*？**(*inline conditional expressions*)

您可以使用 JS 提供的 if 语句或三元表达式来有条件地呈现表达式。除了这些方法之外，您还可以将任何表达式嵌入到 JSX 中，方法是将它们包裹在花括号中，然后跟 JS 逻辑运算符 (&&)。

You can use either if statements or ternary expressions which are available from JS to conditionally render expressions. Apart from these approaches, you can also embed any expressions in JSX by wrapping them in curly braces and then followed by JS logical operator(&&).

```js
if(this.state.mode === 'view') {
  return (
      <button onClick={this.handleEdit}>
        Edit
      </button>
  );
} else {
  return (
      <button onClick={this.handleSave}>
        Save
      </button>
  );
}
// or 
 {
   view
  ? null
  : (
    <p>
      <input
        onChange={this.handleChange}
        value={this.state.inputText} />
    </p>
  )
}
```



### Q41： **如何防止 React 中事件回调的默认行为?**

你调用`e.preventDefault();`传递给回调的事件 e。

You call `e.preventDefault();` on the event e passed into the callback.



### Q42： 什么是**Reconciliation**?

当组件的 props 或 state 发生变化时，React 通过比较新返回的元素和之前渲染的元素来决定是否需要进行实际的 DOM 更新。当它们不一样（变化）时，React 将更新 DOM。这个过程称为***Reconciliation***。

When a component’s props or state change, React decides whether an actual DOM update is necessary by comparing the newly returned element with the previously rendered one. When they are not equal, React will update the DOM. This process is called **reconciliation**.



### Q43： 使用带有 props 参数的`super`构造函数的目的是什么？

在调用`super()`方法之前，子类构造函数不能使用**this**引用。这同样适用于 ES6 子类。将 props 参数传递给`super()`call的主要原因是在您的子构造函数中访问`this.props`。

A child class constructor cannot make use of **this** reference until `super()` method has been called. The same applies for ES6 sub-classes as well. The main reason of passing props parameter to `super()` call is to access `this.props` in your child constructors.

 **通过 props:**

```js
class MyComponent extends React.Component {
    constructor(props) {
        super(props);
        console.log(this.props);  // Prints { name: 'sudheer',age: 30 }
    }
}
```

**不通过 props:**

```js
class MyComponent extends React.Component {
    constructor(props) {
        super();
        console.log(this.props); // Prints undefined
        // But Props parameter is still available
        console.log(props); // Prints { name: 'sudheer',age: 30 }
    }

    render() {
        // No difference outside constructor
        console.log(this.props) // Prints { name: 'sudheer',age: 30 }
    }
}
```

上面的代码片段表明 this.props 的行为仅在构造函数中有所不同。在构造函数之外也是一样的。



### Q44： 当你调用`setState`时会发生什么？

React 在被调用时要做的第一件事就是将你传入的对象合并到组件的当前状态中。这将启动一个称为**Reconciliation**的过程。协调的最终目标是以最有效的方式根据这个新状态更新 UI。`setState``setState`

为此，React 将构建一个新的 React 元素树（您可以将其视为 UI 的对象表示）。一旦有了这棵树，为了弄清楚 UI 应该如何改变以响应新状态，React 会将这棵新树与之前的元素树进行比较。

通过这样做，React 将知道发生的确切更改，并且通过确切知道发生了哪些更改，将能够通过仅在绝对必要的情况下进行更新来最小化其在 UI 上的足迹。

 

### Q45： *Element*和*Component*和有什么不一样？

**Element**是一个简单的对象，描述您希望在屏幕上显示的 DOM 节点或其他组件。元素可以在其道具中包含其他元素。创建一个 React 元素很便宜。一旦创建了一个元素，它就永远不会发生变异。React 元素的对象表示如下，

An **element** is a plain object describing what you want to appear on the screen in terms of the DOM nodes or other components. Elements can contain other elements in their props. Creating a React element is cheap. Once an element is created, it is never mutated. The object representation of React element would be as follows,

```js
const element = React.createElement(
  'div',
  {id: 'login-btn'},
  'Login'
)
```

以上作为对象返回如下，`createElement`

```js
{
  type: 'div',
  props: {
    children: 'Login',
    id: 'login-btn'
  }
}
```

最后它使用如下渲染到 DOM ，`ReactDOM.render`

```js
<div id='login-btn'>Login</div>
```

而一个**组件**可以用几种不同的方式声明。它可以是一个带有方法的类。或者，在简单的情况下，它可以定义为一个函数。无论哪种情况，它都将 props 作为输入，并返回一个元素树作为输出。JSX在最后被编译。`render()``createElement`

```js
function Button ({ onLogin }) {
  return React.createElement(
    'div',
    {id: 'login-btn', onClick: onLogin},
    'Login'
  )
}
```



### Q46： 什么是*高阶*组件？

高阶组件**(HOC)**是一个函数，它接受一个组件并返回一个新组件。基本上，这是一种源自 React 组合特性的模式。我们称它们为**“纯”组件** ，因为它们可以接受任何动态提供的子组件，但它们不会修改或复制其输入组件的任何行为。

A higher-order component **(HOC)** is a function that takes a component and returns a new component. Basically, it’s a pattern that is derived from React’s compositional nature We call them as **“pure’ components”** because they can accept any dynamically provided child component but they won’t modify or copy any behavior from their input components.

```js
const EnhancedComponent = higherOrderComponent(WrappedComponent);
```

HOC 可用于以下许多用例，

1. 代码重用、逻辑和引导抽象
2. 渲染高顶
3. 状态抽象和操作
4. 道具操作

HOC can be used for many use cases as below,

1. Code reuse, logic and bootstrap abstraction
2. Render High jacking
3. State abstraction and manipulation
4. Props manipulation



## Mid



### Q47： 为类组件命名不同的*生命周期方法*

- `componentWillMount`- 这最常用于根组件中的应用程序配置。

- `componentDidMount`- 在这里，您想要完成所有没有 DOM 就无法完成的设置，并开始获取您需要的所有数据。此外，如果你想设置 eventListeners 等，这个生命周期钩子是一个很好的地方。

- `componentWillReceiveProps`- 这个生命周期作用于特定的道具更改以触发状态转换。

- `shouldComponentUpdate`- 如果您担心浪费的渲染 是提高性能的好地方，因为它允许您在组件收到新的. 应该总是返回一个布尔值，并根据它决定组件是否被重新渲染。`shouldComponentUpdate``prop``shouldComponentUpdate`

- `componentWillUpdate`- 很少使用。它可以用来代替也具有（但无法访问以前的道具）的组件。`componentWillReceiveProps``shouldComponentUpdate`

- `componentDidUpdate`- 也常用于更新 DOM 以响应 prop 或状态更改。

- `componentWillUnmount`- 在这里您可以取消任何传出的网络请求，或删除与组件关联的所有事件侦听器。

  

- `componentWillMount`- this is most commonly used for App configuration in your root component.
- `componentDidMount` - here you want to do all the setup you couldn’t do without a DOM, and start getting all the data you need. Also if you want to set up eventListeners etc. this lifecycle hook is a good place to do that.
- `componentWillReceiveProps` - this lifecyclye acts on particular prop changes to trigger state transitions.
- `shouldComponentUpdate` - if you’re worried about wasted renders `shouldComponentUpdate` is a great place to improve performance as it allows you to prevent a rerender if component receives new `prop`. `shouldComponentUpdate` should always return a boolean and based on what this is will determine if the component is rerendered or not.
- `componentWillUpdate` - rarely used. It can be used instead of `componentWillReceiveProps` on a component that also has `shouldComponentUpdate` (but no access to previous props).
- `componentDidUpdate` - also commonly used to update the DOM in response to prop or state changes.
- `componentWillUnmount` - here you can cancel any outgoing network requests, or remove all event listeners associated with the component.

![q47](/Users/jerry/Desktop/面试/react面试宝典/react--interview-point/图库/q47.png)



### Q48： **什么是`{this.props.children}`以及何时应该使用它？**

您可以在代表“通用框”并且不提前知道其子级的组件上使用`props.children`。它用于在调用组件时显示您在开始标签和结束标签之间包含的任何内容。

You can use `props.children` on components that represent ‘generic boxes’ and that don’t know their children ahead of time. It is used to display whatever you include between the opening and closing tags when invoking a component.

```js
const Picture = (props) => {
  return (
    <div>
      <img src={props.src}/>
      {props.children}
    </div>
  )
}
```



### Q49： **什么是高阶（HOC）组件？**

*高阶组件*是一个接受一个组件并返回一个新组件的函数。HOC 允许您重用代码、逻辑和引导抽象。最常见的大概就是 Redux 的`connect`函数了。除了简单地共享实用工具库和简单的组合之外，HOC 是在 React 组件之间共享行为的最佳方式。如果你发现自己在不同的地方写了很多做同样事情的代码，你也许可以将这些代码重构为可重用的 HOC。

*A higher-order component* is a function that takes a component and returns a new component. HOC's allow you to reuse code, logic and bootstrap abstraction. The most common is probably Redux’s `connect` function. Beyond simply sharing utility libraries and simple composition, HOCs are the best way to share behavior between React Components. If you find yourself writing a lot of code in different places that does the same thing, you may be able to refactor that code into a reusable HOC.



### Q50： React中的State是什么？

 *State*类似于 props，但它是私有的，完全由组件控制。状态本质上是一个对象，它保存数据并确定组件如何渲染和发生行为。

*State* is similar to props, but it is private and fully controlled by the component. State is essentially an object that holds data and determines how the component renders and behaves.



### Q51： **Redux 中的store是什么？**

 ***store***是一个保存应用程序状态的JavaScript 对象。除此之外，它还具有以下职责：

- 允许通过`getState()`访问状态;
- 允许通过`dispatch(action)`更新状态;
- 通过`subscribe(listener)`注册监听器;
- 通过`subscribe(listener)`返回的函数处理监听器的注销。

The *store* is a JavaScript object that holds application state. Along with this it also has the following responsibilities:

- Allows access to state via `getState()`;

- Allows state to be updated via `dispatch(action)`;

- Registers listeners via `subscribe(listener)`;

- Handles unregistering of listeners via the function returned by `subscribe(listener)`.

  

### Q52： **你将如何阻止组件渲染？**

从组件的渲染方法返回`null`不会影响组件生命周期方法的触发。

Returning `null` from a component's render method does not affect the firing of the component's lifecycle methods.



### Q53： **为什么建议将回调函数传递给 setState 而不是对象？**

因为`this.props`和`this.state`可能会异步更新，所以您不应该依赖它们的值来计算下一个状态。

Because `this.props` and `this.state` may be updated asynchronously, you should not rely on their values for calculating the next state.



### Q54： **从数据数组呈现组件列表的典型模式是什么？**

使用为每个数组元素执行的箭头函数调用数组上的 map，可能为每个元素输出一个 React 组件。

Call map on an array with an arrow function that executes for each array element, possibly outputting a React component for each.



### Q55： **React 中的 PropType 是什么？**

它们帮助向 React 指示 一个React 组件的属性是和应该接受的数据类型。

They help indicate to React what data types a React component's properties are and should accept.

 

### Q56： **什么是纯组件？**

**PureComponent**与 Component 完全相同，只是它为您处理`shouldComponentUpdate`方法。当 props 或 state 发生变化时，PureComponent 将对 props 和 state 进行浅层比较。另一方面，组件不会将当前的道具和状态与开箱即用的下一个进行比较。因此，无论何时调用`shouldComponentUpdate`组件都会默认重新渲染。

**PureComponent** is exactly the same as Component except that it handles the `shouldComponentUpdate` method for you. When props or state changes, PureComponent will do a shallow comparison on both props and state. Component, on the other hand, won’t compare current props and state to next out of the box. Thus, the component will re-render by default whenever `shouldComponentUpdate` is called.



### Q57： **React 相对于 VueJS 的优势是什么？**

- 为大型应用程序开发提供了更大的灵活性；
- 更容易测试；
- 适合移动应用创建；
- 提供更多信息和解决方案

1. Gives more flexibility in large apps developing; 

2. Easier to test; 

3. Suitable for mobile apps creating; 

4. More information and solutions available

   

### Q58： 一些流行的 Flux 库

虽然 Flux 是一种通过应用程序强制执行数据流的通用模式，但存在许多可供选择的实现，例如：

- [Redux](http://redux.js.org/)：也许是当今最受欢迎的 Flux 库，
- [Alt.js](http://alt.js.org/)：另一个流行的库，用于管理 React 应用程序中的数据。

While Flux is a general pattern for enforcing data flow through an application, there exist many implementations from which to choose from, for example:

- [Redux](http://redux.js.org/): perhaps the most popular Flux library today,
- [Alt.js](http://alt.js.org/): another popular library for managing data in React applications.



### Q59： React + Redux 应用程序中典型的数据流是怎样的？

来自 UI 组件的回调调度带有有效负载的操作，然后在 reducer 中拦截该操作，可能产生新的应用程序状态，然后从 Redux 存储通过应用程序中的组件树向下传播。

Callback from UI component dispatches an action with a payload, which then is intercepted in a reducer, possibly producing a new application state, which is then propagated down through the tree of components in the application from the Redux store.



### Q60： **避免在事件回调方法中绑定到 this 的替代方法是什么？**

在事件处理程序中使用箭头函数。

Use arrow functions in your event handlers.



### Q61： 在组件的渲染方法中你不应该做的事情有哪些限制？

您不能修改组件的状态（使用`setState`），也不能与浏览器交互（在`componentDidMount`中进行）。渲染应该是一个纯函数。

You cannot modify the component's state (with `setState`), nor interact with the browser (do that in `componentDidMount`). Render should be a pure function.



### Q62： **如何在 JSX 回调中绑定方法或事件处理程序？**

 有3种可能的方式来实现，

1. **构造函数中的绑定：**在 JavaScript 类中，默认情况下不绑定方法。同样的事情也适用于定义为类方法的 ReactJS 事件处理程序。通常我们将它们绑定在构造函数中，如下所示，

   ```js
   constructor(props) {
       super(props);
       this.handleClick = this.handleClick.bind(this);
   }
   
   handleClick() {
       // Perform some logic
   }
   ```

2. **公共类字段语法：**如果您不喜欢使用绑定方法，则可以使用公共类字段语法正确绑定回调

   ```js
   handleClick = () => {
        console.log('this is:', this);
   }
   <button onClick={this.handleClick}>
        Click me
   </button>
   ```

3. **回调中的箭头函数：**您可以直接在回调中使用箭头函数，如下所示

   ```js
   <button onClick={(e) => this.handleClick(e)}>
         Click me
   </button>
   ```



### Q63： **为什么fragment比container div 更好？**

1. 通过不创建额外的 DOM 节点，片段速度更快，内存使用更少。这只对非常大和深的树有真正的好处。
2. 一些 CSS 机制，如 Flexbox 和 CSS Grid 有特殊的父子关系，中间添加 div 很难保持想要的布局。
3. DOM 检查器不那么混乱

1. Fragments bit faster and has less memory usage by without creating an extra DOM node. This only has a real benefit on very large and deep trees.
2. Some CSS mechanisms like Flexbox and CSS Grid have a special parent-child relationship, and adding divs in the middle makes it hard to keep the desired layout.
3. The DOM inspector is less cluttered



### Q64： 什么是*prop drilling*，如何避免？

在构建 React 应用程序时，通常需要一个深度嵌套的组件来使用层次结构中更高级别的另一个组件提供的数据。最简单的方法是简单地将 prop 从每个组件传递到层次结构中的下一个组件，从源组件到深度嵌套的组件。这称为**prop drilling**。

prop drilling的主要缺点是不应该知道数据的组件变得不必要地复杂并且更难维护。

为了避免prop drilling，一种常见的方法是使用 React 上下文。这允许定义提供数据的`Provider`组件，并允许嵌套组件通过`Consumer`组件或`useContext`hook使用上下文数据。

When building a React application, there is often the need for a deeply nested component to use data provided by another component that is much higher in the hierarchy. The simplest approach is to simply pass a prop from each component to the next in the hierarchy from the source component to the deeply nested component. This is called **prop drilling**.

The primary disadvantage of prop drilling is that components that should not otherwise be aware of the data become unnecessarily complicated and are harder to maintain.

To avoid prop drilling, a common approach is to use React context. This allows a `Provider` component that supplies data to be defined, and allows nested components to consume context data via either a `Consumer` component or a `useContext` hook.



### Q65： **什么是Action？**

Action是普通的 javascript 对象。它们必须具有指示正在执行的操作类型的类型。从本质上讲，操作是将数据从您的应用程序发送到您的store的信息payloads。

Actions are plain javascript objects. They must have a type indicating the type of action being performed. In essence, actions are payloads of information that send data from your application to your store.



### Q66： **shouldComponentUpdate() 方法的意义何在？**

它用于性能原因，例如，如果组件的实现者确定特定属性更改不需要重新渲染，他们可以从此方法返回 false 并跳过重新渲染。

It's used for performance reasons, for example if the implementor of a component knows for sure that a particular property change does not necessitate a re-render, they could return false from this method and skip the re-render.



### Q67： **什么是Ref 转发？**

**Ref 转发**是一项功能，它允许某些组件获取它们接收到的 ref，并将其进一步传递给子组件。

**Ref forwarding** is a feature that lets some components take a ref they receive, and pass it further down to a child.

```js
const ButtonElement = React.forwardRef((props, ref) => (
  <button ref={ref} className="CustomButton">
    {props.children}
  </button>
));

// Create ref to the DOM button:
const ref = React.createRef();
<ButtonElement ref={ref}>Forward Ref</ButtonElement>;
```



### Q68： React 中的这三个点 ( `...`) 有什么作用？

**问题**

`...`在这个 React（使用 JSX）代码中做了什么，它叫什么？

```js
<Modal {...this.props} title='Modal heading' animation={false}/>
```

**回答**

那是property传播符号。它是在 ES2018 中添加的（数组/可迭代的传播更早，ES2015）。

例如，如果 this.props 包含`a: 1`and`b: 2` ，那么

That's property spread notation. It was added in ES2018 (spread for arrays/iterables was earlier, ES2015).

For instance, if this.props contained `a: 1` and `b: 2`, then

```js
<Modal {...this.props} title='Modal heading' animation={false}>
```

将与以下内容相同：

```js
<Modal a={this.props.a} b={this.props.b} title='Modal heading' animation={false}>
```

扩展表示法不仅适用于该用例，而且适用于创建具有现有对象的大部分（或全部）属性的新对象 - 当您更新状态时会出现很多情况，因为您无法修改状态直接地：

```js
this.setState(prevState => {
    return {foo: {...prevState.foo, a: "updated"}};
});
```



### Q69： **你如何告诉 React 在生产模式下构建，它会做什么?**

通常，您会使用 Webpack 的 DefinePlugin 方法将**NODE_ENV**设置为**production**。这将删除诸如 propType 验证和额外警告之类的内容。最重要的是，缩小代码也是一个好主意，因为 React 使用 Uglify 的死代码消除功能来去除仅用于开发的代码和注释，这将大大减少包的大小。

Typically you’d use Webpack’s DefinePlugin method to set **NODE_ENV** to **production**. This will strip out things like propType validation and extra warnings. On top of that, it’s also a good idea to minify your code because React uses Uglify’s dead-code elimination to strip out development only code and comments, which will drastically reduce the size of your bundle.



### Q70： **在 Redux 中处理异步调用的典型中间件选择是什么？**

- Redux Thunk，
- Redux Promise，
- Redux Saga

 

### Q71： 

 



### Q72： 

 

### Q73： 

 

### Q74： 

 

### Q75： 

 



### Q76： 

 

### Q77： 

 

### Q78： 

 

### Q79： 

 

### Q80： 

 

### Q81： 

 

### Q82： 

 

### Q83： 

 



### Q84： 

 

### Q85： 

 

### Q86： 

 

### Q87： 

 



### Q88： 

 

### Q89： 

 

### Q90： 

 

### Q91： 

 

### Q92： 

 

### Q93： 

 

### Q94： 

 

### Q95： 

 



### Q96： 

 

### Q97： 

 

### Q98： 

 

### Q99： 

 



### Q100： 

 

### Q101： 

 

### Q102： 

 

## Senior



### Q103： 

 

### Q104： 

 

### Q105： 

 

### Q106： 

 

### Q107： 

 



### Q108： 

 

### Q109： 

 

### Q110： 

 

### Q111： 

 



### Q112： 

 

### Q113： 

 

### Q114： 

 

### Q115： 

 

### Q116： 

 

### Q117： 

 

### Q118： 

 

### Q119： 

 



### Q120： 

 

### Q121： 

 

### Q122： 

 

### Q123： 

 



### Q124： 

 

### Q125： 

 

### Q126： 

 

### Q127： 

 

### Q128： 

 

### Q129： 

 

### Q130： 

 

### Q131： 

 



### Q132： 

 

### Q133： 

 

### Q134： 

 

### Q135： 

 



### Q136： 

 

### Q137： 

 

### Q138： 

 

### Q139： 

 

### Q140： 

 

### Q141： 

 

### Q142： 

 

### Q143： 

 



### Q144： 

 

### Q145： 

 

### Q146： 

 

### Q147： 

 



### Q148： 

 

### Q149： 

 

### Q150： 