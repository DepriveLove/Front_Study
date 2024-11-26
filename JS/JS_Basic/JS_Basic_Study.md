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

  

