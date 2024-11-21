### CSS基础

------

#### 一、CSS选择器

+ 通配选择器

  + 作用：可以选中所有的HTML元素,常用于样式清除

  + 语法：

    ```html
    * {
    	属性名:属性值;
    }
    ```

  

+ 元素选择器

  + 作用：选中某种元素，统一设置样式

  + 语法：

    ```html
    标签名 {
    	属性名:属性值;
    }
    ```

  

+ 类选择器

  + 作用：为HTML元素添加class属性，通过.class的方式选中这些元素

  + 语法：

    ```html
    .class {
    	属性名:属性值;
    }
    ```

    

+ id选择器

  + 作用：为HTML元素添加唯一标识的id属性，通过#id的方式选中该元素，一个id只能对应一个HTML元素

  + 语法：

    ```html
    #id {
    	属性名:属性值;
    }
    ```

------



+ 交集选择器（且条件，紧紧相连）

  + 作用：通过多条件并列，选中同时满足所有条件的HTML元素，条件与条件之间紧紧相连

  + 语法：

    ```html
    条件1条件2条件3 {
    	属性名:属性值;
    }
    ```

  + 注意事项

    + 条件之间相互紧挨的，不可使用空格分隔开
    + 当元素选择器出现时，应该放在第一个条件的位置，且不能同时出现两个元素选择器作为条件



+ 并集选择器（或条件，逗号分割）

  + 作用：选中多个选择器对应的元素，又称：分组选择器，条件之间使用逗号分割

  + 语法：

    ```html
    选择器1,选择器2,选择器3 {
    	属性名:属性值;
    }
    ```

  + 举例

    ```html
    <!-- 选中id为root 或 class为rich 或 class为beauty 的所有元素 -->
    #root,
    .rich,
    .beauty {
    	font-size:40px;
    	background-color: green;
    }
    ```



+ 后代选择器（所有子孙后代，使用空格分割开）

  + 作用：选中指定元素中，符号要求的后代元素

  + 语法：选择器1  选择器2 ...  选择器n { }

    > 选择器之间使用空格分隔开，且祖先在前，后代在后



+ 子代选择器（选中子代元素，使用>链接）
  + 作用：选中指定元素中，仅选中符合要求的子代元素，后代不会被选中
  + 语法：选择器1 > 选择器2 { }



+ 兄弟选择器

  + 相邻兄弟选择器:选中div后紧紧相邻的p元素，若div与p元素之间有其他元素，该选择器会失效

    ```html
    div+p {
    	
    }
    ```

  + 通用兄弟选择器：选中div后所有的兄弟p元素，无论中间是否有其他元素

    ```html
    div~p{
    
    }
    ```



+ 属性选择器

  + 仅指定属性名

    选中拥有title属性的元素，不规定属性的值

    ```html
    [title] {
    	
    }
    ```

  + 指定属性名与属性值

    选中具有指定属性，且属性值为value的元素

    ```html
    [title="value"] {
    
    }
    ```

  + 指定属性名与属性值以特定字符开头

    ```html
    [title^="a"] {
    	//选中拥有title属性，且属性值以a开头的元素
    }
    ```

  + 指定属性名与属性值以特定字符结尾

    ```html
    [title$="u"] {
    	//选中拥有title属性，且属性值以u结尾的元素
    }
    ```

  + 指定属性名与属性值包含某段字符的元素

    ```html
    [title*="u"] {
    	//选中具有title属性，且属性值包含字母u的元素
    }
    ```



> 总结：
>
> 基础选择器：通配选择器（*）、元素选择器（元素名）、id选择器、class选择器
>
> 复合选择器：交集选择器（条件相连）、并集选择器（逗号分割）
>
> ​						后代选择器（空格分割）、子代选择器（箭头分割）、兄弟选择器（+紧跟兄弟，~后边所有兄弟）
>
> ​						属性选择器( [属性名] ，[属性名=值]，[属性名^=开头字符]，[属性名$=结尾字符]，[属性名*=包含字符])			



------



#### 二、伪类选择器

+ a标签的四大伪类选择器（link、visited、hover、active）

  + :link（选中未访问过的a元素）

    ```css
    a:link {
        color:orange;
    }
    ```

  + :visited（选中访问过的a元素）

    ```css
    a:visited {
        color:gray
    }
    ```

  + :hover（选中鼠标悬浮的元素）

    ```css
    a:hover {
        color:skyblue;
    }
    ```

  + :active（选中鼠标正在点击还未释放的元素）

    ```css
    a:active {
        color:red;
    }
    ```

  + :focus（选中获取焦点的输入类表单元素）

    ```css
    inpput:focus {
        color:white;
    }
    ```

  > 1. link、visited、hover、active在CSS样式中的书写顺序不可以被改变，改变后某些样式可能会失效
  >
  >           2. link、visited是a标签的专属伪类选择器，hover、active对于大部分元素都可使用



+ 结构伪类选择器

  + :first-child（选中给定元素集的第一个孩子）   :last-child类似

    > 总结：该选择器能选中的只能是第一个孩子，该孩子与父元素之间不可被其他元素隔开
    >
    > ​		    当div>p :first-child时第一个孩子不可以被其他元素所包裹，因为div>p选择的是儿子标签
    >
    > ​			当div p :first-child选中的是div后代中的嫡长子、嫡长孙……可以同时选中多个元素
    >
    > xxx选择器：first-child
    >
    > ​	xxx选择器的集合中第一个孩子必须是结构上的第一个元素

    ```html
    <style>
        // div的后代p中嫡长子与嫡长孙等嫡长后代，可以同时选中多个嫡长后代，不可被其他元素隔开
        div p :first-child {
            
        }
        
        // div子代p中的嫡长子不可被其他元素隔开
        div>p:first-child{
            
        }
    </style>
    <div>
        <p>嫡长子</p>  //选中  div>p:first-child与div p:first-child
        <marquee>
        	<p>嫡长孙</p>  //选中  div p:first-child
        </marquee>
        <p>2</p>
        <p>3</p>
        <p>4</p>
    </div>
    ```

  

  + :nth-child(count)

    选中给定集合的第几个孩子

    > count的取值：数字、2n（2的倍数）、3n（3的倍数）、even（偶数）、2n+1（奇数）、odd（奇数）
    >
    > ​						 -n+5（选中前5个）

    ```css
    div>p:nth-child(count){
        // count的范围为1-正无穷，当count超出集合范围时，谁都无法选中
    }
    ```

  

  + ：first-of-type与：last-of-type，nth-of-type（）

    > 与：first-child不同的是，：first-child当第一个满足的元素不是结构上的第一个孩子时，不可以被选中。
    >
    > ：first-of-type是选中第一个满足条件的元素，无论是不是结构上的第一个孩子

    ```css
    div>p:first-of-type{
        
    }
    <div>
    	<span></span>
    	<p></p>       // first-child不可选中，first-of-type可以被选中
    	<p></p>
    	<p></p>
    </div
    ```

> 结构伪类总结：
>
> + first-child 与 last-child（两者的使用细节主要在复合筛选时，筛选出的集合到底是什么样子的）
>
>   + 筛选的元素必须位于集合的第一个孩子（最后一个孩子）
>   + 筛选出的元素在结构上必须是父元素的第一个子元素
>
>   
>
> + nth-child(an+b)
>
>   + 在使用时只需要保证内部填写的值，满足ax+b的形式即可
>   + 需要范围选中时可以利用负数，如-n+5可选中前五个
>
>   
>
> + first-of-type、last-of-type与first-child、last-child的区别
>   + 前者只关注所删选出的元素集合的位置的第一位和最后一位
>   + 后者需要关注其在结构上的第一位和最后一位
>   + 用法：当希望选中的元素上还有其他元素，应使用前者，且后者的用法较为复杂，慎用
> + nth-of-type（）与nth-child（）的区别
>   + 前者的计数方式是对于集合来讲的，所有满足的元素从头到尾计数
>   + 后者的计数方式是对于所有兄弟的，无论该元素有没有被筛选出来，即当希望选中一堆p元素时，若p元素上方有其他元素时，后者的计数方式是从其他元素开始数的，前者是从第一个p元素开始数
>
> 
>
> + 不常用的结构伪类
>
>   + nth-last-child（）与nth-last-child-type（）
>
>     从后往前数
>
>   + ：only-child
>
>     选中给定集合中没有兄弟的元素，即它的父元素中仅有其一个元素
>
>   + ：only-child-type
>
>     选中给定集合中仅有一种该类型的元素，eg：  span:only-child-type   选中可以有其他类型兄弟的span元素
>
>   + div：empty
>
>     选中给定元素中没有内容的元素

+ 否定伪类

  + 排除满足条件的元素，选中其他元素
  + 语法：eg  div>p:not(.fail)   排除div子代p中类名为.fail的元素，括号中可以使用其他方式的选择器

+ UI伪类

+ 语言伪类

+ 目标伪类

  + 借助a标签的锚点跳转的方式选中目标给定样式

    ```html
    // 锚点的写法
    <a href="#tar"></a>
    
    <div id="tar">
        
    </div>
    
    // 当点击a标签借助锚点跳转至给定div时，div就会被作为目标伪类选中
    div:target{
    	
    }
    ```

#### 三、伪元素选择器

+ div::first-letter

  + 选中div中的第一个字符

  ```html
  // 选中div中的第一个字符
  div::first-letter {
  	color:red;
  	font-size:20px;
  }
  
  <div>
      Lorem
  </div>
  ```

+ div::first-line

  + 选中div中的第一行

+ div::selection

  + 选中div中被鼠标选中的字符

+ input::placeholder

  + 选中input元素中的提示文字

+ p::before

  + 选中p元素内容之前，可以对其进行操作

+ p::after

  + 选中p元素内容之后

------



#### 四、选择器优先级

+ CSS选择器优先级顺序

  > 当不同的CSS选择器选中相同的元素时，要根据优先级判断哪个样式生效
  >
  > 行内  >  ID选择器  >  类选择器  >  元素选择器  >  通配选择器

+ 选择器权重

  + 权重格式（a,b,c)

    + a：ID选择器的个数
    + b：类、伪类、属性选择器的个数
    + c：元素、伪元素的选择器的个数

  + 比较方式

    两个选择器的权重按照顺序依次比较，平局则向后计算，直到决出胜负，胜者权重更高，若全部相等，则按照书写顺序，后来者居上





### CSS样式

------

#### 一、字体属性（可继承）

+ 字体大小——font-size

  > 注：对于字体大小，在不同的浏览器中有不同的限制，如Chrome浏览其中的字体大小会在浏览器内部做最小限制，最小为可以设置到多少px，同时对于一些没有给定font-size属性的字体，也会有浏览器默认的字号，它对于默写单位em或rem等会有影响，因此在大多数情况下，请在html中为页面整体设置字体大小，方便em与rem单位以及在未给定某些元素字体大小时，可以通过继承的方式沿用html的字体大小

  ![image-20241111172542703](C:\Users\27120\AppData\Roaming\Typora\typora-user-images\image-20241111172542703.png)

  

+ 字体——font-family

  + 衬线字体与非衬线字体

    衬线字体的横竖撇捺有棱角，非衬线线条粗细基本相同，不会发生变化

  + font-family属性值

    1. 使用字体的英文名字兼容性会更好，具体的英文名可以自行百度
    2. 如果字体名包含空格，必须使用引号包裹，建议都使用引号包裹
    3. 可以设置多个字体，按照从左到右的顺序逐个查找，找到就用，没得找到就使用后面的，且在开发中通常要求字体同属于衬线或非衬线类型，在最后加入serif（衬线字体，不需要双引号），sans-serif（非衬线字体）
    4. windows中默认字体就是微软雅黑

+ 字体风格——font-style

  + 属性值
    + normal：默认值
    + italic：     斜体，在字体设计时，若该字体有斜体，则会使用设计的斜体，若没有效果与oblique相同
    + oblique：斜体，强制倾斜

+ 字体粗细——font-weight

  + 属性值

    + lighter：细
    + normal：正常
    + bold：粗
    + bolder：很粗（多数字体不支持

    

+ 字体复合属性——font

  + 书写规则
    + 字体大小、字体族必须都写上
    + 字体族必须为最后一位，字体大小必须为倒数第二位，其他任意
    + 属性之间使用空格隔开

  > font：bold  italic  100px  “STHupo”，sans-serif



#### 二、文本属性（可继承）

+ 文字颜色——color

  ```css
  div {
  	color : rgb(112,45,78);
  }
  ```

+ 文本间距——letter-spacing与word-spacing

  + 区别

    前者是调整每一个字符之间的间距，后者仅调整空格的大小间距

  ```css
  .letter{
  	// 调整每个字符之间的间距为10px
   	letter-spcing:10px;
  }
  .word{
  	// 调整每个空格的大小为10px
  	word-spacing:10px;
  }
  ```

  

+ 文本修饰——text-decoration

  + 可选值
    + none：无任何效果
    + underline：下划线
    + overline：上划线
    + line-through：删除线
  + 线条样式
    + dotted：虚线
    + wavy：波浪线

  ```css
  div {
  	text-decoration:underline dotted red
  }
  
  a {
      text-decoration:none
  }
  ```



+ 文本缩进——text-indent

  > 文本缩进常用为缩进两字符，在设置单位时，若以px为单位则设置为两倍的字体大小，若以em为单位时设置为2em



+ 文本对齐

  + 水平对齐——text-align
    + left：默认值
    + center：居中对齐
    + right：右对齐
  + 垂直对齐
    + 单行文字居中 ：一般可以给定行高和元素的高度一致时，会将元素放在最中间
  + 基线对齐——vertical-align
    + baseline：默认值
    + top：当一行中两个两个元素的字体大小不同时，默认会采用基线对齐的方式，即两个XX的底部会对齐，若设置小字体的vertical-align为top时该元素会移至最上方
    + bottom：与top同理
    + middle：使给定middle的元素的中间   与  父元素X的交叉位置对齐

  > vertical-align的作用：用于控制元素在那一行垂直方向上的对齐方式，当一行中有图片时，给图片一个vertical-align属性时，middle就会完全居中，当图片的高度大于文字行高时，该行的高度会被图片撑开，此时给定该属性时改行的文字就会按照该属性发生变化
  >
  > 基线垂直居中操作的是父元素内部的子元素，只有子元素可以给定vertical-align



+ 行高——line-height
  + 行高是指在选中文字时，被选中的范围就是那一行的行高
    + 当了解完字体设计的基线概念，可以知道X的底部就是基线，其余字符都是按照贴准基线的，g的与b都是那个圆环贴着基线，在了解完基线后，需要知道font-size指的是在设计字体时会为文字给定一个框的概念，这个框的高度就是字体的大小，且并不是字体一定在这个框内，是可以超出这个框的
    + 在给定完行高和font-size后，并不能简单的认为字体的上间距与下间距都是相等的，因为字体设计的时候字体的大小是可以超出那个框的，故上间距和下间距只是基本相等，对于gbf等就会有些差距
    + 当行高与字体大小相等时，由于行高给定的是框的高度，且有些字符会超出这个框，故两行之间有些地方会发生一些重合，这是字体设计时的标准，所有行高一般在开发时会设计为字体大小的1.5倍
    + 在给定字体大小后，可以借助em单位给定行高为1.5em



------

#### 三、列表属性

+ 列表复合属性list-style（调整符号样式、位置、自定义符号）

  > 复合写法：list-style : decimal  inside  url("../video.png")
  >
  > 该属性可以在ul ol上使用，调整整体的样式，也可以在li上使用调整单个li的样式

  + 列表符号list-style-type（文字前的符号）
    + 常用值：none，square，decimal
  + 符号位置list-style-position（符号位置，背景颜色是否可以笼罩到）
    + 常用值：inside、outside
  + 自定义符号list-style-image("url"）



------

#### 四、表格属性

+ 边框复合样式border

  <u>边框相关的属性，不仅仅时表格能用，其他元素也能用</u>

  > 注：给table加上边框复合样式调整的仅为边框最外边的边框线，每个单元格之间并不会有样式,且在单独调整的时候必须三个样式全部书写，否则边框会失效
  >
  > 当给table、td、th同时加上border样式时，每个单元都会有一圈独立的边框线，两个单元格之间也会有相应的缝隙，table最外边还会有一圈边框线，将所有单元格框在一起
  >
  > 
  >
  > 写法：border：2px  green  solid
  >
  > 
  
  1. border-width：调整边框线的宽度
  2. border-color：调整边框线的颜色
  3. border-style：调整边框线的样式，solid（实线）、dotted（虚线）、doubble（双实线）



+ 表格table独有的属性

  + 表格列宽 table-layout

    auto（默认）、fixed（固定：固定时会将每个人平分表格宽度，同时还可以单独选中某个单元格给width）

  + 表格单元格之间的间距 border-spacing

    border-spacing：2px（当给定0px时，两个线会紧挨在一起，但不会重合，即线宽会双倍加粗）

  + 合并相邻单元格的边框  border-collapse

    separate（默认）、collapse（合并：合并边框线，当给定该值时，border-spacing会失效）



------

#### 五、背景属性

+ 背景复合属性background

  > 复合属性：background：skybule   url()   no-repeat  left  top  
  >
  > 

  + 背景颜色 background-color
  
  + 背景图片
  
    background-image：url（""）； 
    
  + 设置背景图片的重复方式
  
    background-repeat：repeat（重复）、no-repeat（不重复）、repeat-x（x轴重复）、repeat-y（y轴重复）
  
  + 控制背景图片的位置
  
    background-position：left top；（左上）（10px，20px相对于左上角 左10  上20）



+ 鼠标相关属性

  + cursor

    为某元素设置该属性时，可以控制鼠标悬浮时的鼠标图标效果





### 盒子模型

------

#### 一、前置知识

+ 常用的长度表示单位

  + 像素px

    常用的长度表示单位

  + em（相对于当前元素的font-size的倍数）

    由于浏览器自身有默认的font-size或父元素会设置font-size，且font-size有继承性，故每个元素都会有对象的font-size值，1em对应的是自身font-size的1倍的px

  + rem（相对于根元素的font-size的倍数，一般默认指的是html的font-size）

  + 百分比表示

    百分比是相对与其父元素的长度的百分比，100%表示的是占满整个父元素或长度与父元素相等，对于未定位元素参考的是父元素，在做类似浮动、定位等操作后，百分比表示方法参考的对象可能会发生变化，因此在实际应用中并不推荐使用这种表示方法



+ 元素的显示默认
  + block块级元素
    + 在页面中独占一行，不会与任何元素共用一行，是从上到下排列的
    + 默认宽度：撑满整个父元素
    + 默认高度：由内容撑开
    + 可以通过CSS样式调整宽高
  + inline行内元素
    + 在页面中不独占一行，一行中不能容纳的行内元素，会在下一行中继续从左到右排列
    + 默认宽度：由内容撑开
    + 默认高度：由内容撑开
    + 不可以通过CSS样式调整宽高
  + inline-block行内块元素
    + 在页面中不独占一行，一行中不能容纳的行内元素，会在下一行中继续从左到有排列
    + 默认宽度：由内容撑开
    + 默认高度：由内容撑开
    + 可以通过CSS样式调整宽高



+ 修改元素的显示模式display
  + 值：block块元素、inline-block行内块、inline行内元素



#### 二、盒子模型的组成

+ 模型大小计算

  CSS会将所有的HTML元素都看做为一个盒子，所有的样式都是基于这个盒子，当为元素设置宽高时，是给内容区设置宽高，盒子整体的大小需要加上盒子的边框和盒子的内边距（补白区域），margin是用于调整盒子与其他元素盒子之间的距离和位置

  margin：盒子与外界的距离

  border：盒子的边框

  padiding：紧贴内容区的补白区域

  content：元素中的文本或后代元素都是它的内容

+ 盒子内边距padding（不可为负数）

  + 行内元素设置上下内边距出现覆盖问题

    行内元素设置左右边距会正常显示，但设置上边边距后，只有内容区占位置，上下内边距可能会覆盖在其他元素上，这时行内元素本身性质决定的，因此在开发时不要为行内元素添加上下内边距

  

+ 盒子边框border

  + 当为盒子border时，盒子的整体大小是内容区+padding+border的整体宽度



+ 盒子外边距margin

  + 盒子的外边距是用于调整盒子的整体位置的，不参与盒子整体大小的计算

  > margin注意事项
  >
  > 1. 当一个元素设置内边距时，其内元素的外边距是从内容区开始计算的，并非从父元素的左上角
  > 2. 行内元素可以设置左右外边距，不可以设置上下外边距
  > 3. 对于块级元素来说，设置左右边距为auto时，可以使得块级元素居中
  > 4. margin的值可以是负值，会导致盒子整体的移动，可能会覆盖在其他元素上



#### 三、margin相关问题

+ margin塌陷问题

  > 问题描述：当存在一个父元素中有n个子元素，如果第一个子元素贴紧父元素时，给其设置上外边距时该上外边距会被其父元素抢走，即：子元素的上外边距会消失，出现在父元素身上
  >
  > 同时最后一个元素如果紧贴父元素下边框，设置下外边距时，也会出现塌陷问题
  >
  > 
  >
  > 主要原因为：当出现类似情况时，上外边距是不属于盒子的大小的，且外边距只是为了盒子的位置出现的，故紧贴父元素添加上外边距时，浏览器会认为是你希望整个父元素向下移动
  >
  > 解决方案
  >
  > 	1. 方案一：可以为父元素添加一个边框，且边框宽度不允许设置为0px
  > 	1. 方案二：为父元素设置一个padding
  > 	1. 方案三：为父元素添加    overflow：hidden

  ```html
  <style>
      .outer{
          width:400px;
          height:400px;
          background-color:gray;
      }
      
      .inner1{
       	width:100px;
          height:100px;
          background-color:orange;
      }
      
      .inner2{
          width:100px;
          height:100px;
          background-color:green
      }
  </style>
  <div class="outer">
      <div class="inner1">inner1</div>
      <div class="inner2">inner2</div>
  </div> 
  ```



+ margin合并问题

  > margin合并问题只出现在上下盒子中，左右盒子并不会出现这种情况
  >
  > 问题描述：当给上边盒子给定下边距，下边盒子给定上边距，浏览器会从中挑选最大值，作为两个盒子之间的距离
  >
  > 解释：外边距的存在是为了调整盒子的位置，且外边距是参与盒子大小计算的，当为两个盒子分别添加外边距时，相当于生活中你希望物品1与物品2的距离为100，对于物品2而言，调整过后物品2与物品1的距离也是100，当希望设置物品2的外边距时，小于之前的距离浏览器会认为没必要移动，则取其中最大值

  

+ 内容溢出overflow

  + hidden

    当一个元素内部的内容过多，纵向或横向上发生了内容溢出，可以给该元素添加属性overflow：hidden，可以将这些溢出隐藏

  + scroll

    与hidden类似，超出部分也会隐藏，同时会在超出方向上产生一个滚动条，方便观看隐藏的内容

  + auto

    当内容没有溢出时，与默认值visible类似，当有内容溢出时，与scroll类似



#### 四、隐藏元素的两种方式

+ 通过dispaly控制

  > 通过这种方式隐藏元素，该元素会整个脱离文档，彻底消失，其后的元素会占据其位置
  >
  > display：none



+ 通过visibility控制

  > 与display的区别就是这种方式依旧占据位置
  >
  > visibility：hidden



------

### 布局

#### 一、浮动

+ 元素浮动后的特点
  + 脱离文档流，在3d方向上可以看到元素浮动后漂浮在原来的位置上
  + 不管浮动前是什么元素，浮动后默认宽与高都是被内容撑开，且可以设置宽高
  + 不会独占一行，可以与其他元素共用一行
  + 不会出现margin合并问题，也不会出现塌陷



+ 元素浮动后的效果

  **脱离文档流**‌：浮动元素会脱离文档流，不再占据原来的位置，后面的元素会向上移动填补空缺‌

  **对齐方式**‌：浮动元素会尽可能地向左或向右浮动，直到碰到父元素的边界或其他浮动元素的边界‌25。

  **影响布局**‌：浮动元素会影响周围元素的布局，可能会导致布局错乱，因此需要清除浮动‌



+ 浮动的影响
  + 当父元素的所有子元素都加上浮动效果之后，若没有给父元素设置高度，父元素就会塌成一条线
  + 当父元素中有子元素浮动时，如果此时有一个子元素没有浮动，那么该子元素上就可能会被其他元素所覆盖，且元素的文字会被浮动元素溢出盒子
  + 如果父元素可以容纳四个div，前三个div全部浮动，若第四个div不浮动，该div会钻入第一个div的后边，文本会出现在第一个div的下方，若四个div修改display为inline-block，浏览器会将其视为文本，环绕在前三个div的后边，也就是以前浏览器的文字环绕模式



+ 浮动影响的消除（通过BFC双伪元素的形式清除影响）

  > 选中父元素，通过：：after选中最后一个元素后边的位置（伪元素），
  >
  > 为它添加content：‘’；display：block；clear：both

  ```css
  .outer::after{
      content:'';
      display:block;
      clear:both;
  }
  ```

  

#### 二、相对定位 （不脱离文档）

> position：relative；     // 设置完这个属性，必须要添加left、right、top、bottom等属性
>
> left：100px；				// 距离原来的位置，左边要留出100px；即向右移动100px

 相对定位是对于元素本身的位置移动的，且该元素并没有离开原来的位置，其他元素也不会占据它的位置，只是其被展现在相对定位后的位置



+ 相对定位不会脱离文档流，元素位置的变化，只是视觉效果上的变化，并不会对其他元素产生任何影响
+ 定位元素的显示层级比普通元素高，无论什么定位，显示层级都是一样的
+ left与right不能同时设置，top与bottom也不能同时设置
+ 相对定位的元素，也能继续浮动，**但不推荐这样做**
+ 相对定位的元素，也可以通过margin调整位置，**但不推荐这么做**



#### 三、绝对定位（脱离文档流）

+ 如何设置绝对定位

  + 给元素设置position：absolute即可实现绝对定位，仅设置这个位置，元素就会直接原地起飞脱离文档
  + 可以使用left、right、top、bottom调整元素的位置

+ 绝对定位的参考点（包含块）

  第一个开启定位的祖先元素，不限定什么定位，只要设置position即可；正常情况下为   子绝父相

+ 特点

  绝对定位与浮动不能同时设置，如果同时设置以绝对定位为主

  绝对定位也可以通过margin调整位置，但不推荐这样做

  无论是什么元素，设置绝对定位后，都变成了定位元素



#### 四、固定定位

+ 如何设置固定定位

  + 给元素设置 position：fixed即可实现固定定位
  + 可以使用left、right、top、bottom调整位置

+ 参考点

  参考整个页面的左上角

+ 特点

  + 脱离文档流，会对后面的兄弟元素、父元素有影响
  + 与浮动一起设置时，浮动会失效

+ 与绝对定位的区别

  绝对定位与固定定位都会脱离文档流，绝对定位的参考点为第一个设置定位的祖先元素，如果找不到就会参考视口；

  固定定位会直接参考视口



#### 五、粘性定位

+ 如何设置

  position：sticky；

+ 参考点

  希望哪个元素出现粘性定位，就将该属性加在那个元素上，且其参考点为第一个出现滚动条的祖先元素

















### CSS3简介

#### 一、CSS3私有前缀

W3C标准所提出的某个CSS特性中，在被浏览器正式支持前，浏览器厂商会根据浏览器内核，使用私有前缀来测试该CSS特性，在浏览器正式支持该CSS特性后，就不需要私有前缀了。

常见的私有前缀有：Chorme的-webkit-、Safari的-webkit-、Firefox的-moz-、Edeg的-webkit-



#### 二、CSS3新增长度单位

> rem也是CSS3新增长度单位

+ 单位VW（viewwidth）

  vw指的是整个视口的百分之多少，50vw就是视口的50%，故vw会随着浏览器的变化而变化具体的值

+ 单位vh（viewheight）

  与vw类似

+ 单位vmax（viewMax）

  选择视图中宽和高中的最大值，50vmax指的是其中最大值的50%

+ 单位vmin（与vmax类似）



#### 三、盒子模型新增属性

+ box-sizing

  + 常用值

    content-box：这是box-sizing属性的默认值。当设置为content-box时，元素的宽度和高度只包括内容区域（content），不包括内边距（padding）、边框（border）和外边距（margin）。这意味着在设置元素的宽度和高度时，需要额外考虑内边距、边框和外边距的影响‌。

    border-box：当设置为border-box时，元素的宽度和高度包括内容区域（content）、内边距（padding）和边框（border），但不包括外边距（margin）。这意味着设置元素的宽度和高度时，内边距和边框的宽度会被包含在内，不会增加元素的总宽度和高度。



+ resize

  规定用户是否可以在浏览器界面直接调整整个盒子的大小

  + 常用值

    - `none`：用户无法调整元素的尺寸，这是默认值。
    - `both`：用户可以在水平和垂直方向上自由调整元素尺寸。
    - `horizontal`：用户只能在水平方向上调整元素的宽度。
    - `vertical`：用户只能在垂直方向上调整元素的高度‌。

  + resize内置子元素的问题

    当有一个盒子设置了resize属性，内部也有一个盒子，且内部盒子的宽高超过了外部盒子的大小，resize会失效，因为浏览器需要知道当内部盒子超出外部盒子大小时，应该如何处理，因此如果希望resize属性能被正常使用，必须加上overflow属性



+ box-shadow 阴影属性

  + 复合属性box-shadow如何设置

    > 写两个值，含义：水平位置阴影   垂直位置阴影
    >
    > box-shadow : 10px  10px
    >
    > 
    >
    > 第三个为颜色   水平  垂直  颜色
    >
    > box-shadow：10px  10px  blue
    >
    > 
    >
    > 第三个为像素   水平  垂直   模糊程度，越大背景阴影越模糊
    >
    > box-shadow：10px  10px  20px
    >
    > 
    >
    > 写四个值：水平  垂直  模糊程度  颜色
    >
    > box-shadow： 10px   10px  20px  blue
    >
    > 
    >
    > 通过设置inset属性调整阴影具体方向,inset会使得阴影向内凹陷,形成阴影渐变的效果
    >
    > box-shadow: 10px  10px  20px  blue  inset



+ opacity透明度

  > opacity : 0 ;                  完全透明



#### 四、背景新增属性

+ background复合属性

  > background : 颜色  url  是否重复  位置/大小  原点  裁剪方式

+ background-origin背景起点

  正常情况下,图片展示是从盒子的内边距左上角开始展示,border区域在重复状态下,会衔接一些残缺部分进行展示

  > 值padding-box:图片展示从内边距原点开始
  >
  > 值content-box:图片展示从内容区原点开始
  >
  > 值border-box:从边框原点开始

+ background-clip背景图修剪(可以与background-origin联合使用)

  + border-box : 默认值,背景图超过边框部分会被修剪
  + padding-box : 超过内边距的部分会被修剪
  + content-box  : 超过内容区的部分会被修剪
  + text : 当文字颜色设置为透明色(transparent)时,背景图只会呈现在文字背后

+ background-size背景图压缩

  设置背景图的尺寸

  > 用长度值指定背景图片大小,不允许负值
  >
  > background-size : 300px  300px
  >
  > 
  >
  > 用百分比指定背景图片大小,不允许负值
  >
  > background-size : 100%  100%
  >
  > 
  >
  > 设置为contain可以保证图片原本宽高比,保证图片不变形的情况下呈现图片,当图片不足以占满父元素时,采用重复的方式补满整个父元素
  >
  > background-size : contain
  >
  > 
  >
  > 将背景图等比例缩放,直到完全覆盖容器,图片会尽可能全的展示在元素上,但要注意背景图片肯呢个展示不完整(是开发中比较好的选择)
  >
  > background-size : cover




#### 五、新增边框属性

+ border-radius边框圆角

  > 50px指的是每个角的两条边,从弯曲程度的地方引条垂线,两条边的垂线的交点,就是以交点为圆心,50px为半径的圆
  >
  > 边框圆角的最大值就是一条边的一半,此时原因就会移动至正方形的最中间
  >
  > border-radius：50px

+ outline复合属性  





#### 六、新增文本属性

+ 文本阴影 text-shadow

  > 设置两个值时,水平垂直阴影      设置三个值时,第三个为颜色        设置四个值时,水平垂直阴影  模糊程度  颜色
  >
  > text-shadow：3px  3px  10px  red

  + 常见效果1

    当文字颜色与背景颜色一致时,文字会融合在背景颜色中,此时将水平垂直阴影设置为0, 添加模糊程度就会出现渐变文字效果
    
  + 常见效果2
  
    当文字颜色与背景颜色相反时,添加模糊程度,会出现文字光晕的效果
  
+ 文本换行white-space

  > 原文输出,无论一句多长,代码中文本怎么能写,就怎么输出,打死不换行
  >
  > white-space:pre
  >
  > 在pre的效果基础上.超出元素边界自动换行
  >
  > white-space:pre-wrap
  >
  > 在pre的效果基础上,超出元素边界自动换行,且只识别文本中的换行,空格会忽略
  >
  > white-space:pre-line
  >
  > 全部文字在一行中展示
  >
  > white-space:nowrap

+ 文本溢出text-overflow

  > 要使得text-overflow生效,块容器必须显式设置  overflow为非visible值, 且white-space为nowrap 

  + clip

    当文本元素溢出时,将溢出部分截掉

  + ellipsis

    当文本元素溢出时,将溢出部分替换为...



#### 七、渐变

+ 线性渐变  

  > 默认从上到下，颜色可以有多个，从颜色1至后变化
  >
  > background-image ：linear-gradient（颜色1，颜色2，颜色3，...）
  >
  > 可以设置颜色渐变的方向  to 方位，eg：to  right top（右上）、20deg（20度角）
  >
  > background-image：linear-gradient（to right，颜色1，颜色2，颜色3）

+ 径向渐变

  > 默认当元素为正方形时，以中点为圆心，向四周扩散，长方形则以长宽中线交点为中心，以椭圆形式扩散
  >
  > background-image：radial-gradient（red，yellow，green）
  >
  > 
  >
  > 可以通过调整圆心的位置，改变扩散的效果，at left top以左上为圆心，向外按照红黄绿扩散
  >
  > background-image：radial-gradient（at  left  top，red，yellow，green）
  >
  > 
  >
  > 也可以通过像素的形式调整圆心，以元素左上角为基准  at  100px  50px
  >
  > background-image：radial-gradient（at  100px  50px，red，yellow，green）
  >
  > 
  >
  > 可以通过调整扩散的形状，改变扩散效果，长方形默认为椭圆，可以调成圆
  >
  > background-image：radial-gradient（circle，red，yellow，green）
  >
  > 
  >
  > 同时可以通过调整圆的半径调整扩散效果，两值相等为正圆半径为100，不等为椭圆
  >
  > background-image：radial-gradient（100px  100px，red，yellow，green）
  >
  > 
  >
  > 以上属性可以写在一起  圆心为150px，150px，扩散形式为椭圆长半径100px，短半径50px
  >
  > background-image：radial-gradient（100px  50px  at  150px  150px，red，yellow，green）

+ 重复渐变（重复线性渐变与重复径向渐变）



#### 八、web字体

+ 通过引入字体文件，将字体嵌入至项目（没有版权切忌使用）

  该方法有几个问题

  1、字体文件过大，当用户网速过慢时，网站字体会有一瞬间的变化

  2、若将字体文件放入服务器，当多人访问网站时，会多次访问服务器字体文件，下载量高可能冲毁服务器

  > 1、将字体文件.ttf文件引入项目
  >
  > 2、在使用前引入字体文件，通过自己设置的font-family字体即可设计
  >
  > ​	  @font-face{
  >
  > ​			font-family：'某某字体'
  >
  > ​			src：url（）
  >
  > ​	  }

+ 通过网上设计icon-font单独为某些字添加字体

  推荐使用阿里字体图标库



+ 字体图标

  > 为什么需要字体图标
  >
  > 对于项目中一些图标，如果设计为图片形式，在不同的设备上，可能会因为图片放大的问题发虚
  >
  > 同时也会一些其他问题

  更推荐使用SVG可缩放矢量图



#### 九、2D变换

+ 位移transform:translate()

  + 位移与相对定位类似，都不脱离文档流，不会影响到其他元素

  + 与相对定位的区别：相对定位的百分比值，参考的是其父元素，定位的百分比值参考的是其自身

  + 位移对行内元素无效

  + 位移配合定位，可实现元素水平垂直居中

    > .box {
    >
    > ​	position:absolute;
    >
    > ​	left:50%
    >
    > ​	right:50%
    >
    > ​	transform:translate(-50%,-50%)
    >
    > }

+ 缩放transform:scale

  > transform:scale(1.5,1.5)

+ 旋转transform:rotateZ

  请注意绕Z轴的旋转才是2d选中,绕x与y轴时,元素是需要突出3d效果的

  > 顺时针30度旋转
  >
  > transform:rotateZ(30deg)

+ 多重变换(综合属性)

  注:缩放的参考点是自身图形的中心,而位移参考的是原图的左上角,参考点不同,因此顺序不同会导致最终位置不同,类似高中函数中三角函数的缩放,顺序不同会导致最终表达式不同

  且在开发中请把旋转属性放在最后

  > transform：translate(-50%,-50%)  rotate(30deg)

+ 原点变化(调整变换的锚点)



#### 十、3D变换

+ 景深perspective：px

  日常生活中，在看一些立体3d物时会受到近大远小的影响，同样在CSS中也有这样的效果，其是调整宏观意义上，眼离该元素的位置，举例：若有一个300*300像素的div，若将其景深调整为150px，在旋转到接近90度时，该元素在视觉效果上就会非常接近眼睛，在网页的表现就是该元素会从父元素中一直延伸至网页底部，且整个元素会因为近大远小的效果长短会发生变化

+ 开启3D空间

  元素在进行3D变化的首要条件是父元素必须开启3D空间，且开启景深才会有近大远小的效果，若不开启景深，就是旋转过后，将元素在平面上进行投影

  > 开启3D空间
  >
  > transform-style：preserve-3d
  >
  > 调整景深通常为800px-1200px
  >
  > perspective：800px

+ 透视点的位置(观察位置)

  透视点的默认位置为开启3D观察空间的元素的正中央,在生活中,观察立体物品的效果会随着自身位置的不同而发生变化,透视点的位置就是指观察者所在的位置

  perspective-origin

+ 3D位移

+ 3D旋转

+ 3D缩放

+ 3D多重变换

+ 3D背部

#### 十一、过渡（transition）

+ 基本使用

  + transition-property

    > 当元素发生变化时，设置需要过渡变化的属性eg：当宽度和高度发生变化时，分别设置过渡时间为1s和5s
    >
    > transition-property：width，height
    >
    > transition-duration：1s，5s
    >
    > 若需要过渡的属性较多时，可以直接设置所有属性都添加过渡
    >
    > transition-property：all
    >
    > transition-duration：1s    设置一个时间所有元素共用

  + transition-delay

    指定开始过渡的延迟时间，单位s或ms

  + transition-timing-fuction

    1. ease：平滑过渡，默认值
    2. linear：线性过渡

       .....更多值使用时查询

+ 复合属性

  如果设置了一个时间，表示duration；如果设置两个时间，第一个时duration，第二个是delay，其他值没有顺序要求

  > transition：1s  1s  linear  all



#### 十二、动画animation



#### 十三、flex布局

+ 如何开启flex布局

  当元素设置了display：flex时，其就成为了伸缩容器，其内的元素无论块、行内块、行内元素都会成为一种新的“块”元素，这种块元素的布局会根据伸缩容器的属性而变动，请注意：在主轴方向上是默认是相邻排列，侧轴开启换行后，每行平均排列

+ 复合属性

  flex是复合属性，复合了：flex-grow（拉伸比）、flex-shrink（压缩）、flex-basis（基准长度）

  eg：flex：1 1 auto

+ 主轴方向flex-direction（元素都是按主轴方向排列）

  + row：水平从左到右，默认值
  + row-reverse：水平从右到左
  + column：垂直从上到下
  + column-reverse：垂直从下到上

+ 主轴换行方式flex-wrap

  弹性盒子中默认情况下，主轴排列，当元素的总长度超过盒子长度，会要求在主轴方向平分盒子的长度。

  warp：自动换行，当主轴方向要溢出时，自动换行，且此时若侧轴高度足够会流出相等的上下边距，不够则依旧平分

+ 主轴对齐方式justify-content

  + flex-start：第一个元素贴着盒子主轴起始位置边框
  + flex-end：最后一个元素贴着盒子主轴结束位置边框
  + center：居中排列
  + space-around：项目均匀的分布在一行中，项目与项目之间的距离，是项目距边距边缘的两倍
  + space-between：项目均匀的分在一行中，项目与项目之间的距离是相等的，项目距边缘没有距离
  + space-evenly：项目均匀的分在一行中，项目与项目之间的距离和项目距边缘的距离是相等的

+ 侧轴对齐方式

  + 元素只有一行时align-items
    + stretch：默认值，如果伸缩项目没有设置高度，将占满整个容器的高度
    + flex-start：侧轴起始位置
    + flex-end：侧轴终点位置
    + center：侧轴中点位置
    + baseline：伸缩项目的第一行文字的基线对齐
  + 元素有多行时align-content
    + stretch：默认值，不给高度，撑满容器
    + flex-start：
    + flex-end：
    + center：
    + space-between：第一行与最后一行与边框没有距离，其余距离平均分布至伸缩项目之间
    + space-around：伸缩项目之间距离相等，且是项目与边缘距离的2倍
    + space-evenly：完全平分

+ 基准长度flex-basis（基本不用）

+ 伸缩性

  伸时多余平分

  缩时等比缩放

+ 单独对齐align-self



#### 十四、响应式网页

+ 媒体查询

  + 媒体类型

    + all：检测所有设备
    + screen：所有电子屏幕，电脑、手机、平板
    + print：打印机

  + 用法

    > @media  print{
    >
    > ​		样式
    >
    > }

+ 媒体特性（查询宽高）

  + 检测

    宽高属性都类似属性

    > 检测到视口宽度等于800px时，应用如下样式
    >
    > @media（width：800px）{
    >
    > ​		样式
    >
    > }
    >
    > 检测到视口宽度小于等于800时，
    >
    > @media（max-width：800px）{
    >
    > ​		样式
    >
    > }
    >
    > 检测视口宽度大于等于800时
    >
    > @media（min-width：800px）{
    >
    > ​		样式
    >
    > }
    >
    > 检测设备宽高
    >
    > @media（device-width： px）{
    >
    > 
    >
    > }

  + 运算符

    and且、or或、not否定、only肯定

    > @media（min-width：700px）and（max-width：800px）{
    >
    > }
    >
    > @media	screen  and（min-width：700px）and（max-width：800px）{
    >
    > }
    >
    > @media（min-width：700px）or（max-width：800px）{
    >
    > }
    >
    > @media  not  screen{
    >
    > }

#### 十五、BFC

+ BFC可以解决什么问题

  + 元素开启BFC后，其子元素不会再产生margin塌陷问题
  + 元素开启BFC后，自己不会被其他浮动元素所覆盖
  + 元素开启BFC后，就算其子元素浮动，元素自身高度也不会塌陷

+ 如何开启BFC

  用到再说