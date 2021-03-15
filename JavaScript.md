# JavaScript

---

### 一.历史和简介

#### 1.历史

Netscape（网景公司），起源于1995，用于网页中的前端验证。SUN公司介入后，Livescript改名Javascript

微软1996：Jscript，IE浏览器

为保证标准一致，几个公司共同制定标准ECMAScript（埃克玛）简称ES。

不同浏览器厂商对ES标准为不同的实现。实现方式即引擎，V8引擎速度最快

<img src="JavaScript.assets/image-20210217194645794.png" alt="image-20210217194645794" style="zoom:80%;" />

#### 2.组成部分

![image-20210217200639069](JavaScript.assets/image-20210217200639069.png)

ES标准，DOM（如何用Javascript操作网页），BOM（如何用JavaScript操作浏览器）



### 二.ES基础

----

#### 1.注释

----

单行注释：//

多行注释：/*   */

#### 2.大小写

---

严格区分大小写

如果不写分号，浏览器会自动添加

#### 3.空格

---

忽略多个空格

#### 4.字面量和变量

---

字面量：不可改变的值，即常量

变量：可以改变的量

#### 5.变量的声明

---

var关键字声明变量

undefined：未赋值变量的值

声明和赋值同时进行

```javascript
var a=0
```

6.标识符

---

自主命名的称为标识符，如变量名，函数名，属性名

1.可以有字母，数字,  _  ,  $

2.不能以数字开头

3.不能以关键字和保留字符为标识符

<img src="JavaScript.assets/image-20210217193123369.png" alt="image-20210217193123369" style="zoom:80%;" />

#### 6.驼峰命名法

首字母小写，每个单词开头字母大写，其他字母小写

#### 7.数据类型

----

String：字符串

Number：数字类型

Boolean：布尔类型

Undefined：未定义

Object：对象

除了Object是引用数据类型，其余都是基本数据类型



typeof运算符可以检查变量的类型

---

##### 7.1String

----

```javascript
var a="hello"
```

1.使用双引号或者单引号圈起来，但不能混着用

2.引号不能嵌套，但可以再单引号里嵌套双引号

3.在字符串中我们可以使用\ 作为转义字符

```javascript
str="我说：\"今天天气真不错\"";
/*

\"     表示"
\'     表示'
\\     表示\
\n     表示换行
\t     表示制表符


*/
```

##### 7.2 Number

----

整数和浮点数

最大数：

Number.MAX_VALUE    1.79769e+308

超过这个词为Infinity，表示＋无穷大

-infinity表示负无穷

Infinity是字面量，属于Number类型

NAN：Not a number，非数字，但是类型仍然为Number

js的整数运算可以保证精确，但是浮点运算无法保证精度，所以千万不要进行js进行精确度比较高的运算

---

##### 7.3 Boolean

---

只有两个值true和false

主要用于逻辑判断



---

##### 7.4 Null和Undefined

---

null这个值专门用来表示一个空对象

typeof null  == object

用typeof检查一个null值会返回一个object



undefined类型的值只有一个，就是undefined

表示声明但是没有赋值

typeof  undefined 会返回一个undefined



---

##### 7.5 强制类型转换

---

类型转换：一般是其他数据类型转换为string number boolean

###### 7.5.1 转换为String

number->string：

如：3->"3"

方法一：调用被转换类型的toString方法

```javascript
a.toString();
```

不会改变原变量，知惠转换结果返回给或者赋值给另一个值

boolean-.string:

如：true-> "true"

undefined和null无法toString

方法二：调用String（）函数

```javascript
a=123;
b=String(a);
//b="123"
```

实际就是调用toString方法，但是undefined和null无法调用，会直接转换为”null“和”undefined“

---

###### 7.5.2转换为Number

---

string -> number(没有toNumber方法)

方法一：采用Number函数

```javascript
a ="123";
b=Number(a);
//b=123
a ="abc";
b=Number(a);
//b=NaN
```

1.如果为纯数字的字符串会转化为数字，如果字符串有非数字的内容，则返回N

2.如果字符串为一个全是空格或者是空字符串，这转换为0；

boolean->number

1.true转换为1，false转化为0

null->number

1.null转化为0

undefined->number

1.undefined转换为NaN

方法2：专门用来对付字符串

parseInt（）：专门将一个字符串转换为整数

可以把一个字符串的有效的整数内容取出来

```javascript
a ="123aaa";
b=parseInt(a);
//b=123
a ="b213abc";
b=parseInt(a);
//非法
```

paeseFloat（）：专门将一个字符串转换为小数

可以把一个字符串的有效的小数内容取出来

```javascript
a ="123.45aaa";
b=parseInt(a);
//b=123.45
a ="b213.23abc";
b=parseInt(a);
//非法
```

如果对非string类型的变量进行parseInt操作，会先将变量转化为string类型，然后再进行操作

```javascript
a =ture;
b=parseInt(a);
//b=NaN
```

---

###### 7.5.3 转换为其他进制

---

js中如果需要表示16进制的数字，则需要**0x**开头

如果需要表示8进制的数字，需要以**0**开头，（070不等于70）

如果需要表示二进制的数字，需要**以0b开头，但是不是所有的浏览器都支持**

像“070”这种字符串的强制类型转换，有些浏览器会当成8进制进行；

解决方法：可以采用parseInt（a，8）进行选择进制转化方法

---

###### 7.5.4 转换为Boolean

---

number->boolean

方法：调用boolean（）函数

**非0，NaN值，其余都是true，包括infinity**



null->boolean

false



undefined->boolean

false



String->boolean

除了空串都是true



object->boolean

true

#### 8.运算

##### 8.1 操作运算符

typeof：对之后的变量进行类型返回

**typeof的结果以字符串的形式返回 typrof （typeof a）==string**

##### 8.2 算数运算符

+-*/%

但对非number类型的值进行运算的时候，都会转化为number类型后进行计算

任何值和NaN进行运算都是得到NaN

对于true转换为1；

对于字符串进行操作，会进行字符串的拼接，我们可以利用这一特点将任意数据类型转换为string

+“”空字符即可，本质上也是调用toString方法

我们可以利用算数运算符  - * / 简单的转换为number类型

##### 8.3 逻辑运算符

！：非

&&：与

||：或

对任意数据类型做两次！（取反）运算，可将其转换为布尔值

##### 8.4 相等运算符

== 运算符 ，比较两个值的时候，如果两个值的类型不同会进行类型转换后，然后再比较，大部分情况下转换为数字

<img src="JavaScript.assets/image-20210218110035546.png" alt="image-20210218110035546" style="zoom:80%;" />

！=运算符 ，比较两个值的时候，如果两个值的类型不同会进行类型转换后，然后再比较，大部分情况下转换为数字

===全等符，用来判断两个值是否全等，但不会进行类型转换

<img src="JavaScript.assets/image-20210218112626371.png" alt="image-20210218112626371" style="zoom:80%;" />

！==不全等，用来判断两个值是否不全等，但不会进行类型转换

##### 8.5 条件运算符

<img src="JavaScript.assets/image-20210218121721108.png" alt="image-20210218121721108" style="zoom:80%;" />

如果条件表达式结果是非Boolean值，会先转换为boolean值后在进行判断

##### 8.6 逗号运算符

， 运算符可以分割多个语句，一般用于声明多个变量时使用

8.7 运算符优先级

<img src="JavaScript.assets/image-20210218152743852.png" alt="image-20210218152743852" style="zoom:67%;" />

#### 9. 代码块

用{}括起来

<img src="JavaScript.assets/image-20210218155222259.png" alt="image-20210218155222259" style="zoom:67%;" />

js的代码块只有分组的作用。没有其他的用途

#### 10.对象

基本数据类型：单一。值和值之间没有联系，相互独立

引用数据类型：

##### 10.1.内建对像

-使用ES标准中定义的对象

-如Math String Number Boolean Function

##### 10.2.宿主对象

-JS运行环境提供的对象

-如BOM DOM

##### 10.3.自定义对象

-开发人员自己提供的对象



##### 10.4.创建对象

```javascript
var obj = new Object（）；//new关键字调用的函数，是构造函数constructor
//添加属性
//对象.属性=属性值
//读取属性：对象.属性,读取没有的属性会返回undefined
//删除属性 delete 对象.属性名
```

![image-20210218160635380](JavaScript.assets/image-20210218160635380.png)



##### 10.5.in运算符

**![image-20210218160828262](JavaScript.assets/image-20210218160828262.png)**

判断是否有某个属性

##### 10.6 对象字面量

用对象字面量创建一个对象

```javascript
var obj ={};
var obj1={name:"sds",
          age:12
         };//可以创建对象时候直接设置指定对象的属性
//名和值之间用:连接，不能用等号  多个名值用 , 连接，最后一个不能用逗号
```

##### 10.7 函数

函数也是一个对象

函数可以封装一些功能

创建一个函数对象:

```javascript
var fun =new function();
//可以将要封装的代码以字符串的形式传给构造函数
var fun1 =new function("console.log('这是一个函数')");//实际开发时不经常使用
//封装在函数的代码不会立即执行
//当调用函数时，函数中封装的代码会按顺序执行


//使用函数声明创建一个函数
function fun2 ([形参1，2，3.]){
//语句;
}
var fun2=function([形参1，2，3]){
    //语句;
};//匿名函数赋值给变量
//调用函数的时候解析器不会检查实参的类型和数量，多余的实参不会被赋值
//如果实参的数量少于调用的最少数量，类型将会是undefined
//返回return，不返回默认返回一个undefined，可以是任意的数据类型
//return直接结束当前函数
```

##### 10.8 参数调用

实参可以是任意类型，也可以是一个对象，也可以是一个函数

当我们的参数过多的时候，我们可以把参数封装到一个对象中，然后通过对象传递

fun（）：调用函数

fun：函数对象

##### 10.9 立即执行函数

```javascript
(function(){
    alert("我是一个匿名函数");
})(参数1，参数2);
//函数定义完，立即使用立即被调用，只会执行一次

```

函数也可以是对象的属性，我们称为对象的方法，但只是名称上的区别

##### 10.10 枚举对象中的属性

```javascript
//采用for in 语句
for(var n in obj){
    console.log(n);//属性名
    console.log(obj[n]);//属性值
}
```

##### 10.11 作用域

1.全局作用域

-直接写在script的JS代码，都在全局作用域中

-全局作用域在页面打开是创建，页面关闭时销毁

-全局作用域中有一个全局对象window

---它代表的是一个浏览器的窗口，浏览器创建时我们可以直接使用

-全局作用域中创建的变量都会作为window对象的属性保存，创建的函数都会作为window的方法保存

```javascript
var a= 10;
console.log(window.a);

```

2.函数的作用域

函数调用时开启，执行完毕后作用域销毁

每调用一次，创建一个新的作用域，他们之间相互独立

函数作用域可以访问到全局，反之不行

函数作用域操作一个变量的时候，优先采取函数的作用域，如果没找到再向上找全局的作用域，如果要访问全局变量，可以调用window对象

在函数中不用var声明的变量都是全局变量的使用，设置全局变量

##### 10.12 this指针

解析器即浏览器

解析器调用函数的时候都会向函数内部传递一个隐含的参数

这个隐含的参数就是this

this指向的是一个对象，根据函数调用方式的不同，this会指向不同的对象

调用方式1

以函数的调，this永远指向window

以方法的形式调用时，ths指向调用方法的对象

##### 10.13 构造函数

<img src="JavaScript.assets/image-20210218174914845.png" alt="image-20210218174914845" style="zoom:80%;" />

instanceof 实例 可以检查一个对象是否为一个类的实例

```javascript
对象 instanceof 构造函数
//如果是返回true，否则返回false
```

所有对象都是Object类的后代

每个实例的方法都是独立的，唯一的，需要共享，可以让该方法再全局作用域中定义，可以减少空间

但是函数再定义在全局作用域，会污染全局作用域的命名空间，而且也不安全

##### 10.14 原型对象

原型prototype

我们创建的每一个函数对象，解析器都会添加一个属性prototype

这个属性对应一个对象，这个对象就是原型对象

如果函数作为普通函数使用的时候，prototype没有任何作用

当函数以构造函数的形式调用，所创建的对象都有一个隐含属性

我们可以通过

```javascript
_proto_
```

来访问属性

原型对象就相当于一个公共区域，统一到原型对象

 当我们访问一个对象的一个属性或者方法时，它会现在对象自身中寻找，如果有则直接使用，如果没有则会再原型对象中去寻找，如果找到则直接使用

![image-20210218183614751](JavaScript.assets/image-20210218183614751.png)

用in检查对象是否有属性，如果原型对象有也会返回true

可以使用hasOwnProperty（）检查是否自身对象中有属性

该方法在原型对象的原型对象中；即Object对象（祖宗类）

原型对象最多两层

##### 10.15 toString方法

当我们直接在页面打印一个对象的时候，实际上时输出对象的toString（）方法的返回值

![image-20210218184655602](JavaScript.assets/image-20210218184655602.png)

---

#### 11.垃圾回收

----

JS的垃圾回收机制：

当一个对象没有任何变量进行引用，此时该对象为垃圾，会占用大量内存

JS有自动的垃圾回收机制，我们不能也不需要进行垃圾回收

我们需要做的只是将不需要的对象设置为null就行

#### 12.数组

数组（Array）也是一种对象

不同的是数组是采用数字作为索引来操作元素

创建数组对象

```javascript
var arr = new array();
//语法 数组[索引数字]=值，如果越界则返回undefined不会报错
arr.length();//获取数组的长度
//对于连续数组返回初始化的数目，若非连续则获取到最大索引数+1
//我们可以修改length，如果修改的length大于原长度会空出来
//如果我们设置的length小于原长度，原数组的部分数据会被删除
arr[arr.length]=1;//可以一直给数组最后一个位置添加元素
arr1 =new Array(10)//创建一个长度为10的数组
arr2 =new Array(10,20)//创建一个数组为[10,20]
```

数组的元素可以是任意的数据类型，也可以是对象,也可以是数组（即为二维数组）

---

数组的属性：constructor，length，prototype

数组的方法：

```javascript
数组名.push(新元素1，新元素2.....);  //末尾添加一个或多个元素，并返回新的数组长度
数组名.pop();                       //末尾删除元素，并返回删除的元素
数组名.unshift(新元素1，新元素2.....);//开头添加一个或多个元素，并返回新的数组长度
数组名.shift();                      //开头删除一个元素，并返回删除的元素
```

数组的遍历

```javascript
for(var i=0;i<arr.length;i++){
    console.log(arr[i]);
}
```

forEach方法

JS提供forEach方法进行遍历(IE8以下不支持)

```javascript
arr.forEach(function(){
//函数语句
});
//forEach需要一个函数作为参数
//数组元素有几个，函数就会执行几次，每次执行时，浏览器都会将遍历的元素作为实参传进来
，我们可以定义形参，来读取这些内容
```

![image-20210218191942928](JavaScript.assets/image-20210218191942928.png)

slice方法

```javascript
//从数组返回选定的元素
//参数：
/*
*1.截取开始的位置索引，包括开始索引
*2.截取结束的位置的索引，不包含结束索引
*  第二个参数可以省略不写，此时会截取从开始索引往后的所有元素
*如果传递一个负值，则从后往前计算
*/
arr.slice(1,2);//第2个到第三个元素返回
```

splice方法

```javascript
//可以删除和添加数组的指定元素
//splice()会影响原数组，并将删除的元素作为返回值返回
//参数
//1.第一个：表示开始位置的索引
//2.第二个，表示删除的数量
//3.第三个及以后：这些元素会自动插入开始位置索引的前面
```

<img src="JavaScript.assets/image-20210218192906090.png" alt="image-20210218192906090" style="zoom:80%;" />

concat方法：连接两个或者多个数组，并返回新的数组，但不会对原数组产生影响

join方法：可以将数组转换为一个字符串，不会对原数组产生影响，数据类型为String

可以选定一个字符串作为参数，这个字符可以作为数组元素的连接符，不指定则默认为逗号

<img src="JavaScript.assets/image-20210218193251648.png" alt="image-20210218193251648" style="zoom:80%;" />

reverse方法：用来反转数组，会影响原数组

sort方法：可以对数组的元素进行排序，会影响原数组，默认按照unicode编码进行排序

#### 13.函数对象（其他）

函数名.call（），调用函数

函数名.apply（）,调用函数

在调用这两个方法时，可以将第一个对象指定为第一个参数

此时这个对象将会称为函数执行时的this，参数是谁，this就是谁

call方法可以在实参在对象之后依次传递

```javascript
函数.call（obj，实参1，实参2）
apply方法需要将实参封装到一个数组进行统一传递
```

arguments 封装实参的对象

arguments是类数组对象，但不是数组，可以用索引进行操作

```
arguments.callee：对应当前执行的函数对象
```

Data对象，会直接封装为当前代码执行的时间

格式：

<img src="JavaScript.assets/image-20210218195235822.png" alt="image-20210218195235822" style="zoom:67%;" />

包装类

<img src="JavaScript.assets/image-20210218200636119.png" alt="image-20210218200636119" style="zoom:80%;" />

![image-20210218200921601](JavaScript.assets/image-20210218200921601.png)

#### 14.正则表达式

正则表达式用于定义一些字符串的规则

计算机可以根据正则表达式来检查一个字符串是否符合规则

获取字符串中符合规则的内容提取出来

```java
var reg =new RegExp("a");//检查一个字符串是否含有"a"
console.log(typeof reg);
//var 变量 = new RegExp(“正则表达式”，“撇配模式”)
//正则表达式的方法：
//  test（）方法检查一个字符串是否符合正则表达式的规则

```

![image-20210218201839898](JavaScript.assets/image-20210218201839898.png)

![image-20210218202118388](JavaScript.assets/image-20210218202118388.png)

![image-20210218202230800](JavaScript.assets/image-20210218202230800.png)

![image-20210218202256470](JavaScript.assets/image-20210218202256470.png)

![image-20210218202410593](JavaScript.assets/image-20210218202410593.png)

#### 15.DOM

DOM：document object model 文档对象模型

<img src="JavaScript.assets/image-20210218202615804.png" alt="image-20210218202615804" style="zoom:80%;" />p

p91

### 三. Node.js

---

1.命令行常用

dir：列出当前目录所有文件

cd 地址（Tab可以补全）：进入需要进入的目录

.  :当前目录

..  :上一级目录

cd ..    :返回上一级目录

md 文件夹名字 ：新建文件夹 make docment

rd  目录 ：删除文件夹 remove document

环境变量（windows系统变量）：随时可以进入当前文件夹

系统属性 -环境变量-用户变量-path

2.进程和线程

进程

-提供程序的必备环境，类似于工厂的车间

线程

-计算机的最小计算单位，负责执行程序，类似工厂的工人



单线程

js单线程

多线程

主流程序多线程

node。js在服务器运行

模块化

程序分为小程序

一个js就是一个模块

引入模块

require（“”）； 用。/进行写相对路径

每一个js代码都是独立运行在一个函数中

exports +暴露方法和属性

![image-20210222150315866](JavaScript.assets/image-20210222150315866.png)

![image-20210222150452069](JavaScript.assets/image-20210222150452069.png)

exports和module.exports

![image-20210222152744015](JavaScript.assets/image-20210222152744015.png)

<img src="JavaScript.assets/image-20210222154000415.png" alt="image-20210222154000415" style="zoom:80%;" />

<img src="JavaScript.assets/image-20210222154336900.png" alt="image-20210222154336900" style="zoom:67%;" />

npm 命令

![image-20210222160919268](JavaScript.assets/image-20210222160919268.png)

node搜索包的流程
，会优先搜寻node-module文件夹寻找，没有就返回上一级目录的nodemodule寻找

![image-20210222163159448](JavaScript.assets/image-20210222163159448.png)

unicode中文占3个字节

万国码 2个字节

![image-20210222171117663](JavaScript.assets/image-20210222171117663.png)

![image-20210222181257287](JavaScript.assets/image-20210222181257287.png)

jsx规则

![image-20210222224635952](JavaScript.assets/image-20210222224635952.png)

![image-20210223162009740](JavaScript.assets/image-20210223162009740.png)

![image-20210223182108281](JavaScript.assets/image-20210223182108281.png)

![image-20210223185017549](JavaScript.assets/image-20210223185017549.png)

![image-20210226220430897](JavaScript.assets/image-20210226220430897.png)



变量的分类：

方式一：按照数据类型

<img src="JavaScript.assets/image-20210208140720731.png" alt="image-20210208140720731" style="zoom:80%;" />

方式二：	

![image-20210208141057108](JavaScript.assets/image-20210208141057108.png)

### LESS

![image-20210216095340965](JavaScript.assets/image-20210216095340965.png)

无形参的

![image-20210216094959180](JavaScript.assets/image-20210216094959180.png)

命名参数 

匹配参数第一个可以是匹配符；



### Git

git操作总结

<img src="JavaScript.assets/image-20210216181928971.png" alt="image-20210216181928971" style="zoom: 50%;" />

**1.状态查看操作**

git status

查看工作区和暂存区的状态

**2.添加操作**

git add<文件名>

**3.查看历史记录**

git log

完整显示

git log --pretty=oneline

用一行显示

git log --oneline:只显示过去

更简洁的形式显示（缩短哈希值）

多屏显示操作： 

空格向下翻页

b向上翻页

q 退出

4.前进后退

tail -n 3文件名（打开对应文件并展示最后三行的内容）

git reflog

HEAD@{移动到当前版本需要多少步}

git reset--hard(索引值：哈希值)

 使用^符号：只能后退 git reset --hard HEAD^^^（退3步）

使用~符号：只能后退  git reset --hard HEAD~n（退n步）



reset命令的三个参数对比

--soft：仅在本地库移动HEAD指针

--mixed：再本地库移动HEAD指针和重置暂存区

--hard ：三区全部移动到相应的指针上

删除文件

rm 文件名

git diff 比较两个文件的不同

git 分支

![image-20210216194026669](JavaScript.assets/image-20210216194026669.png)

<img src="JavaScript.assets/image-20210216194132993.png" alt="image-20210216194132993" style="zoom:80%;" />





