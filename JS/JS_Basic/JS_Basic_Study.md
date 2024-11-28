### JS常识

------

#### 一、书写位置

+ 内部JavaScript

  直接写在html文件中，使用script标签包裹起来

  注：将script放在HTML文件的底部附近的原因是浏览器会按照代码在文件中的顺序加载HTML，如果先加载的JS希望修改其下方的HTMl，那么它可能会由于HTML尚未加载而失效。

+ 引入外部js文件

  在body中通过script标签引入

  ```html
  <body>
      <script src="某某.js"></script>
  </body>
  ```



#### 二、变量、常量与数组

+ ES6须知

  > 在ES6（ECMAScript 6）中，变量的声明方式发生了显著的变化，主要引入了`let`和`const`两种新的关键字，并对原有的`var`关键字的行为进行了补充和明确。以下是ES6中变量声明的主要变化：
  >
  > ### 一、`let`关键字的引入
  >
  > 1. **块级作用域**：使用`let`声明的变量具有块级作用域，只在其所在的代码块（如函数体、循环体、条件语句块等）内有效。这意味着在块外部无法访问块内部使用`let`声明的变量。
  > 2. **不存在变量提升**：与`var`不同，`let`声明的变量不会被提升到其作用域的顶部。因此，在变量声明之前访问该变量会抛出错误，这称为暂时性死区（Temporal Dead Zone，TDZ）。
  > 3. **不允许重复声明**：在同一作用域内，不允许使用`let`重复声明同一个变量。
  >
  > ### 二、`const`关键字的引入
  >
  > 1. **块级作用域**：与`let`类似，`const`声明的变量也具有块级作用域。
  > 2. **必须赋值**：使用`const`声明变量时，必须同时为其赋值。一旦赋值后，变量的值就不能再被重新赋值（对于基本数据类型而言）。但如果`const`声明的是一个对象或数组，虽然其内存地址不能被改变，但对象或数组的内容是可以修改的。
  > 3. **不存在变量提升**：与`let`一样，`const`声明的变量也不会被提升到其作用域的顶部，存在暂时性死区。
  > 4. **不允许重复声明**：在同一作用域内，不允许使用`const`重复声明同一个变量。
  >
  > ### 三、`var`关键字的行为明确
  >
  > 1. **函数作用域与全局作用域**：在ES6之前，使用`var`声明的变量在函数内部具有函数作用域（也称为局部作用域），在函数外部具有全局作用域。此外，`var`声明的变量存在变量提升现象，即变量可以在声明之前被访问（但值为`undefined`）。
  > 2. **重复声明不报错**：在ES6之前，使用`var`可以在同一作用域内重复声明同一个变量，而不会引发错误。但在ES6中，由于`let`和`const`的引入，这种做法被视为不良实践。

+ 变量声明

  ```js
  // 赋值
  let age = 18
  // 修改
  age = 20
  ```

+ 常量

  当某个变量永远不会改变时，就可以使用const来声明；常量不允许重新赋值，故声明时必须赋值

+ 数组的声明、赋值与使用

  ```js
  // 声明与赋值
  let arr = ['小刚','小红','小明','小丽']
  // 数组的使用
  console.log(arr[0])
  // 数组length属性
  console.log(arr.length)  // 4
  ```

  

#### 三、数据类型

+ 数字类型（number）：数据类型在运算错误时，会打印NaN表示运算不符合逻辑且NaN的任何操作都会返回NaN，例如：除0，类型不匹配

  > console.log('你好'+2)       NaN
  >
  > console.log(NaN + 2)      NaN

+ 字符串类型

  + 字符串拼接：使用+运算符，可以实现字符串之间的连接

  + 模板字符串：对于使用反引号``包括起来的字符串中${变量名}相当于C语言中的占位符

    > let  age  =  18
    >
    > 在字符串声明时，可以直接使用``将字符串括起来，该字符串可以直接加入${变量名}做替换

+ boolean类型：有固定的值为true与false两个，且在其他类型做强制转换时，也有对应的真或假

  + ‘’（空串）、0、undefined、null、false、NaN转换为boolean后都是false，其余皆为true

+ undefined类型：只声明变量，不对变量进行赋值，变量默认为undefined，在开发过程中经常声明一个变量，等待传送过来的数据，当需要判断一个数据是否有值，可以通过检测该变量是否为undefined，就可以判断用户是否有数据传送过来

+ null：官方解释null为尚未创建的对象，简言之为将来有一个变量存放的为一个对象，但对象还没创建好，值为null

+ 类型检测：typeof  变量名，可以检测一个变量的类型

#### 四、类型转换

+ 隐式转换

  +号两边只要有一个是字符串，都会把另一个转换为字符串，除了加号以外的算术运算符都会将数据转换为数字类型，若不能转换为数字类型做运算会输出NaN

+ 强制转换

  ```js
  let str = "123"
  // 转换为数字型，后两种类型的用法请使用时自行查询
  let num = Number(str)  
  let num = parseInt(str)  
  let num = parseFloat(str) 
  ```

+ 运算符优先级

  小括号 > 一元运算符(++,--,!) > 算术运算符 > 关系运算符(>,>=,<,<=) > 相等运算符(==,!=,全等,不全等) > 逻辑



#### 五、分支与循环

+ 分类

  + 分支：if分支、if-else分支、if-else if-else分支、switch分支语句
  + 三元运算符：与java三目运算符用法一样
  + 循环：while循环、for循环
  + 退出循环：break与continue

+ while循环

  ```js
  let i = 1
  while(i<3){
      document.write("循环")
      i++
  }
  ```

+ for循环

  ```js
  for(let i = 0; i < 3; i++){
      
  }
  
  // 遍历数组
  let arr = ["张三","李四","王五","赵六"]
  for(let i = 0; i < arr.length; i++){
      console.log(arr[i])
  }
  ```

  

#### 六、数组操作

```js
// 1. 数组修改
arr[0] = "你好"

// 2. 数组新增
arr.push(新增内容)   // 向数组末尾添加数据，并返回数组新长度
arr.unshift(新增内容) // 向数组开头添加元素，并返回数组长度

// 3. 删除数组中数据
arr.pop()   // 删除数组中最后一个元素，并返回该元素的值
arr.shift   // 删除第一个元素
```



### 函数与对象

------

#### 一、函数基本使用

+ 函数的声明与使用

  ```js
  function 函数名(){
      函数体
  }
  // 调用函数
  函数名()
  ```

+ 函数参数、默认参数与返回值

  ```js
  function add(a,b){
      return a+b
  }
  
  // 默认参数,若调用时不传参数，则使用默认参数
  function add(a=1,b=2){
      return a+b
  }
  
  let sum = add(5,10)
  ```

  

#### 二、匿名函数

+ 函数表达式-匿名函数

  将匿名函数赋值给一个变量，并且通过变量名称进行调用，将这个称为函数表达式；函数表达式只能先声明后调用，而具名函数可以在文件的任意位置声明，任意位置调用

  ```js
  let fn = function(){
      // 函数体
  }
  // 调用
  fn()
  ```

  

+ 函数立即执行-匿名函数

  ```js
  // 该函数会在页面加载时立即执行，不需要调用，匿名函数立即执行通常是为了防止全局变量污染
  // 当使用其他js文件时，若对方的文件过于巨大，会导致某些在其文件内部使用过的命名无法使用，立即执行函数可以解决
  (function(){
      // 函数体
  })()
  ```



------

#### 三、对象的基本使用

+ 对象的声明与使用

  对象的声明需要使用{}，使用属性通过变量名.属性

  ```js
  let obj = {
      name:'pink',
      age:18,
      gender:'女',
      // 对象方法，以及方法的使用
      print:function(){
          console.log(`${name}+${age}+${gender}`)
      }
  }
  // 使用
  console.log(obj.name)
  
  // 对象打印
  console.dir(obj)
  ```
  
+ 对象属性的增删改查

  + 查的两种方式
    + 通过对象.属性名的方式获取属性值
    + 通过对象["属性名"]获取属性值
  + 改：obj.property = 新值
  + 增：对象名.新属性 = 新值

+ 对象遍历（for-in遍历细节）

  遍历索引：for（let k in arr）在数组遍历过程中k为字符类型的下标，对象遍历的过程k为对象的属性名（字符型）

  ```js
  // 数组遍历
  let arr = [1,2,3,4,5,6]
  for(let i = 0; i < arr.length; i++){
      console.log(arr[i])
  }
  
  // 对象遍历
  let obj = {
      name:"zhangsan",
      age:18,
      gender:"女"
  }
  for(let k in obj){
      console.log(obj[k])
  }
  ```

+ math数学内置对象(使用过程中查询具体参数)

  random：生成0-1之间的随机数（含0不含1）

  ceil/floor：向上/向下取整

  max/min：找最大/最小数

  pow：幂运算

  abs：绝对值



#### 四、引用数据类型

+ 定义区别

  基本数据类型在存储时变量中存储的是值本身，因此叫做值类型

  引用数据类型在存储时变量中存储的仅仅是地址（引用），因此叫做引用数据类型，通过new关键字创建的对象（系统对象、自定义对象），如object，Array，Date

+ 分配空间

  + 栈：由操作系统自动分配释放存放函数的参数值、局部变量的值等，其操作方式类似于数据结构中的栈；基本数据类型存放在栈中
  + 堆：存放引用类型，一般由程序员分配释放，若程序员不释放，则由垃圾回收机制回收，引用类型是通过地址来找到对象的，当变量通过=号赋值时，两个变量会指向同一个对象，任何一方修改都会引起数据变化





### API阶段

------

#### 一、DOM与BOM

+ DOM（Document Object Model——文档对象模型）

  > DOM时用来呈现以及与任意HTML或XML文档交互的API，简言之，DOM时浏览器提供的一套专门用来操作网页内容额功能，DOM的作用为开发网页内容特效和实现用户交互

+ const优先

  在日常开发中，请使用const声明变量，当发现需要修改时，再将其修改为let

#### 二、获取DOM元素

+ 主要方式（CSS选择器）

  ```js
  // 1. 选择匹配的第一个元素
  const firstElement = document.querySelector('CSS选择器')
  // 2. 选择匹配的所有元素，并以类似数组列表的方式返回，该列表只能通过for循环遍历或者，没有pop与push方法
  const elementList = document.quertSelectorAll('CSS选择器')
  ```

+ 通过DOM树获取节点

  ```js
  // 可以通过当前节点获取其父节点，子节点以及兄弟节点
  const son = document.querySelector('.son')
  console.log(son)
  // 父节点
  console.log(son.parentNode)
  // 子节点
  console.log(son.children)
  // 兄弟节点
  console.log(son.nextElementSibling)  // 弟弟节点
  console.log(son.previousElementSibling) // 哥哥节点
  ```
  
+ 新增节点

  ```js
// 创建一个新的元素节点
  const 元素 = document.createElement('标签名')
  // 设置新增节点的位置
  父元素.appendChild(元素)  // 插入至父元素的最后一个子元素后
父元素.insertBefore(要插入的元素，在哪个元素前面)  //插入至指定子元素前
  ```

+ 节点克隆与删除节点

  ```js
  // 删除指定元素
  父元素.removeChild(要删除的元素)
  ```
  
  
  
+ 其他方式（不重要）

  + 通过ID获取元素getElementById()

    ```js
    const elem = document.getElementById('id')
    ```

  + 通过类名获取元素getElementsByClassName()

    ```js
    // 由于一个类型会对应多个html元素，该方法会返回一个数组对象，用于存放所有类名为给定值的html元素
    let elements = document.getElementsByClassName('myClassName')
    ```
    
    

#### 三、操作元素内容

+ 操作元素内容

  + innerText属性：获取标签文本 （不包含标签本身，只有标签内容）
  + innerHTML属性：获取标签整体（含内容与标签本身），且在重新赋值

+ 修改元素常见属性

  通过选择器获取HTML元素后，形成的是一个 DOM对象，通过对象直接.来访问其对应的属性
  
  ```js
  const img = document.querySelector('img')
  img.src = '路径'
  ```
  
+ 修改元素常见CSS样式

  + 通过style修改样式（样式请用引号括起来）

    ```js
    const box = document.querySelector('.box')
    box.style.backgroundColor = 'pink'
    ```

  + 通过调整类名className修改样式（常用于修改样式过多）

    ```js
    const box = document.querySelector('.box')
    // 这种方式会覆盖掉之前的类型，在开发中并不常用，了解即可
    box.className = 'pink'
    
    // 通过classList操作类控制CSS，可以追加与删除类名
    const box = document.querySelector('.box')
    // 类名追加，类名并不需要加.仅需要类名即可
    box.classList.add('类名')
    // 类名删除
    box.classList.remove('类名')
    // 类名切换，若已经存在类名，则删除，不存在就追加
    box.classList.toggle('类名')
    ```

+ 获取表单元素内容

  对于输入类表单，在前后端传递过程中是通过name=值  来传递的，因此获取输入类表单内容需要通过 .value属性获取，不能使用innerHTML

  而对于勾选框（单选，复选），默认勾选是通过加入checked属性，但仅只有一个单词无法设置值，可以通过元素.checked = false或true来选择是否勾选

+ H5自定义属性

  + 区别

    标准属性：标签天生自带的属性，比如class，id，title等，可以通过使用点语法操作

    自定义属性：在h5推出了专门以data-属性  来添加自定义属性，在标签上一律以data-  开头，在DOM对象上需要通过  元素.dataset.自定义属性   设置对应属性



#### 四、间歇函数

+ 定时器-间歇函数的开关

  ```js
  // 间歇函数的开启，第一个参数为间隔函数，第二个参数为间隔时间
  // 在此处的函数通过使用匿名函数，且通过es6的箭头函数指定，间隔时间的单位为ms
  let n = setInterval(function(){
      console.log('一秒执行一次')
  },1000)
  
  // 间隔函数的关闭：间歇函数拥有返回值 唯一确定的id值，用于指向该定时器，在关闭时需要通过返回值关闭
  clearInterval(n)
  ```



### 事件

------

#### 一、事件监听

+ 事件监听语法与分类

  > 事件监听三要素：1. 事件源：也就是元素对象，用于指定那个对象需要监听该事件
  >
  > ​							   2.事件类型：js中有许多事件类型，click（点击），mouseover（鼠标悬浮）等等
  >
  > ​							   3.函数：即当事件发生时需要执行的操作
  >
  > 元素对象.addEventListener('事件类型',要执行的函数)

+ 事件对象event

  + 什么是事件对象

    在JavaScript中，事件对象（Event Object）是一个由浏览器在事件发生时自动创建的对象，它包含了事件的所有相关信息，比如事件类型、触发事件的元素、鼠标位置、键盘状态等。这些信息对于开发者来说非常重要，因为它们可以用来判断事件的上下文，从而决定如何响应事件。

  + 事件对象获取

    ```js
    button.addEventListener('click', function(event) {
      // event 就是事件对象
      console.log(event);
    });
    ```

  + 事件对象属性

    + type：返回事件的类型，如click，mouseover，keydown等
    + target：触发事件的元素（事件的目标节点），在事件冒泡阶段，target始终指向触发事件的元素
    + currentTarget：事件绑定的元素，随着事件流的冒泡，current的值会指向当前元素
    + preventDefault（）方法调用的结果会存储在defaultPrevented属性中
    + stopPropagation（）方法调用的结果会影响isPropageationStopped属性
    + timeStamp：事件发生的时间戳（以毫秒为单位，从1970年1月1日00:00:00 UTC开始计算）
    + bubbles：一个布尔值，表示事件是否冒泡
    + cancelable：一个布尔值，表示事件是否可以取消其默认行为
    + preventDefault()：取消事件的默认行为（如果事件是可以取消的）。
    + stopPropagation()：阻止事件冒泡到父元素。
    + stopImmediatePropagation()：不仅阻止事件冒泡，还阻止当前元素上其他事件监听器的执行。

+ 事件类型

  + 鼠标类型
    + click：当用户点击一个元素时触发
    + dbclick：双击时触发
    + mouseover：当鼠标指针移动至元素上时触发
    + mouseout：当鼠标指针从元素上移开时触发
    + mousemove：当鼠标在元素身上移动时触发
    + mouseenter：在鼠标光标从元素外部移动到元素范围内时触发（不冒泡）
    + mouseleave：元素上方的光标移动至元素范围之外时触发（不冒泡）
  + 键盘事件
  + 表单事件
    + submit：当表单提交时触发
    + reset：当表单重置时触发
    + change：当用于该表域的内容时触发，常用于表单沿着
    + input：输入事件
  + 焦点事件
    + focus：当元素获取焦点时触发（不冒泡）
    + blur：当元素失去焦点时触发（不冒泡）
    + focusin：在元素或其子元素获得焦点时触发（冒泡）
    + focusout：在元素或其子元素失去焦点时触发（冒泡）
  + UI事件
    + load：当页面或某个资源（如图像）完全加载时触发
    + unload：当用户离开页面时触发
    + resize：当窗口或框架被调整尺寸时触发
    + scroll：当文档被滚动时触发

+ 事件冒泡

  事件冒泡是指当某个元素上的事件被触发时，该事件会沿着DOM树向上传播，依次触发父级元素上相同类型的事件处理程序。这个过程就像气泡从水底逐渐向上升一样，因此得名“冒泡”。事件冒泡的传递过程是从最具体的目标元素开始，逐级向上传递到最不具体的元素，通常时document对象

  在时间冒泡过程中，所有绑定在这些父级元素上相同类型的事件处理程序都会依次被触发，这种机制常用于简化代码，比如通过事件委托，可以在父元素上管理所有子元素的事件处理，从而减少事件绑定的数量，提升性能

  阻止事件冒泡可以在事件函数将事件本身传入，内部通过e.stopPropagation()阻止冒泡



#### 二、事件进阶知识

+ 环境对象

  指的是函数内部特殊的变量this，它代表当前函数运行时所处的环境，弄清楚this的指向是及其重要的。

  this的指向与Java大致类似：

  1. 全局上下文中（通常指的是整体环境浏览器、node.js等），浏览器指向的是window，node.js指向global
  2. js文件内的普通函数在非严格模式下指向window，严格模式下指向undefined
  3. 构造函数：当一个正常的函数是通过let instance = new 函数名() 的方式调用，它会被看做为构造函数，this指向创建的对象，即instance
  4. 箭头函数：箭头函数没有自己的this，会通过捕获上下文中的this来当做自己的this，如在调用定时器时，若使用箭头函数来当做计时器的执行函数，在执行函数内部调用this指向的是计时器的this
  5. 显式绑定：在js中可以通过一些方法改变this的指向
  6. 事件处理函数：在事件处理函数中，this指向的是触发事件的元素，若事件处理函数使用箭头函数，其指向的是上文中的this
  7. 对象方法调用：若是通过对象.方法（）,在方法执行过程中this指向的是调用方法的对象



#### 三、事件流

+ 事件流、事件捕获、事件冒泡

  事件流是指当用户在网页上执行某些操作（如点击、输入、鼠标移动等）时，会触发相应的事件，这些事件会在DOM树中按照特定的顺序传播和处理。事件流包括事件捕获阶段、目标阶段和事件冒泡阶段。

  **事件的传播顺序是固定的：先捕获后冒泡。但可以通过`addEventListener`方法的第三个参数来控制事件处理函数的触发顺序（设置为`true`表示在捕获阶段触发，设置为`false`或省略表示在冒泡阶段触发）。**

  事件捕获是指当事件触发时，会从document对象或windows对象等祖先节点，根据DOM树依次向下传播，且在传播过程中事件的第三个参数为true的函数为捕获阶段函数，这些函数会依次触发。事件会途经每一个祖先元素，直到达到触发事件的具体目标

  目标阶段：当事件到达目标元素后，对应函数会被执行

  冒泡阶段：事件从目标元素开始向上冒泡，沿着相反的路径传播到文档的根节点，在冒泡阶段可以使用event.target属性获取触发事件的元素，从而在一个事件处理函数中处理来自不同子元素的事件。

  **事件的传播是可以通过event.stopPropagation()阻止的**，无论冒泡还是捕获，被阻止后都会停止

  

+ 事件解绑

  + 使用removeEventListener

    请注意，通过匿名函数绑定事件是不能解绑事件的

    ```js
    // 添加事件监听器
    const button = document.getElementById('myButton');
    function handleClick() {
        console.log('Button clicked!');
    }
    button.addEventListener('click', handleClick);
    
    // 移除事件监听器
    button.removeEventListener('click', handleClick);
    ```

  + 一次性事件监听

    ```js
    button.addEventListener('click', handleClick, { once: true });
    // 这个监听器将在第一次点击后被自动移除
    ```



+ 事件委托

  + 事件委托定义与好处

    事件委托（Event Delegation）是JavaScript中一种重要且高效的事件处理机制。其核心思想是将事件监听器绑定到父元素上，而不是直接绑定到目标元素上。

    + 提升性能、简化代码
    + 支持动态元素：即使是页面加载后动态添加的元素，也可以通过事件委托（事件代理）触发父元素的监听器

    ```css
    <!-- 若想实现点击某个li使其变色，在不适用代理的情况下，需要为每一个元素添加点击事件 -->
    <ul class="list">
    	<li>1</li>
    	<li>2</li>
    	<li>3</li>
    </ul>
    <script>
    	const ul = document.querySelectorAll('#list')   // 获取list元素
        ul.addEventListener('click',function(event){
    		const target = event.target
            target.classList.toggle('change')
        })
    	
    </script>
    ```




#### 四、页面事件

+ 页面加载事件（load）

  等待页面所有资源加载完毕，就回去执行回调函数，且是通过window添加事件监听

  ```js
  // 页面所有资源加载完毕，该回调函数才会执行
  window.addEventListener('load',function(){
      
  })
  ```

  

+ DOMContentLoaded加载

  当初始的HTML文档被完全加载和解析完成后，DOMContentLoaded事件被触发，无需等待样式表、图像等完全加载

  ```js
  document.addEventListener('DOMContentLoaded',function(){
      
  })
  ```

  

+ 页面滚动事件 scroll

  网页需要检测用户把页面滚动到某个区域后做一些处理，比如固定导航栏，比如返回顶部

  ```js
  window.addEventListener('scroll',function(){
      // 获取html的写法
      document.documentElement
  })
  
  div.addEventListener('scroll',function(){
      // 可以通过scrollTop获取滚动时被隐藏的高度
      div.scrollTop
  })
  ```

+ 页面尺寸事件

  会在窗口尺寸改变的时候触发事件(请回忆媒体查询)，可以获取元素的可见部分宽高（不包含边框、margin、滚动条），即仅为页面的  内边距与内容区

  clientWidth与clientHeight不包含外边距 与边框的 宽高

  offsetWidth与offsetHeight 包含边框的宽高

  offsetLeft与offsetTop获取距离自己定位父级元素的左上距离

  ```js
  window.addEventListener('resize',function(){
      
  })
  ```

+ 日期对象Date

  + 实例化

    ```js
    // 得到当前时间
    const date = new Date()
    console.log(date)
    
    // 指定时间
    const currentDate = new Date('2022-5-1 08:30:00')
    console.log(currentDate)
    ```

  + Date对象相关方法

    ```js
    const date = new Date()
    //在JavaScript中，Date 对象提供了一个名为 toLocaleString() 的方法，该方法用于根据本地时间惯例将日期和时间转换为字符串。这个方法非常有用，因为它能够考虑用户的地区设置和时区，从而生成一个对用户友好的日期时间字符串。
    // 使用默认的区域设置
    console.log(date.toLocaleString());
    // 获取四位数年份
    console.log(date.getFullYear())
    // 获取月份 取值为0-11，使用应+1
    console.log(date.getMonth())
    // 获取星期 取值0-6,使用时+1
    console.log(date.getDay)
    // 获取小时
    console.log(date.getHours())
    // 获取分钟
    console.log(date.getMinutes())
    // 获取秒
    console.log(date.getSeconds())
    ```

  + 时间戳

    ```js
    // 时间戳获取的三种方式
    const date = new Date()
    console.log(date.getTime())
    
    console.log(+new Date())
    // 这种方式只能获取当前时间戳，前两种可以获取指定时间时间戳
    console.log(Date.now())
    
    // 根据时间戳制作倒计时
    ```

    

+ 移动端事件

  + touchstart：手指触摸到一个DOM元素时触发
  + touchmove：手指在一个DOM元素上滑动时触发
  + touchend：手指从一个DOM元素上移开时触发

+ 移动端swiper插件

  自己去看  https://www.swiper.com.cn/





### BOM模型

------

#### 一、BOM相关对象

![image-20241126183937239](C:\Users\27120\AppData\Roaming\Typora\typora-user-images\image-20241126183937239.png)

+ 延迟函数setTimeout

  ```js
  // 定时器，每隔一秒调用一次函数
  setInterval(function(){
      
  },1000)
  // 延时函数，等待多少秒后，仅调用一次函数
  let timer = setTimeout(function(){
      // 十秒后执行该函数
  },10000)
  // 移除延时函数
  clearTimeout(timer)
  ```

   



#### 二、location对象

+ href地址属性

  location对象拆分保存了URL地址的各个组成部分

  ```js
  // location是默认对象，每个页面可以直接使用与document属于同级对象，都是window下子元素
  console.log(location)
  // location.href存储的是当前页面的网址，href属性也可以自行赋值，实现页面跳转
  location.href = 'www.baidu.com'
  ```

+ search属性

  ```js
  // 对于网址为www.baidu.com?user=pink&pwd=123456
  console.log(location.search)   // 打印的是?user=pink&pwd=123456
  ```

+ hash属性

  ```js
  // 对于单页面应用，在跳转时不会刷新整个页面，而是仅修改某个区域的内容，此时网址会出现路由信息
  // www.baidu.com#/friend 类似这种情况
  console.log(location.hash)      // 打印#/friend
  ```



#### 三、navigator对象

+ userAgent属性

  navigator对象记录了浏览器自身的相关信息

  ```js
  // 可以让页面跳转至移动端页面
  (function(){
      const userAgent = navigator.userAgent
      // 验证是否为Android或iPhone
      const android = userAgent.match(/(Android);?[\s\/]+([\d.]+)?/)
      const iPhone = userAgent.match(/(iPhone\sOS)\s([\d_]+)/)
      
      if(android || iPhone){
          location.href = 'http://m.itcast.cn'
      }
  })()
  ```

  

#### 四、history对象

+ back()与forward()方法

  history对象主要管理历史记录，该对象与浏览器地址栏的操作相对应，如前进、后退、历史记录等

  ```js
  const back = document.querySelector('button:first-child')
  const forward = back.nextElementSibling
  back.addEventListener('click',function(){
      history.back()
  })
  forward.addEventListener('click',function(){
      history.forward()
  })
  // 前进或后退num步
  history.go(num)
  ```



#### 五、本地存储

+ 本地存储的概念

  本地存储（Local Storage）是Web应用中的一种数据存储机制，它允许网站在用户的浏览器中存储数据，并且这些数据可以跨会话（session）持久保存。这意味着，即使关闭了浏览器，重新打开后，之前存储的数据仍然可以被访问。本地存储是HTML5 Web存储API的一部分，与早期的Cookies相比，它提供了更大的存储空间（通常为5MB或更多），并且存储的数据类型更加灵活（可以存储字符串、对象等）。

  **本地存储在当前页面的信息，当页面跳转后，可以在其他页面获取。具体来说，使用localStorage存储数据后，这些数据可以在同一来源下的任何页面被访问，这意味只要页面属于同一网站，就可以在其他页面通过localStorage的API访问之前存储的数据，需要注意的是虽然本地存储提供了遍历的数据存储方式，但也存在一些限制和注意事项，例如，存储的数据量有限，并且存储的数据可以被任何访问该页面的js代码读取，因此不应存储敏感信息。此外对于大量数据的读写操作，本地存储的性能可能会受到影响。**

  

+ 本地存储-localStorage

  本地存储只能存储字符串类型，无论在存放时使用什么类型，在存储在本地后都会被转换为字符串，localStorage会永久存在本地，除非手动删除，但sessionStorage当浏览器窗口关闭后就会消失

  ```js
  // 存储数据 localStorage.setItem('key','value')  如果key已经存在就是该，不存在则为增
  localStorage.setItem('uname','pink')
  // 获取数据 localStorage.getItem(key)
  localStorage.getItem('uname')
  // 删除数据 localStorage.removeItem(key)
  localStorage.removeItem('uname')
  ```

+ 本地存储-sessionStorage

  生命周期为关闭浏览器窗口，在同一个窗口下数据可以共享，以键值对的形式存储使用，用于与localStorage类似

  ```js
  
  ```

+ 存储复杂数据类型使用JSON.stringify(复杂数据类型)

  由于本地存储要求值必须为字符串类型，因此在存储复杂数据类型或对象类型时，需要将其进行JSON序列化转为字符串后进行存储

  ```js
  const obj = {
      name:'pink',
      age:18,
      gender:'女'
  }
  // 在存储obj时需要先转换格式
  localStorage.setItem('obj',JSON.stringify(obj))
  // 获取时由于获取回来的是一段JSON序列化字符串，将其转换为对象需要反序列化
  JSON.parse(localStorage.getItem('obj'))
  ```



#### 六、数组

+ map迭代数组

  `map` 方法用于创建一个新数组，其结果是该数组中的每个元素都调用一个提供的函数后返回的结果。`map` 方法不会改变原始数组。

  > array.map(callback(currentValue, index, array), thisArg)
  >
  > - callback：为数组中每个元素执行的函数，该函数接收三个参数：
  >   - `currentValue`：数组中正在处理的当前元素。
  >   - `index`（可选）：数组中正在处理的当前元素的索引。
  >   - `array`（可选）：调用 `map` 方法的数组。
  > - `thisArg`（可选）：执行 `callback` 函数时 `this` 的值。

  ```js
  const arr = ['red','blue','green']
  // arr中每个元素都会调用map中的回调函数，且不改变元素在数组中的位置，不会更改原始数组
  const newArr = arr.map(function(currentValue,index){
      return currentValue + '颜色'
  })
  ```

  

+ join拼接数组

  `join` 方法用于将数组的所有元素连接成一个字符串。元素之间可以通过指定的分隔符进行分隔。如果不指定分隔符，则默认使用逗号 `,` 作为分隔符。

  ```js
  const fruits = ['Apple', 'Banana', 'Cherry'];
  // 参数为字符串
  const fruitString = fruits.join(' and ');
  ```
















### JS进阶

------

#### 一、作用域与作用域链

+ 局部作用域与全局作用域

  局部作用域仅可以在定义它们的函数或块级作用域内部访问，这些变量和函数在外部是不可见的

  局部作用域是es6提出的概念，（var声明的变量不会产生块级作用域，可以在块外部使用）

  

+ 作用域链

  作用域链的本质是底层的变量查找机制，在函数被执行时，会优先在当前函数作用域中查找变量，如果当前作用域查找不到则会依次逐级查找父级作用域直到全局作用域

  嵌套关系的作用域串联起来形成了作用域链，相同作用域链中按照从小到大的规则查找变量，子作用域可以访问父作用域，但父作用域无法访问子作用域

+ 垃圾回收机制

  全局变量除非页面关闭，否则基本不会被回收，但局部变量当其所在的块级作用域中的代码执行完毕后，该局部变量就会被回收。

  内存泄漏：程序分配的内存因为某个原因程序未释放或无法释放  叫做内存泄漏

  + JS垃圾回收机制算法拓展-引用计数法

    引用计数法定义内存不再使用，就是看一个对象是否有指向它的引用，没有引用了就回收对象，减少引用是通过将变量赋值为null或其他值，当所有指向该对象的变量全部赋值为null或其他值时也就是该对象没有指向它的引用了，就可以被回收，一般为以下情况

    + 跟踪记录被引用的次数
    + 如果被引用了一次，则+1
    + 如果减少一个引用--
    + 当引用为0时，就该回收了

    引用计数法存在一个致命缺点：嵌套引用，如果两个对象相互引用，尽管它们不再使用，垃圾回收不会进行回收

  + 标记清除法

    标记清除法将'不再使用的对象'定义为'无法达到的对象'，就是从根部（全局对象）出发定时扫描内存中的对象。凡是能从根部到达的对象，都是还需要使用的。那些无法由根部无法触及到的对象被标记为不再使用，稍后进行回收



#### 二、闭包（非常重要）

假设将函数称为盒子，闭包就是指在一个大盒子中存在一些变量，我们可以通过return返回一些操作这些变量的函数，当调用外层函数时会返回一个对象，对象中具有操作大盒子变量的方法。

当然也可以在大盒子中创建许多方法，通过return 返回，可以借助返回对象.方法的形式使用这些方法，通过这些方法操作原大盒子中的一些属性，因此我个人给闭包一个定义，若一个函数的返回值提供了一个或多个可以访问当前函数变量的方法，那么我们可以通过调用大函数拿到返回值的方式，即使大函数已经执行完毕，由于返回值中存在了许多操作函数中变量的方法，因此我们依旧可以对该变量进行访问

```js
function createCalculator(initialValue) {
  let value = initialValue; // 闭包记住的变量

  return {
    increment: function() { // 一个闭包函数，执行增加操作
      value++;
      return value;
    },
    decrement: function() { // 另一个闭包函数，执行减少操作
      value--;
      return value;
    },
    multiplyBy: function(factor) { // 一个带参数的闭包函数，执行乘法操作
      value *= factor;
      return value;
    },
    getValue: function() { // 一个返回当前值的闭包函数
      return value;
    }
  };
}

const calc = createCalculator(10); // 创建一个计算器实例
console.log(calc.getValue()); // 输出 10
console.log(calc.increment()); // 输出 11
console.log(calc.multiplyBy(2)); // 输出 22
console.log(calc.decrement()); // 输出 21
```

+ var变量提升

  在执行时会将var声明的变量提升至当前作用域的最前面，只提升声明，不提升赋值

  ```js
  // 相当于var num放在了打印前，但没有赋值
  console.log(num+'件')   // 输出undefined
  var num = 10
  ```



#### 三、函数进阶

+ 函数提升：与变量提升类似，是指函数在声明之前即可被调用，会把所有函数声明提升至当前作用域最前面

  ```js
  fn()  // 不会报错
  function fn(){
      console.log('函数提升')
  }
  
  fun()     // 报错，var声明函数表达式，会将var fun的声明放在最前面，但未赋值不是函数，不能调用
  var fun = function(){
      
  }
  ```

+ 函数参数---动态参数arguments

  arguments是函数内部内置的伪数组变量，它包含了调用函数时传入的所有实参

  ```js
  // 不设置参数，在函数内部有动态参数伪数组
  function getSum(){
      console.log(arguments)  // [1,2,3]
      let sum
      for(let i = 0; i < arguments.length; i++){
          sum += arguments[i]
      }
  }
  
  getSum(1,2,3)
  ```

+ 函数参数---剩余参数

  当函数采用剩余参数时，是允许给定形参的，当实参个数大于形参个数时，会将多出来的参数给到剩余参数数组中

  ```js
  function getSum(a,b,...arr){
      // 此时a=1，b=2，arr=[3,4,5,6]
  }
  getSum(1,2,3,4,5,6)
  ```

+ 展开运算符

  ```js
  // 展开运算符可以将一个数组在输出时展开
  const arr = [1,2,3,4,5]
  console.log(...arr)  // 1 2 3 4 5 
  
  
  // 典型运用场景：求数组最大值（最小值）、合并数组等
  let max = Math.max(...arr)
  const arr1 = [1,2,3,4,5]
  const arr2 = [10,12,34,57,20]
  const arr = [...arr1,...arr2]
  ```

+ 箭头函数

  匿名函数中没有arguments，但可以使用匿名函数

  ```js
  // 初始写法
  const fn = (a,b,c)=>{
      // 代码
  }
  // 若只有一个参数，可以省略小括号
  const fn = a => {
      // 代码
  }
  // 若函数只有一行
  const fn = a => console.log(a)
  
  // 若函数只有一个返回值,后边那一行当返回值
  const fn = x => x+x
  
  // 返回值可以为对象
  const fn = name = ({userName:name})
  ```

+ 箭头函数的this



#### 四、解构赋值ES6语法

+ 数组解构

  + 基本结构

    ```js
    // 一对一赋值,以下会将对应的值赋值给对应的变量
    let arr = [1,2,3,4]
    let [a,b,c,d] = arr
    ```

  + 跳过元素

    ```js
    // 在基本结构的基础上，将某个元素在声明时空出，即可跳过该元素的赋值
    let [a,,c,d] = [1,2,3,4] // 此时a为1，c为3，d为4
    ```

  + 设置默认值

    ```js
    // 在元素声明时直接给定默认值，当给定位置对应的赋值数组中没有对应的值时会使用默认值
    let [a,b=10,c] = [1,2,3] // 与基本结构相同b会被赋值为2
    
    // 没有给定值
    let [a,b=10] = [1]  // b的值为2
    
    // 若声明数组的长度大于赋值数组的长度，且超出部分没有给定默认值，会被设置为undefined
    let [a,b=10,c,d] = [1,2]  // b的值为2，c、d全为undefined
    ```

  + 嵌套解构

    ```js
    // 解构可以通过嵌套的模式解构多维数组,就是保证两边结构相同，对应位置有值就赋值，没值默认，最后undefined
    let [a,[b,c],d] = [1,[2,3],4]  
    ```

  + 邪门写法

    ```js
    // 剩余元素写法
    let [a,...rest] = [1,2,3,4]   // a=1,rest=[2,3,4]
    ```

  + 最终用法

    ```js
    function method([a,b,c]){
        
    }
    method([1,2,3])  // a=1,b=2,c=3
    
    function method([a,b=10,c,...rest]){}
    method([1,,3,4,5,6])    // 1 10 3 [4, 5, 6]
    ```

+ 对象解构---与数组解构基本类似

  ```js
  // 对应同名对象解构
  let {name,age} = {name:'pink',age:18}
  let {name} = {}
  // 对应非同名解构,userName='pink',UserAge=18
  let {name:userName,age:userAge} = {name:'pink',age:18}
  
  // 默认解构，有值替换，没值默认
  let {name:userName,age:userAge,gender:userGender='男'} = {name:'pink',age:18}  // gender为男
  let {name:userName,age:userAge,gender:userGender='男'} = {name:'pink',age:18,gender='女'}
  
  // 解构赋值与函数参数
  function greet({ name, age }) {
      console.log(`Hello, my name is ${name} and I am ${age} years old.`);
  }
  let person = {
      name: 'Alice',
      age: 25
  }
  greet(person)
  ```



#### 五、加强for循环

```js
// forEach方法,第一个参数为当前元素必选，第二个可选
数组.forEach(function (当前数组元素，当前元素索引号){
    // 函数体
})
let arr = [1,2,3,4,5,6]
arr.forEach(function(item,index){
    console.log(item)
    console.log(index)
})
```



#### 六、创建对象的三种方式

+ class关键字

  与java类似，是从ES6定义的，用法与java基本类似

  + 区别1：构造方法的名字固定为constructor
  + 区别2：静态方法与属性前加static关键字，其余为非静态

+ 使用对象字面量

  对象字面量是最常见且最简洁的创建对象的方法。它允许你直接在代码中使用大括号 `{}` 来定义对象的属性和方法。

  ```js
  let person = {
      name: "Alice",
      age: 30,
      greet: function() {
          console.log("Hello, my name is " + this.name);
      }
  };
   
  person.greet();
  ```

+ 使用构造函数创建对象

  构造函数是一种可以创建特定类型对象的函数。构造函数的名字通常以大写字母开头，以区别于普通函数。你可以使用 `new` 关键字来调用构造函数，并创建一个新的对象实例。

  ```js
  function Person(name, age) {
      this.name = name;
      this.age = age;
      this.greet = function() {
          console.log("Hello, my name is " + this.name);
      };
  }
   
  let person = new Person("Charlie", 28);
  person.greet();
  ```

+ 静态属性（与java一样，但写法有所不同）

  ```js
  // 声明构造方法
  function Person(name,age){
      // 在内部声明赋值的为非静态属性
  }
  // 直接使用函数名.属性名添加函数
  Person.arms = 2
  Person.walk = function (){
      console.log('人都有两个胳膊')
      console.log(this.arms)
  }
  ```



#### 七、内置对象方法

+ 包装类

  JS的基本数据类型，底层是拥有对应的包装类的，请对比java（类似）

+ Object内置类型

  与java类似，在js中存在原型链，几乎所有的对象类型都会隐式继承于Object类，除了基于null原型或特定环境的对象，如Array和function等等。

  + Object.keys() 静态方法

    ```js
    // 获取对象中所有属性的键（即属性名）
    const  object = {
        name:'pink',
        age:18
    }
    // 获取所有的key值，返回值为一个数组，包含所有的属性名，采用数组解构可以直接赋值
    const arr = object.keys(object)
    ```

  + Object.values() 静态方法

    ```js
    const object = {
        name:'pink',
        age:18
    }
    // 返回所有value值
    const arr = object.values(object)
    ```

  + Object.assign(o1,o2)对象拷贝

    ```js
    // 将o2对象的引用赋值给o1,通过该方式的拷贝的是引用，也就是两个对象指向了同一份引用
    const o = {
        name:'pink',
        age:18
    }
    // 将o赋值为o1,指向了同一份引用
    Object.assign(o1,o)
    ```



+ Array内置类型

  Array数组提供了许多方法，join拼接字符串，find查找元素，concat合并数组，sort排序、findIndex查找指定索引值

  + forEach方法

    ```js
    // 遍历数组，请查看本章第五节加强for循环
    ```

  + filter(function(currentValue, index, arr), thisArg)

    ```js
    // 数组过滤,其中函数必须提供boolean形式返回值，真为保留  thisArg用于指定函数的this指向，箭头函数无效
    const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
     
    // 创建一个新数组，包含所有大于5的元素
    const filteredNumbers = numbers.filter(function(number) {
      return number > 5;
    });
     
    console.log(filteredNumbers); // 输出: [6, 7, 8, 9, 10]
    
    ```

  + map迭代处理数据

    ```js
    // map方法也必须提供返回值，map会将每个数组元素作相同的处理，并返回，同时也提供了this指向，箭头函数失效
    const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    const mapNumber = numbers.map(function(number){
        return number*=2
    },this) // this可以指定过滤条件函数中的this，但此时函数不能使用箭头函数，否则会从上下文中捕获this
    ```

  + reduce累计器

    ```js
    // reduce的工作原理为：对每个元素操作过后的最后的返回值赋值给init，最后将init返回
    // reduce遍历每个数组元素，但最后的返回值只有一个，因此常用于求数组和，求最大/小值，平均值，字符串凭借等等
    const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    const sum = numbers.reduce(function(init,current){
       return init+=current                  
    })
    
    const sum = numbers.reduce(function(init,current){
        // initValue是为init的赋初值
    },initValue)
    ```

+ String静态(与Java类似)

  length求长度、split分割、substring截取、startsWith以..开头，大小写转换，字符替换、匹配



#### 八、原型（非常重要）

+ 原型出现的原因

  使用构造函数的方式创建对象（也就是new 构造函数() ），每次创建对象时构造函数中的属性和方法都会创建一份副本保存在该对象的引用中，以供其调用。**这存在一个问题就是，当创建对象的个数非常多时，每个对象都会保存一个方法副本，那么一千个、一万个方法副本 就可能会引起内存溢出，因此我们希望每个对象都指向了一份公用的方法原型中，在调用时每个对象都去访问该原型方法，不需要创建副本，共用一个对象即可**

+ 原型方法

  在JavaScript开发中，通常建议避免在构造方法（构造函数）内部创建方法，而是应该直接将方法创建在原型（`prototype`）内部。这种做法有几个重要的原因：

  1. **内存效率**：如果在构造方法内部创建方法，那么每次创建新对象时都会为该对象创建一个新的方法副本。这不仅浪费内存，而且降低了性能，因为方法代码被重复存储了多次。相反，如果将方法定义在原型上，那么所有实例都可以共享同一个方法实现，从而节省内存并提高性能。
  2. **原型链继承**：JavaScript中的对象通过原型链来继承属性和方法。将方法定义在原型上，可以确保这些方法能够被所有实例对象所继承。这是JavaScript中实现继承的核心机制之一。
  3. **封装和可维护性**：将方法定义在原型上，可以使代码更加清晰和易于维护。构造方法应该专注于初始化对象的实例变量，而方法定义则应该放在原型上，这样更符合面向对象编程的封装原则。
  4. **避免意外的行为**：如果在构造方法内部修改原型（例如，添加新方法），这可能会导致意外的行为，特别是当构造方法已经被多次调用，并且已经创建了对象实例时。这种修改会影响到所有已经存在的实例，以及未来创建的实例。

+ 创建原型方法的方式

  ```js
  function Person(){
      // 属性
      // 请不要在构造函数内部创建方法，因为每当创建一个对象时，构造函数内部的函数都会被创建一份副本
  }
  // 通过以下方式创建的函数只会存在一份，每次通过函数调用都是调用的原型对象上的方法
  Person.prototype.方法名 = function(){
      
  }
  ```

+ constructor属性

  用一句话描述 构造函数拥有原型对象，而原型对象的constructor属性反过来又指向了构造函数本身

  ```js
  function Person(){
      
  }
  // 构造函数拥有原型对象
  Person.prototype
  // 原型对象的constructor属性指向了函数本身
  Person.prototype.constructor === Person 
  ```

  请注意以下问题

  ```js
  // 当原型对象挂载很多方法时，可以直接调整整个原型对象，但会导致constructor属性丢失，需要重新制定
  function Person(){
      
  }
  Person.prototype = {
      // 重新指定constructor属性
      constructor:Person,
      方法1:function(){},
      方法2:function(){},
      方法3:function(){}
  }
  ```

+ 对象原型 _proto\_

  对象原型_proto\_指向了构造函数的原型对象prototype,之所以对象可以使用构造函数prototype原型对象的属性和方法，就是因为对象有\_proto\_原型的存在

+ 原型总结与原型链

  + 原型总结

    1. 构造函数拥有prototype对象，记录了构造函数的原型对象，类似与“模型与模型概念”，构造函数（模型）可以定义各种属性，而原型对象（prototype）上定义了固定的函数与属性供对象使用。
    2. 对于prototype对象在赋值时，若使用{}赋值，应该重新指定其constructor属性，指定其构造函数
    3. 当对象通过构造函数创建后，会存在[[Prototype]]属性指定其对象原型
    4. 综上：若使用上述模型的比喻，可以看做  模型对象通过“构造函数”创建，但其本质上是仿照模型概念而生成的（对象的[[Prototype]]指向了其对象原型），因此对象拥有 构造函数的普通属性 也拥有原型对象的公共方法与属性

  + 原型链

    原型链是指当前对象拥有一个 对象原型 指向了自己的原型对象，原型对象身上存在属性constructor指向了构造方法，以及[[Prototype]]指向了自己的原型；（可以想象为当前对象身上存在一条链，每一个链点都有一个尾巴指向了自己的构造函数）

+ 继承

  将希望继承的父类放入当前构造函数的”蓝图“（也就是原型对象中），并且重新指定自己的constructor属性，因为赋值时若使用 = 会覆盖该属性，**同时有一个问题需要解决，当两个子类的prototype属性同时指向了同一个父类，当为其中一个子类添加自己的公共方法时，需要修改prototype对象，向内添加方法或属性，直接修改了该对象，会使得另一个子类的prototype对象发生变化，因此在对子类prototype进行赋值时，需要通过new 父类()的方式指定prototype，方便添加子类独有的公共属性和方法**

  ```js
  function People(){
      this.eyes = 2
      this.head = 1
  }
  function Woman(){
      
  }
  Woman.prototype = new People()
  // 将自身构造器指回自身
  Woman.prototype.constructor = Woman
  // 向子类添加独有方法
  Woman.prototype.baby = function(){
      console.log('我会生孩子')
  }
  
  function Man(){
      
  }
  Man.prototype = new People()
  Man.prototype.constructor = Man
  ```




#### 九、拷贝

+ 深浅拷贝

  + 浅拷贝（仅复制引用）

    ```js
    // 使用Object.assign()方法
    // 将o2对象的引用赋值给o1,通过该方式的拷贝的是引用，也就是两个对象指向了同一份引用
    const o = {
        name:'pink',
        age:18
    }
    Object.assign(o1,o)
    
    //使用展开运算符（...）
    let original = { a: 1, b: { c: 2 } };
    let shallowCopy = { ...original };
    
    // 使用slice()方法
    let originalArray = [1, 2, 3, { a: 4 }];
    let copiedArray = originalArray.slice(); 
    // 使用concat方法
    let originalArray = [1, 2, 3, { a: 4 }];
    let copiedArray = originalArray.concat();
    ```

  + 深拷贝

    ```js
    // 通过json转为字符串，在转回来
    let original = { a: 1, b: { c: 2 } };
    let deepCopy = JSON.parse(JSON.stringify(original)); 
    // 通过lodash中的cloneDeep实现拷贝，需要引入相关库，使用时再查询
    const copiedObject = _.cloneDeep(originalObject);
    ```

+ 异常(与java一样)

  try-catch-finally，以及throw new error('')



#### 十、收尾处理

+ call方法

  ```js
  // 使用方法调整函数，同时指定被调用函数的this值
  // call就是函数的调用，只是在调用时通过call函数指定了this的值
  函数名.call(thisArg,arg1,arg2)
  
  const obj = {
      uname:'pink'
  }
  function fn(){
      
  }
  // 将fn的this值调整为obj
  fn.call(obj)
  ```

+ apply方法

  ```js
  // 与call类似，只不过第一个参数为this值，第二个参数为原函数的参数数组
  ```

+ bind方法

  ```js
  // bind不会调用函数
  const btn = document.querySelector('button')
  btn.addEventListener('click',function(){
      this.disable = true
      // setTimeout的调用者是window
      setTimeout(function(){
          // 若直接使用this，指向的是window，可以通过bind调整this,直接函数.bind(NewThis)
      }.bind(btn),2000)
  })
  ```

+ 防抖与节流

  防抖：在单位时间内频繁触发事件，若上次事件还没结束，会直接打断，重新执行（即只执行最后一次，类似王者回城，打断需重开始）

  节流：在事件执行过程中，不允许该事件再次触发，需等待事件执行结束才可触发（王者放技能，一个放完才能放第二个）
