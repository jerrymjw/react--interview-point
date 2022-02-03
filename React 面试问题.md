## 一般 React – React 面试问题
###	1.区分真实DOM和虚拟DOM

| **真实 DOM**                | **虚拟 DOM**                  |
| ------------------------------------- | ----------------------------- |
| 1、更新慢。                           | 1、更新速度更快。             |
| 2.可以直接更新HTML。                  | 2.不能直接更新HTML。          |
| 3. 如果元素更新，则创建一个新的 DOM。 | 3. 如果元素更新，则更新 JSX。 |
| 4. DOM 操作非常昂贵。                 | 4. DOM 操作非常容易。         |
| `5.过多的内存浪费。                   | 5.没有内存浪费。              |

| **Real DOM**                              | **Virtual  DOM**                        |
| ----------------------------------------- | --------------------------------------- |
| 1. It updates  slow.                      | 1. It updates  faster.                  |
| 2. Can directly  update HTML.             | 2. Can’t directly  update HTML.         |
| 3. Creates a new  DOM if element updates. | 3. Updates the  JSX if element updates. |
| 4. DOM  manipulation is very expensive.   | 4. DOM  manipulation is very easy.      |
| 5. Too much of  memory wastage.           | 5. No memory  wastage.                  |

###	2.什么是React？

- React     是     Facebook 于     2011 年开发的前端     JavaScript 库。
- 它遵循基于组件的方法，有助于构建可重用的     UI 组件。
- 它用于开发复杂的交互式     Web 和移动     UI。
- 尽管它仅在     2015 年才开源，但它拥有支持它的最大社区之一。

- React is a front-end JavaScript library     developed by Facebook in 2011.

- It follows the component-based     approach which helps in building reusable UI components.

- It is used for     developing complex and interactive web and mobile UI.

- Even though it was open     sourced only in 2015, it has one of the largest communities supporting it.

###	3. React 有什么特点？
React 的主要特点如下：
i.	它使用虚拟DOM而不是真实DOM。
ii.	它使用服务器端渲染。
iii.	它遵循单向数据流或数据绑定。
Major features of React are listed below:
i.	It uses the virtual DOM instead of the real DOM.
ii.	It uses server-side rendering.
iii.	It follows uni-directional data flow or data binding.
###	4. 列出 React 的一些主要优点。
React 的一些主要优点是：
i.	它提高了应用程序的性能
ii.	它可以方便地在客户端和服务器端使用
iii.	因为 JSX，代码的可读性增加了
iv.	React 很容易与 Meteor、Angular 等其他框架集成
v.	使用 React，编写 UI 测试用例变得非常容易
i.	It increases the application’s performance
ii.	It can be conveniently used on the client as well as server side
iii.	Because of JSX, code’s readability increases
iv.	React is easy to integrate with other frameworks like Meteor, Angular, etc
v.	Using React, writing UI test cases become extremely easy

###	**5**. React 的**局限性**是什么？

React 的限制如下：

1. React     只是一个库，而不是一个成熟的框架
2. 它的库很大，需要时间去理解
3. 对于新手程序员来说理解起来可能有点困难
4. 编码变得复杂，因为它使用内联模板和     JSX

1. React     is just a library, not a full-blown framework
2. Its library is very     large and takes time to understand
3. It can be little     difficult for the novice programmers to understand
4. Coding gets complex as     it uses inline templating and JSX

### 6.什么是JSX？

JSX 是 JavaScript XML 的简写。这是 React 使用的一种文件类型，它利用 JavaScript 的表现力以及类似 HTML 的模板语法。这使得 HTML 文件非常容易理解。该文件使应用程序健壮并提高其性能。下面是一个 JSX 的例子：

**JSX** is a shorthand for JavaScript XML. This is a type of file used by React which utilizes the expressiveness of JavaScript along with HTML like template syntax. This makes the HTML file really easy to understand. This file makes applications robust and boosts its performance. Below is an example of JSX:

![image-20220204001136527](/Users/jerry/Library/Application Support/typora-user-images/image-20220204001136527.png)

###	**7.** **Virtual DOM** **你是怎么理解的？解释其如何工作。**

虚拟 DOM 是一个轻量级的 JavaScript 对象，它最初只是真实 DOM 的副本。它是一个节点树，将元素、它们的属性和内容列为对象及其属性。React 的渲染函数从 React 组件中创建一个节点树。然后，它更新此树以响应由用户或系统执行的各种操作引起的数据模型中的突变。这个虚拟 DOM 通过三个简单的步骤工作。 

A virtual DOM is a lightweight JavaScript object which originally is just a copy of the real DOM. It is a node tree that lists the elements, their attributes and content as Objects and their properties. React’s render function creates a node tree out of the React components. It then updates this tree in response to the mutations in the data model which is caused by various actions done by the user or by the system. This Virtual DOM works in three simple steps.

1. 每当任何底层数据发生变化时，整个 UI 都会以 Virtual DOM 表示形式重新呈现。![虚拟 DOM 1 - 什么是 ReactJS？ - 埃杜里卡](file:////Users/jerry/Library/Group%20Containers/UBF8T346G9.Office/TemporaryItems/msohtmlclip/clip_image001.png)

2. 然后计算前一个 DOM 表示和新的表示之间的差异。![Virtual DOM 2 - React 面试问题 - Edureka](file:////Users/jerry/Library/Group%20Containers/UBF8T346G9.Office/TemporaryItems/msohtmlclip/clip_image002.png)

3. 一旦计算完成，真实的 DOM 将只更新实际发生变化的内容。 ![Virtual DOM 3 - React 面试问题 - Edureka](file:////Users/jerry/Library/Group%20Containers/UBF8T346G9.Office/TemporaryItems/msohtmlclip/clip_image003.png)

###	8. 为什么浏览器不能读取 JSX?

浏览器只能读取 JavaScript 对象，但不能读取常规 JavaScript 对象中的 JSX。因此，为了让浏览器能够读取 JSX，首先，我们需要使用 Babel 等 JSX 转换器将 JSX 文件转换为 JavaScript 对象，然后将其传递给浏览器。

Browsers can only read JavaScript objects but JSX in not a regular JavaScript object. Thus to enable a browser to read JSX, first, we need to transform JSX file into a JavaScript object using JSX transformers like Babel and then pass it to the browser

 

### **9.** **与** **ES5** **相比，****React** **的** **ES6** **语法有何不同？**

从 ES5 到 ES6 的语法在以下几个方面发生了变化：

 i.   require vs **import**

![image-20220204002446123](/Users/jerry/Library/Application Support/typora-user-images/image-20220204002446123.png)

ii.	export vs exports

![image-20220204002616715](/Users/jerry/Library/Application Support/typora-user-images/image-20220204002616715.png)
iii.	component and function

![image-20220204002727539](/Users/jerry/Library/Application Support/typora-user-images/image-20220204002727539.png)

iv.	Props



![image-20220204002839411](/Users/jerry/Library/Application Support/typora-user-images/image-20220204002839411.png)

v.	State

![image-20220204002853767](/Users/jerry/Library/Application Support/typora-user-images/image-20220204002853767.png)


### **10. React** **与** **Angular** **有何不同？**

| **Topic**       | **React**     | **Angular**    |
| --------------- | ------------- | -------------- |
| *1.* *架构*     | 只有MVC的观点 | 完整的MVC      |
| *2.* *渲染*     | 服务器端渲染  | 客户端渲染     |
| *3.DOM*         | 使用虚拟 DOM  | 使用真实的 DOM |
| *4.* *数据绑定* | 单向数据绑定  | 双向数据绑定   |
| *5.* *调试*     | 编译时调试    | 运行时调试     |
| *6.* *作者*     | Facebook      | 谷歌           |

##	**React** **组件** **——React** **面试问题**

### 11. 解释“在 React 中，一切都是组件。” 。

组件是 React 应用程序 UI 的构建块。这些组件将整个 UI 分割成小的独立且可重用的部分。然后它将这些组件中的每一个呈现为彼此独立，而不会影响 UI 的其余部分。

Components are the building blocks of a React application’s UI. These components split up the entire UI into small independent and reusable pieces. Then it renders each of these components independent of each other without affecting the rest of the UI.

### 12. React中render()的作用是什么。

每个 React 组件都必须强制有一个render() 。它返回一个单一的 React 元素，它是原生 DOM 组件的表示。如果需要渲染多个 HTML 元素，则必须将它们组合在一个封闭标记中，例如<form>、<group>、<div>等。此函数必须保持纯正，即它必须返回相同的结果每次调用它。

Each React component must have a render() mandatorily. It returns a single React element which is the representation of the native DOM component. If more than one HTML element needs to be rendered, then they must be grouped together inside one enclosing tag such as <form>, <group>, <div> etc. This function must be kept pure i.e., it must return the same result each time it is invoked.

### **13.** **如何将两个或多个组件嵌入到一个组件中？**

![image-20220204002936865](/Users/jerry/Library/Application Support/typora-user-images/image-20220204002936865.png)

### 14.什么是Props?

Props 是 React 中properties的简写。它们是只读组件，必须保持纯净，即不可变。在整个应用程序中，它们总是从父组件传递到子组件。子组件永远不能将道具发送回父组件。这有助于维护单向数据流，通常用于呈现动态生成的数据。

Props is the shorthand for Properties in React. They are read-only components which must be kept pure i.e. immutable. They are always passed down from the parent to the child components throughout the application. A child component can never send a prop back to the parent component. This help in maintaining the unidirectional data flow and are generally used to render the dynamically generated data.

 

### **15. React** **中的状态是什么，它是如何使用的？**

状态是 React 组件的核心。状态是数据的来源，必须尽可能简单。基本上，状态是决定组件渲染和行为的对象。与道具不同，它们是可变的，并创建动态和交互式组件。它们通过 this.state()访问。

 

States are the heart of React components. States are the source of data and must be kept as simple as possible. Basically, states are the objects which determine components rendering and behavior. They are mutable unlike the props and create dynamic and interactive components. They are accessed via **this.state().**

 

### 16. 区分state和Props。

| **条件**               | **State** | **Props** |
| ---------------------- | --------- | --------- |
| 1.从父组件接收初始值   | 是的      | 是的      |
| 2.父组件可以改变值     | 不        | 是的      |
| 3.在组件内部设置默认值 | 是的      | 是的      |
| 4.改变内部组件         | 是的      | 不        |
| 5.为子组件设置初始值   | 是的      | 是的      |
| 6.改变内部子组件       | 不        | 是的      |



| **Conditions**                                 | **State** | **Props** |
| ---------------------------------------------- | --------- | --------- |
| 1. Receive initial value from parent component | Yes       | Yes       |
| 2. Parent component can change value           | No        | Yes       |
| 3. Set default values inside component         | Yes       | Yes       |
| 4. Changes inside component                    | Yes       | No        |
| 5. Set initial value for child components      | Yes       | Yes       |
| 6. Changes inside child components             | No        | Yes       |

### 17. 如何更新组件的状态？

可以使用 this.setState() 更新组件的状态。

![image-20220204003405303](/Users/jerry/Library/Application Support/typora-user-images/image-20220204003405303.png)

### 18. React 中的箭头函数是什么？它是如何使用的？

**箭头函数**是用于编写函数表达式的更简短的语法。它们也被称为*“**胖箭头*”（**=>**）函数。这些函数允许正确绑定组件的上下文，因为在 ES6 中默认情况下自动绑定不可用。箭头函数在使用高阶函数时最有用。

**Arrow functions** are more of brief syntax for writing the function expression. They are also called *‘fat arrow*‘ (**=>**) the functions. These functions allow to bind the context of the components properly since in ES6 auto binding is not available by default. Arrow functions are mostly useful while working with the higher order functions.

![image-20220204003501961](/Users/jerry/Library/Application Support/typora-user-images/image-20220204003501961.png)

### 19. 区分有状态和无状态组件。

| **有状态的组件**                                             | **无状态组件**                                              |
| ------------------------------------------------------------ | ----------------------------------------------------------- |
| 1.  在内存中存储有关组件状态变化的信息                       | 1.计算组件的内部状态                                        |
| 2.有权改变状态                                               | 2.无权改变状态                                              |
| 3.  包含过去、现在和未来可能的状态变化的知识                 | 3.  不包含过去、当前和可能的未来状态变化的知识              |
| 4.无状态组件通知他们状态变化的需求，然后他们将props发送给他们。 | 4.  他们从  Stateful 组件中接收 props，并将其视为回调函数。 |

| **Stateful Component**                                       | **Stateless  Component**                                     |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| 1. Stores info about component’s state change in memory      | 1. Calculates the internal state of the components           |
| 2. Have authority to change state                            | 2. Do not have the authority to change state                 |
| 3. Contains the knowledge of past, current and possible future  changes in state | 3. Contains no knowledge of past, current and possible future  state changes |
| 4. Stateless components notify them about the requirement  of the state change, then they send down the props to them. | 4. They receive the props from the Stateful components  and treat them as callback functions. |

### **20. React** **组件生命周期的不同阶段是什么？**

React 组件的生命周期分为三个不同的阶段：

1. ***初始渲染阶段****：* 这是组件即将开始其生命旅程并进入     DOM 的阶段。
2. ***更新阶段****：* 一旦组件被添加到     DOM，它可能只有在     prop 或状态发生更改时才可能更新和重新渲染。这只发生在这个阶段。
3. ***卸载阶段****：*这是组件生命周期的最后阶段，在此阶段 组件被销毁并从     DOM 中移除。

 

1. ***Initial Rendering Phase\****:* This     is the phase when the component is about to start its life journey and     make its way to the DOM.
2. ***Updating Phase\****:* Once     the component gets added to the DOM, it can potentially update and     re-render only when a prop or state change occurs. That happens only in     this phase.
3. ***Unmounting Phase\****:* This     is the final phase of a component’s life cycle in which the component     is destroyed and removed from the DOM.

 

### 21. 详细讲解React组件的生命周期方法。

一些最重要的生命周期方法是：

1. ***componentWillMount ()*** – 在客户端和服务器端进行渲染之前执行。

2. ***componentDidMount ()*** – 仅在第一次渲染后在客户端执行。

3. ***componentWillReceiveProps ()*** -     一旦从父类接收到道具并且在调用另一个渲染之前调用。

4. ***shouldComponentUpdate ()*** – 根据特定条件返回     true 或     false 值。如果您希望您的组件更新，请返回**true**否则返回**false**。默认情况下，它返回     false。

5. ***componentWillUpdate ()*** –     在     DOM 中进行渲染之前调用。

6. ***componentDidUpdate ()*** – 渲染发生后立即调用。

7. ***componentWillUnmount ()*** –     在组件从     DOM 中卸载后调用。它用于清理内存空间。

   

8. ***componentWillMount()\*** – Executed     just before rendering takes place both on the client as well as     server-side.

9. ***componentDidMount()\*** – Executed     on the client side only after the first render.

10. ***componentWillReceiveProps()\*** –     Invoked as soon as the props are received from the parent class and before     another render is called.

11. ***shouldComponentUpdate()\*** – Returns true     or false value based on certain conditions. If you want your component to     update, return **true** else return **false**. By     default, it returns false.

12. ***componentWillUpdate()\*** –     Called just before rendering takes place in the DOM.

13. ***componentDidUpdate()\*** – Called     immediately after rendering takes place.

7. ***componentWillUnmount()\*** –     Called after the component is unmounted from the DOM. It is used to clear     up the memory spaces.

### **22. React** **中的事件是什么？**

在 React 中，事件是对特定动作（如鼠标悬停、鼠标单击、按键等）的触发反应。处理这些事件类似于处理 DOM 元素中的事件。但是有一些语法差异，例如：

1. 事件使用驼峰式命名，而不是仅使用小写。
2. 事件作为函数而不是字符串传递。

event 参数包含一组特定于事件的属性。每个事件类型都包含自己的属性和行为，只能通过其事件处理程序访问。

In React, events are the triggered reactions to specific actions like mouse hover, mouse click, key press, etc. Handling these events are similar to handling events in DOM elements. But there are some syntactical differences like:

1. Events are named using camel     case instead of just using the lowercase.
2. Events are passed as functions     instead of strings.

The event argument contains a set of properties, which are specific to an event. Each event type contains its own properties and behavior which can be accessed via its event handler only.

### 23. 如何在 React 中创建事件？

![image-20220204003807328](/Users/jerry/Library/Application Support/typora-user-images/image-20220204003807328.png)

### **24. React** **中的合成事件是什么？**

合成事件是充当浏览器原生事件的跨浏览器包装器的对象。它们将不同浏览器的行为组合到一个 API 中。这样做是为了确保事件在不同浏览器中显示一致的属性。

Synthetic events are the objects which act as a cross-browser wrapper around the browser’s native event. They combine the behavior of different browsers into one API. This is done to make sure that the events show consistent properties across different browsers.

### **25.** **你对** **React** **中的** **refs** **有什么理解？**

Refs 是 React 中引用的简写。它是一个属性，有助于存储对特定 React 元素或组件的引用，该引用将由组件渲染配置函数返回。它用于返回对 render() 返回的特定元素或组件的引用。当我们需要 DOM 测量或向组件添加方法时，它们会派上用场。

Refs is the short hand for References in React. It is an attribute which helps to store a reference to a particular React element or component, which will be returned by the components render configuration function. It is used to return references to a particular element or component returned by render(). They come in handy when we need DOM measurements or to add methods to the components.

![image-20220204003835734](/Users/jerry/Library/Application Support/typora-user-images/image-20220204003835734.png)

### **26.** **列出一些你应该使用** **Refs** **的情况。**

以下是应该使用 refs 的情况：

- 当您需要管理焦点时，选择文本或媒体播放
- 触发命令式动画
- 与第三方DOM库集成

Following are the cases when refs should be used:

- When you need to manage focus, select text or media playback
- To trigger imperative animations
- Integrate with third-party DOM libraries

### 27. React中的表单是如何创建的？

React 表单类似于 HTML 表单。但是在 React 中，状态包含在组件的 state 属性中，并且只能通过 setState() 进行更新。因此元素不能直接更新它们的状态，它们的提交由 JavaScript 函数处理。此函数对用户输入表单的数据具有完全访问权限。

React forms are similar to HTML forms. But in React, the state is contained in the state property of the component and is only updated via setState(). Thus the elements can’t directly update their state and their submission is handled by a JavaScript function. This function has full access to the data that is entered by the user into a form.

### **28.** **如何在** **React** **中模块化代码？**

我们可以使用导出和导入属性来模块化代码。它们有助于在不同的文件中分别编写组件。

![image-20220204004014481](/Users/jerry/Library/Application Support/typora-user-images/image-20220204004014481.png)

![image-20220204004024350](/Users/jerry/Library/Application Support/typora-user-images/image-20220204004024350.png)

### 29. 你对受控和不受控的组件了解多少？

| **受控组件**                                                 | **不受控制的组件**                            |      |
| ------------------------------------------------------------ | --------------------------------------------- | ---- |
| 1.他们不维护自己的状态                                       | 1.他们保持自己的状态                          |      |
| 2.数据由父组件控制                                           | 2.数据由DOM控制                               |      |
| 3. 他们通过 props 获取当前值，然后通过回调通知更改           | 3. Refs 用于获取它们的当前值                  |      |
| **Controlled  Components**                                   | **Uncontrolled  Components**                  |      |
| 1. They do not maintain their own state                      | 1. They maintain their own state              |      |
| 2. Data is controlled by the parent  component               | 2. Data is controlled by the DOM              |      |
| 3. They take in the current values  through props and then notify the changes via callbacks | 3. Refs are used to get their current  values |      |
|                                                              |                                               |      |

 

## React 面试问题

### 30. 什么是高阶组件（HOC）？

高阶组件是重用组件逻辑的一种高级方式。基本上，它是一种源自 React 组合特性的模式。HOC 是自定义组件，其中包含另一个组件。他们可以接受任何动态提供的子组件，但不会修改或复制其输入组件的任何行为。您可以说 HOC 是“纯”组件。

Higher Order Component is an advanced way of reusing the component logic. Basically, it’s a pattern that is derived from React’s compositional nature. HOC are custom components which wrap another component within it. They can accept any dynamically provided child component but they won’t modify or copy any behavior from their input components. You can say that HOC are ‘pure’ components.



### **31.** **你可以用** **HOC** **做什么？**

HOC 可用于许多任务，例如：

- 代码重用、逻辑和引导抽象
- 渲染高顶
- 状态抽象和操作
- 道具操作

HOC can be used for many tasks like:

- Code reuse, logic and bootstrap     abstraction
- Render High jacking
- State abstraction and     manipulation
- Props manipulation



### 32. 什么是纯成分？

**纯** 组件是可以编写的最简单、最快的组件。它们可以替换任何只有 render()的组件。这些组件增强了代码的简单性和应用程序的性能。

*Pure* components are the simplest and fastest components which can be written. They can replace any component which only has a **render().** These components enhance the simplicity of the code and performance of the application.



### 33. React中keys的意义是什么？

键用于识别唯一的虚拟 DOM 元素及其驱动 UI 的相应数据。它们通过回收 DOM 中的所有现有元素来帮助 React 优化渲染。这些键必须是唯一的数字或字符串，React 使用它只是重新排序元素而不是重新渲染它们。这会提高应用程序的性能。

Keys are used for identifying unique Virtual DOM Elements with their corresponding data driving the UI. They help React to optimize the rendering by recycling all the existing elements in the DOM. These keys must be a unique number or string, using which React just reorders the elements instead of re-rendering them. This leads to increase in application’s performance.

 

 

 

## React Redux – React 面试问题

### 34. MVC框架的主要问题是什么？

以下是 MVC 框架的一些主要问题：

- DOM 操作非常昂贵
- 应用程序缓慢且效率低下
- 有巨大的内存浪费
- 由于循环依赖，围绕模型和视图创建了一个复杂的模型

Following are some of the major problems with MVC framework:

- DOM manipulation was very     expensive
- Applications were slow and     inefficient
- There was huge memory wastage
- Because of circular     dependencies, a complicated model was created around models and views

### 35. 解释Flux。

Flux 是一种强制单向数据流的架构模式。它控制派生数据，并使用对所有数据具有权限的中央存储实现多个组件之间的通信。整个应用程序中的任何数据更新都必须仅在此处发生。Flux 为应用程序提供稳定性并减少运行时错误。

Flux is an architectural pattern which enforces the uni-directional data flow. It controls derived data and enables communication between multiple components using a central Store which has authority for all data. Any update in data throughout the application must occur here only. Flux provides stability to the application and reduces run-time errors.



### 36. 什么是 Redux？

Redux 是当今市场上最流行的前端开发库之一。它是 JavaScript 应用程序的可预测状态容器，用于整个应用程序的状态管理。使用 Redux 开发的应用程序易于测试，并且可以在显示一致行为的不同环境中运行。

Redux is one of the most trending libraries for front-end development in today’s marketplace. It is a predictable state container for JavaScript applications and is used for the entire applications state management. Applications developed with Redux are easy to test and can run in different environments showing consistent behavior.



### **37. Redux** **遵循的三个原则是什么？**

1. ***单一事实来源：\***整个应用程序的状态存储在单个存储中的对象/状态树中。单一状态树可以更轻松地跟踪随时间的变化以及调试或检查应用程序。
2. ***状态是只读的：*** 改变状态的唯一方法是触发一个动作。操作是描述更改的普通     JS 对象。就像状态是数据的最小表示一样，动作是对该数据更改的最小表示。 
3. ***使用纯函数进行更改：\*** 为了指定状态树如何通过操作进行转换，您需要纯函数。纯函数是那些返回值仅取决于其参数值的函数。
4. ***Single source of truth:\*** The state of     the entire application is stored in an object/ state tree within a     single store. The single state tree makes it easier to keep     track of changes over time and debug or inspect the application.
5. ***State is     read-only:\*** The only way to change the state is to     trigger an action. An action is a plain JS object describing the     change. Just like state is the minimal representation of data, the action     is the minimal representation of the change to that data. 
6. ***Changes are     made with pure functions:\*** In order to specify how     the state tree is transformed by actions, you need pure functions. Pure     functions are those whose return value depends solely on the values     of their arguments.




### 38. 您对“单一事实来源”的理解是什么？

Redux 使用“Store”将应用程序的整个状态存储在一个地方。因此，所有组件的状态都存储在 Store 中，并且它们从 Store 本身接收更新。单一状态树可以更轻松地跟踪随时间的变化以及调试或检查应用程序。

Redux uses ‘Store’ for storing the application’s entire state at one place. So all the component’s state are stored in the Store and they receive updates from the Store itself. The single state tree makes it easier to keep track of changes over time and debug or inspect the application.



### **39.** **列出** **Redux** **的组件。**

Redux 由以下组件组成：

1. **动作**——它是一个描述发生了什么的对象。
2. **Reducer** –     这是一个确定状态将如何变化的地方。
3. **Store** –     整个应用程序的状态/对象树保存在     Store 中。
4. **查看**-     仅显示商店提供的数据。

Redux is composed of the following components:

1. **Action** –     It’s an object that describes what happened.
2. **Reducer** –     It is a place to determine how the state will change.
3. **Store** –     State/ Object tree of the entire application is saved in the Store.
4. **View** –     Simply displays the data provided by the Store.

###  40. 展示数据流如何通过 Redux？

qdfsfdsfd



### **41. Redux** **中的** **Actions** **是如何定义的？**

React 中的 Action 必须有一个 type 属性来指示正在执行的 ACTION 的类型。它们必须定义为字符串常量，您也可以向其添加更多属性。在 Redux 中，动作是使用称为动作创建者的函数创建的。以下是 Action 和 Action Creator 的示例：

Actions in React must have a type property that indicates the type of ACTION being performed. They must be defined as a String constant and you can add more properties to it as well. In Redux, actions are created using the functions called Action Creators. Below is an example of Action and Action Creator:

![image-20220204005222470](/Users/jerry/Library/Application Support/typora-user-images/image-20220204005222470.png)

### 42.解释Reducer的作用。

Reducers 是纯函数，它指定应用程序的状态如何响应 ACTION 变化。Reducers 通过接受先前的状态和动作来工作，然后返回一个新的状态。它根据操作的类型确定需要进行哪种更新，然后返回新值。 如果不需要做任何工作，它会按原样返回先前的状态。

Reducers are pure functions which specify how the application’s state changes in response to an ACTION. Reducers work by taking in the previous state and action, and then it returns a new state. It determines what sort of update needs to be done based on the type of the action, and then returns new values. It returns the previous state as it is, if no work needs to be done.

 

### 43. Store在Redux中有什么意义？

store 是一个 JavaScript 对象，它可以保存应用程序的状态并提供一些辅助方法来访问状态、调度操作和注册侦听器。应用程序的整个状态/对象树保存在单个存储中。因此，Redux 非常简单且可预测。我们可以将中间件传递给 store 来处理数据，并记录更改 store 状态的各种操作。所有的动作都通过 reducer 返回一个新的状态。

A store is a JavaScript object which can hold the application’s state and provide a few helper methods to access the state, dispatch actions and register listeners. The entire state/ object tree of an application is saved in a single store. As a result of this, Redux is very simple and predictable. We can pass middleware to the store to handle the processing of data as well as to keep a log of various actions that change the state of stores. All the actions return a new state via reducers.

### **44. Redux** **和** **Flux** **有什么不同？**

| **Flux**                   | **还原**                  |
| -------------------------- | ------------------------- |
| 1. Store包含状态和变化逻辑 | 1.存储和更改逻辑是分开的  |
| 2.有多家店铺               | 2.只有一家店              |
| 3.所有店铺都断网平仓       | 3. 具有分层减速器的单存储 |
| 4. 有单例调度员            | 4.没有dispatcher的概念    |
| 5. React 组件订阅 store    | 5.容器组件利用connect     |
| 6. 状态是可变的            | 6. 状态是不可变的         |

 

| **Flux**                                     | **Redux**                                  |
| -------------------------------------------- | ------------------------------------------ |
| 1. The Store contains state and change logic | 1. Store and change logic are separate     |
| 2. There are multiple stores                 | 2. There is only one store                 |
| 3. All the stores are disconnected and flat  | 3. Single store with hierarchical reducers |
| 4. Has singleton dispatcher                  | 4. No concept of dispatcher                |
| 5. React components subscribe to the store   | 5. Container components utilize connect    |
| 6. State is mutable                          | 6. State is immutable                      |

 

## React 面试问题

### 45. Redux有什么优势？

Redux 的优点如下：

- **结果的可预测性****——** 由于总是有一个事实来源，即存储，因此不会混淆如何将当前状态与动作和应用程序的其他部分同步。
- **可维护性****——**代码变得更容易维护，具有可预测的结果和严格的结构。
- **服务器端渲染****——** 您只需要将在服务器上创建的商店传递给客户端。这对于初始渲染非常有用，并在优化应用程序性能时提供更好的用户体验。
- **开发人员工具****——**从操作到状态更改，开发人员可以实时跟踪应用程序中发生的一切。
- **社区和生态系统** ——Redux     背后有一个庞大的社区，这使得它的使用更具吸引力。一个由人才组成的大型社区为图书馆的改进做出了贡献，并利用它开发了各种应用程序。
- **易于测试** ——Redux     的代码主要是小型、纯净和隔离的函数。这使得代码可测试且独立。
- **组织** ——Redux     对代码的组织方式非常精确，这使得团队使用它时代码更加一致和容易。
- **Predictability     of outcome –** Since there is always one source of     truth, i.e. the store, there is no confusion about how to sync the current     state with actions and other parts of the application.
- **Maintainability     –** The code becomes easier to maintain with a     predictable outcome and strict structure.
- **Server-side     rendering –** You just need to pass the store created on     the server, to the client side. This is very useful for initial     render and provides a better user experience as it optimizes the     application performance.
- **Developer     tools –** From actions to state changes,     developers can track everything going on in the application in real time.
- **Community and     ecosystem –** Redux has a huge community behind it     which makes it even more captivating to use. A large community of talented     individuals contribute to the betterment of the library and develop     various applications with it.
- **Ease of     testing –** Redux’s code is mostly functions which     are small, pure and isolated. This makes the code testable and     independent.
- **Organization     –** Redux is precise about how code should be     organized, this makes the code more consistent and easier when a team     works with it.



## React 路由器– React 面试问题

### **46.** **什么是** **React** **路由器？**

React Router 是一个建立在 React 之上的强大的路由库，它有助于向应用程序添加新的屏幕和流程。这使 URL 与网页上显示的数据保持同步。它维护标准化的结构和行为，用于开发单页 Web 应用程序。React Router 有一个简单的 API。

React Router is a powerful routing library built on top of React, which helps in adding new screens and flows to the application. This keeps the URL in sync with data that’s being displayed on the web page. It maintains a standardized structure and behavior and is used for developing single page web applications. React Router has a simple API.



### 47. 为什么 在 React Router v4 中使用switch 关键字？

虽然**<div>**用于封装Router内部的多个路由。当您只想在多个定义的路由中显示要呈现的单个路由时，使用 “switch”关键字 。 **<switch>**标记在使用时将键入的 URL 与定义的路由按顺序匹配。 当找到第一个匹配项时，它会呈现指定的路由。从而绕过剩余的 路线。

Although a **<div>** is used to encapsulate multiple routes inside the Router. The ‘switch’ keyword is used when you want to display only a single route to be rendered amongst the several defined routes. The **<switch>** tag when in use matches the typed URL with the defined routes in sequential order. When the first match is found, it renders the specified route. Thereby bypassing the remaining routes.



### **48.** **为什么我们需要** **React** **中的路由器？**

路由器用于定义多个路由，当用户键入特定 URL 时，如果此 URL 与路由器内部定义的任何“路由”的路径匹配，则用户将被重定向到该特定路由。所以基本上，我们需要在我们的应用程序中添加一个路由器库，它允许创建多个路由，每个路由都指向我们一个独特的视图。

A Router is used to define multiple routes and when a user types a specific URL, if this URL matches the path of any ‘route’ defined inside the router, then the user is redirected to that particular route. So basically, we need to add a Router library to our app that allows creating multiple routes with each leading to us a unique view.

![image-20220204005147889](/Users/jerry/Library/Application Support/typora-user-images/image-20220204005147889.png)



### **49.** **列出** **React Router** **的优点。**

几个优点是：

1. 就像     React 如何基于组件一样，在     React Router v4 中，API     是*“All About Components”*。路由器可以可视化为单个根组件（**<BrowserRouter>**），我们在其中包含特定的子路由（**<route>**）。
2. 无需手动设置     History 值：在     React Router v4 中，我们需要做的就是将路由包装在**<BrowserRouter>**组件中。
3. 这些包被拆分：三个包，一个用于     Web、Native     和     Core。这支持我们应用程序的紧凑尺寸。基于类似的编码风格很容易切换。
4. Just     like how React is based on components, in React Router v4, the API     is *‘All About Components’*. A Router can be visualized as a     single root component (**<BrowserRouter>**) in which we enclose     the specific child routes (**<route>**).
5. No need to manually set History     value: In React Router v4, all we need to do is wrap our routes     within the **<BrowserRouter>** component.
6. The packages are split: Three     packages one each for Web, Native and Core. This supports the compact size     of our application. It is easy to switch over based on a similar coding     style.



### **50. React Router** **与传统路由有何不同？**

| **话题**       | **常规路由**                                 | **反应路由**                       |
| -------------- | -------------------------------------------- | ---------------------------------- |
| **涉及的页数** | 每个视图对应一个新文件                       | 仅涉及单个 HTML 页面               |
| **网址更改**   | 向服务器发送 HTTP 请求并接收相应的 HTML 页面 | 仅更改历史属性                     |
| **感觉**       | 用户实际上为每个视图浏览不同的页面           | 用户被欺骗认为他正在浏览不同的页面 |

 

| **Topic**          | **Conventional Routing**                                     | **React Routing**                                            |
| ------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| **PAGES INVOLVED** | Each view corresponds to a new file                          | Only single HTML page is involved                            |
| **URL CHANGES**    | A HTTP request is sent to a server and corresponding HTML page  is received | Only the History attribute is changed                        |
| **FEEL**           | User actually navigates across different pages for each view | User is duped thinking he is navigating across different pages |

 
