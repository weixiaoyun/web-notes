# JavaScript高级

## 一、数据类型

### 1.分类

* 基本(值)类型
  * Number: 任意数值
  * String: 任意文本
  * Boolean: true/false
  * undefined: undefined
  * null: null
* 对象(引用)类型
  * Object: 任意对象
  * Array: 特别的对象类型(下标/内部数据有序)
  * Function: 特别的对象类型(可执行)

### 2.判断

* typeof:
  * 可以区别: 数值, 字符串, 布尔值, undefined, function
  * 不能区别: null与对象, 一般对象与数组
* instanceof：专门用来判断对象数据的类型: Object, Array与Function
* ===：可以判断: undefined和null

#### 基本类型

```
var a
console.log(a, typeof a, a===undefined) // undefined 'undefined' true
console.log(a===typeof a) // false
```

```
a = 3
console.log(typeof a === 'number') //true
a = 'wxy'
console.log(typeof a === 'string') //true
a = true
console.log(typeof a === 'boolean') //true
```

```
a = null
console.log(a===null) // true
console.log(typeof a) // 'object'
```

#### 对象类型

```
var b1 = {
  b2: [2, 'abc', console.log],
  b3: function () {
    console.log('b3()')
  }
}
console.log(b1 instanceof Object, typeof b1) // true 'object'
console.log(b1.b2 instanceof Array, typeof b1.b2) // true 'object'
console.log(b1.b3 instanceof Function, typeof b1.b3) // true 'function'

console.log(typeof b1.b2[2]) // 'function'
console.log(b1.b2[2]('abc')) // 'abc' undefined
```

### 3.问题

1. undefined与null的区别?

     * undefined代表没有赋值
     * null代表赋值了, 只是值为null

       ```
       var a1
       var a2 = null
       console.log(a1, a2) //undefined null
       ```
2. 什么时候给变量赋值为null呢?

     * var a = null //a将指向一个对象, 但对象此时还没有确定
     * a = null //让a指向的对象成为垃圾对象

       ```
         //初始
       var a3 = null
         //中间
       var name = 'Tom'
       var age = 12
       a3 = {
         name: name,
         age: age
       }
         //结束
       a3 = null
       ```
3. 严格区别变量类型与数据类型?

   * js的变量本身是没有类型的, 变量的类型实际上是变量内存中数据的类型
   * 变量类型:
       * 基本类型: 保存基本类型数据的变量
       * 引用类型: 保存对象地址值的变量

     * 数据对象
       * 基本类型
       * 对象类型

## 二、数据变量、内存

### 1.数据

  * 存储于内存中代表特定信息的东西, 本质就是0101二进制
  * 具有可读和可传递的基本特性
  * 万物(一切)皆数据, 函数也是数据
  * 程序中所有操作的目标: 数据
    * 算术运算
    * 逻辑运算
    * 赋值
    * 调用函数传参
    ...

### 2.内存

  * 内存条通电后产生的存储空间(临时的)
  * 产生和死亡: 内存条(集成电路板)==>通电==>产生一定容量的存储空间==>存储各种数据==>断电==>内存全部消失
  * 内存的空间是临时的, 而硬盘的空间是持久的
  * 一块内存包含2个数据
    * 内部存储的数据(一般数据/地址数据)
    * 内存地址值数据
  * 内存分类
    * 栈: 全局变量, 局部变量 (空间较小)
    * 堆: 对象 (空间较大)

### 3.变量

  * 值可以变化的量, 由变量名与变量值组成
  * 一个变量对应一块小内存, 变量名用来查找到内存, 变量值就是内存中保存的内容

### 4.内存,数据, 变量三者之间的关系

  * 内存是一个容器, 用来存储程序运行需要操作的数据
  * 变量是内存的标识, 我们通过变量找到对应的内存, 进而操作(读/写)内存中的数据



2个引用变量指向同一个对象, 通过一个变量修改对象内部数据, 另一个变量看到的是修改之后的数据：

```
var obj1 = {}
var obj2 = obj1
obj2.name = 'Tom'
console.log(obj1.name) //Tom
function f1(obj) {
  obj.age = 12
}
f1(obj2)
console.log(obj1.age) //12
```

2个引用变量指向同一个对象, 让其中一个引用变量指向另一个对象, 另一引用变量依然指向前一个对象：

```
var obj3 = {name: 'Tom'}
var obj4 = obj3
obj3 = {name: 'JACK'} //obj3指向的是另一个地址值
console.log(obj4.name) //Tom
function f2(obj) {
  obj = {name: 'Bob'}
}
f2(obj4)
console.log(obj4.name) //Tom
```

### 5.问题

1.var a = xxx, a内存中到底保存的是什么?

  * xxx是基本数据, 保存的就是这个数据
  * xxx是对象, 保存的是对象的地址值
  * xxx是一个变量, 保存的xxx的内存内容(可能是基本数据, 也可能是地址值)



2.在js调用函数时传递变量参数时, 是值传递还是引用传递

  * 理解1：只有值传递, 没有引用传递, 传递的都是变量的值, 只是这个值可能是基本数据, 也可能是地址(引用)数据（都是值(基本/地址值)传递）
  * 理解2：如果后一种看成是引用传递, 那就值传递和引用传递都可以有（可能是值传递, 也可能是引用传递(地址值)）

```
function f(a) {
  console.log(a)  //4
}
var n = 4
f(n) //传递的是n的值 --->值传递

function f2(a) {
  a.name = 'wxy'
}
n = {}
f2(n) // 传递的是n指向的对象 ---> 引用传递   ???
console.log(n.name) //wxy
```



3.JS引擎如何管理内存：

- 内存生命周期

    * 分配小内存空间, 得到它的使用权
    * 存储数据, 可以反复进行操作
    * 释放小内存空间

- 释放内存

    * 局部变量: 函数执行完自动释放

    * 对象: 成为垃圾对象==>垃圾回收器回收

## 三、对象

### 对象

  * 多个数据的封装体
  * 用来保存多个数据的容器
  * 一个对象代表现实中的一个事物

为什么要用对象?

  * 统一管理多个数据

对象的组成

  * 属性: 属性名(字符串)和属性值(任意)组成
  * 方法: 一种特别的属性(属性值是函数)

如何访问对象内部数据?

  * .属性名: 编码简单, 有时不能用
  * ['属性名']: 编码麻烦, 能通用

```
var p = {
  name: 'Tom',
  age: 12,
  setName: function (name) {
    this.name = name
  },
  setAge: function (age) {
    this.age = age
  }
}

p.setName('Bob')
p['setAge'](23)
console.log(p.name, p['age']) //Bob 23
```

**问题：**什么时候必须使用['属性名']的方式?

1. 属性名包含特殊字符: - 空格
2. 属性名不确定

```
var p = {}
//1. 给p对象添加一个属性: content type: text/json
// p.content-type = 'text/json' //不能用
p['content-type'] = 'text/json'
console.log(p['content-type']) //text/json

//2. 属性名不确定
var propName = 'myAge'
var value = 18
// p.propName = value //不能用
p[propName] = value
console.log(p[propName]) //18
```

## 四、函数

### 1.函数

  * 实现特定功能的n条语句的封装体
  * 只有函数是可以执行的, 其它类型的数据不能执行

为什么要用函数?

  * 提高代码复用
  * 便于阅读交流

如何定义函数?

  * 函数声明
  * 表达式

如何调用(执行)函数?

  * test(): 直接调用
  * obj.test(): 通过对象调用
  * new test(): new调用
  * test.call/apply(obj): 临时让test成为obj的方法进行调用

```
function showInfo (age) {
  if(age<18) {
    console.log('未成年, 再等等!')
  } else if(age>60) {
    console.log('算了吧!')
  } else {
    console.log('刚好!')
  }
}

showInfo(17) //未成年, 再等等!
showInfo(20) //刚好!
showInfo(65) //算了吧!

function fn1 () { //函数声明
  console.log('fn1()')
}
var fn2 = function () { //表达式
  console.log('fn2()')
}

fn1() //fn1()
fn2() //fn2()

var obj = {}
function test2 () {
  this.name = 'wxy'
}
// obj.test2()  不能直接, 根本就没有
test2.call(obj) // obj.test2()   // 可以让一个函数成为指定任意对象的方法进行调用
console.log(obj.name) //wxy
```

### 2.回调函数

什么函数是回调函数?

- 你定义的
- 你没有调
- 但最终它执行了(在某个时刻或某个条件下)

常见的回调函数?

  * dom事件回调函数 ==>发生事件的dom元素
  * 定时器回调函数 ===>window

  * ajax请求回调函数
  * 生命周期回调函数

```
document.getElementById('btn').onclick = function () { // dom事件回调函数
  alert(this.innerHTML)
}

//定时器
  // 超时定时器
  // 循环定时器
setTimeout(function () { // 定时器回调函数

  alert('到点了'+this)
}, 2000)
```

### 3.立即执行函数（IIFE）

全称: Immediately-Invoked Function Expression

作用：

  * 隐藏实现
  * 不会污染外部(全局)命名空间
  * 用它来编码js模块

```
(function () { //匿名函数自调用
  var a = 3
  console.log(a + 3) //6
})()
var a = 4
console.log(a) //4

;(function () {
  var a = 1
  function test () {
    console.log(++a) //2
  }
  window.$ = function () { // 向外暴露一个全局函数
    return {
      test: test
    }
  }
})()

console.log($()) //{test: ƒ}
$().test() // 1. $是一个函数 2. $执行后返回的是一个对象
```

### 4.函数中的this

this是什么?

  * 任何函数本质上都是通过某个对象来调用的,如果没有直接指定就是window
  * 所有函数内部都有一个变量this
  * 它的值是调用函数的当前对象

如何确定this的值?

  * test(): window
  * p.test(): p
  * new test(): 新创建的对象
  * p.call(obj): obj

```
function Person(color) {
  console.log(this)
  this.color = color;
  this.getColor = function () {
    console.log(this)
    return this.color;
  };
  this.setColor = function (color) {
    console.log(this)
    this.color = color;
  };
}

Person("red"); //this是谁? window

var p = new Person("yello"); //this是谁? p

p.getColor(); //this是谁? p

var obj = {};
p.setColor.call(obj, "black"); //this是谁? obj

var test = p.setColor;
test(); //this是谁? window

function fun1() {
  function fun2() {
    console.log(this);
  }

  fun2(); //this是谁? window
}
fun1();
```

## 五、函数高级

### 1.原型与原型链

#### 原型（prototype）

1. 函数的prototype属性
  * 每个函数都有一个prototype属性, 它默认指向一个Object空对象(即称为: 原型对象)
  * 原型对象中有一个属性constructor, 它指向函数对象

![原型链分析](https://raw.githubusercontent.com/weixiaoyun/Images/js%E9%AB%98%E7%BA%A7/%E5%8E%9F%E5%9E%8B%E9%93%BE%E5%88%86%E6%9E%90.png)

2. 给原型对象添加属性(一般都是方法)

  * 作用: 函数的所有实例对象自动拥有原型中的属性(方法)

```
// 每个函数都有一个prototype属性, 它默认指向一个Object空对象(即称为: 原型对象)
console.log(Date.prototype, typeof Date.prototype) //Object 'object'
function Fun () {//alt + shift +r(重命名rename)

}
console.log(Fun.prototype)  //Object 默认指向一个Object空对象(没有我们的属性)

// 原型对象中有一个属性constructor, 它指向函数对象
console.log(Date.prototype.constructor===Date) //true
console.log(Fun.prototype.constructor===Fun)  //true

//给原型对象添加属性(一般是方法) ===>实例对象可以访问
Fun.prototype.test = function () {
  console.log('test()')
}
var fun = new Fun()
fun.test()
```

#### 显示原型与隐式原型

1. 每个函数function都有一个prototype，即显式原型(属性)

2. 每个实例对象都有一个__proto__，可称为隐式原型(属性)

3. 对象的隐式原型的值为其对应构造函数的显式原型的值

4. 内存结构(图)

   ![显式原型与隐式原型](https://raw.githubusercontent.com/weixiaoyun/Images/js%E9%AB%98%E7%BA%A7/%E6%98%BE%E5%BC%8F%E5%8E%9F%E5%9E%8B%E4%B8%8E%E9%9A%90%E5%BC%8F%E5%8E%9F%E5%9E%8B.png)

5. 总结:
  * 函数的prototype属性: 在定义函数时自动添加的, 默认值是一个空Object对象
  * 对象的__proto__属性: 创建对象时自动添加的, 默认值为构造函数的prototype属性值
  * 程序员能直接操作显式原型, 但不能直接操作隐式原型(ES6之前)

```
//定义构造函数
function Fn() {   // 内部语句: this.prototype = {}

}
// 1. 每个函数function都有一个prototype，即显式原型属性, 默认指向一个空的Object对象
console.log(Fn.prototype) //{constructor: ƒ}
// 2. 每个实例对象都有一个__proto__，可称为隐式原型
//创建实例对象
var fn = new Fn()  // 内部语句: this.__proto__ = Fn.prototype
console.log(fn.__proto__) //{constructor: ƒ}
// 3. 对象的隐式原型的值为其对应构造函数的显式原型的值
console.log(Fn.prototype===fn.__proto__) // true
//给原型添加方法
Fn.prototype.test = function () {
  console.log('test()')
}
//通过实例调用原型的方法
fn.test()
```

#### 原型链

* 访问一个对象的属性时，
  * 先在自身属性中查找，找到返回
  * 如果没有, 再沿着__proto__这条链向上查找, 找到返回
  * 如果最终没找到, 返回undefined
* 别名: 隐式原型链
* 作用: 查找对象的属性(方法)

```
console.log(Object.prototype.__proto__) //null
function Fn() {
  this.test1 = function () {
    console.log('test1()')
  }
}
console.log(Fn.prototype) //{constructor: ƒ}
Fn.prototype.test2 = function () {
  console.log('test2()')
}

var fn = new Fn()

fn.test1()
fn.test2()
console.log(fn.toString()) //[object Object]
```

函数的显示原型指向的对象默认是空Object实例对象(但Object不满足)：

```
console.log(Fn.prototype instanceof Object) // true
console.log(Object.prototype instanceof Object) // false
console.log(Function.prototype instanceof Object) // true
```

所有函数都是Function的实例(包含Function)：

```
console.log(Function.__proto__===Function.prototype) //true
```

Object的原型对象是原型链尽头：

```
console.log(Object.prototype.__proto__) // null
```



- 读取对象的属性值时: 会自动到原型链中查找
- 设置对象的属性值时: 不会查找原型链, 如果当前对象中没有此属性, 直接添加此属性并设置其值
- 方法一般定义在原型中, 属性一般通过构造函数定义在对象本身上

```
function Fn() {

}
Fn.prototype.a = 'xxx'
var fn1 = new Fn()
console.log(fn1.a, fn1) //xxx Fn {}

var fn2 = new Fn()
fn2.a = 'yyy'
console.log(fn1.a, fn2.a, fn2) //xxx yyy Fn {a: 'yyy'}

function Person(name, age) {
  this.name = name
  this.age = age
}
Person.prototype.setName = function (name) {
  this.name = name
}
var p1 = new Person('Tom', 12)
p1.setName('Bob')
console.log(p1) //Person {name: 'Bob', age: 12}

var p2 = new Person('Jack', 12)
p2.setName('Cat')
console.log(p2) //Person {name: 'Cat', age: 12}
console.log(p1.__proto__===p2.__proto__) // true
```

#### instanceof

instanceof是如何判断的?

  * 表达式: A instanceof B
  * 如果B函数的显式原型对象在A对象的原型链上, 返回true, 否则返回false

Function是通过new自己产生的实例

```
function Foo() {  }
var f1 = new Foo()
console.log(f1 instanceof Foo) // true
console.log(f1 instanceof Object) // true
```

```
console.log(Object instanceof Function) // true
console.log(Object instanceof Object) // true
console.log(Function instanceof Function) // true
console.log(Function instanceof Object) // true

function Foo() {}
console.log(Object instanceof  Foo) // false
```

#### 面试题

```
function A () {

}
A.prototype.n = 1

var b = new A()

A.prototype = {
  n: 2,
  m: 3
}

var c = new A()
console.log(b.n, b.m, c.n, c.m) //1 undefined 2 3
```

```
function F (){}
Object.prototype.a = function(){
  console.log('a()')
}
Function.prototype.b = function(){
  console.log('b()')
}

var f = new F()
f.a() //a()
// f.b()
F.a() //a()
F.b() //b()
console.log(f) //F {}
console.log(Object.prototype) //{a: ƒ, constructor: ƒ, __defineGetter__: ƒ, __defineSetter__: ƒ, hasOwnProperty: ƒ, …}
console.log(Function.prototype) //ƒ () { [native code] }
console.log(Function.prototype.b) /*ƒ (){
                                          console.log('b()')
                                          }*/
```

### 2.执行上下文与执行上下文栈

#### 函数提升与变量提升

变量声明提升

  * 通过var定义(声明)的变量, 在定义语句之前就可以访问到
  * 值: undefined

函数声明提升

  * 通过function声明的函数, 在之前就可以直接调用
  * 值: 函数定义(对象)

函数提升优先级高于变量提升

```
var a = 3
function fn () {
  console.log(a)
  var a = 4
}
fn() //undefined
```

相当于：

```
var a = 3
function fn () {
  var a
  console.log(a)
  a = 4
}
fn() //undefined
```

```
console.log(b) //undefined  变量提升
fn2() //可调用  函数提升
// fn3() //不能  变量提升

var b = 3
function fn2() {
  console.log('fn2()')
}

var fn3 = function () {
  console.log('fn3()')
}
```

#### 执行上下文

代码分类(位置)

  * 全局代码
  * 函数(局部)代码

全局执行上下文

  * 在执行全局代码前将window确定为全局执行上下文
  * 对全局数据进行预处理
    * var定义的全局变量==>undefined, 添加为window的属性
    * function声明的全局函数==>赋值(fun), 添加为window的方法
    * this==>赋值(window)
  * 开始执行全局代码

函数执行上下文

  * 在调用函数, 准备执行函数体之前, 创建对应的函数执行上下文对象(虚拟的, 存在于栈中)
  * 对局部数据进行预处理
    * 形参变量==>赋值(实参)==>添加为执行上下文的属性
    * arguments==>赋值(实参列表), 添加为执行上下文的属性
    * var定义的局部变量==>undefined, 添加为执行上下文的属性
    * function声明的函数 ==>赋值(fun), 添加为执行上下文的方法
    * this==>赋值(调用函数的对象)
  * 开始执行函数体代码

```
console.log(a1, window.a1) //undefined undefined
window.a2()
console.log(this) //Window

var a1 = 3
function a2() {
  console.log('a2()')
}
console.log(a1) //3
```

#### 执行上下文栈

1. 在全局代码执行前, JS引擎就会创建一个栈来存储管理所有的执行上下文对象
2. 在全局执行上下文(window)确定后, 将其添加到栈中(压栈)
3. 在函数执行上下文创建后, 将其添加到栈中(压栈)
4. 在当前函数执行完后,将栈顶的对象移除(出栈)
5. 当所有的代码执行完后, 栈中只剩下window

```
var a = 10
var bar = function (x) {
  var b = 5
  foo(x + b)
}
var foo = function (y) {
  var c = 5
  console.log(a + c + y) // 10 + 5 + 15
}
bar(10) //30
```



```
console.log('gb: '+ i)
var i = 1
foo(1)
function foo(i) {
  if (i == 4) {
    return
  }
  console.log('fb:' + i)
  foo(i + 1) //递归调用: 在函数内部调用自己
  console.log('fe:' + i)
}
console.log('ge: ' + i)
```

依次输出：

```
gb: undefined
fb: 1
fb: 2
fb: 3
fe: 3
fe: 2
fe: 1
ge: 1
```

整个过程中产生了5个执行上下文

#### 面试题

先执行变量提升, 再执行函数提升（函数提升优先级高于变量提升）

```
function a() {}
var a
console.log(typeof a) // 'function'
```

```
if (!(b in window)) {
  var b = 1
}
console.log(b) // undefined
```

该处未把c识别为一个函数

```
var c = 1
function c(c) {
  console.log(c)
  var c = 3
}
c(2) // 报错 Uncaught TypeError: c is not a function
```

```
// var c = 1
function c(c) {
  console.log(c)
  var c = 3
}
c(2) // 2
```

### 3.作用域与作用域链

#### 作用域

理解

  * 就是一块"地盘", 一个代码段所在的区域
  * 它是静态的(相对于上下文对象), 在编写代码时就确定了

分类

  * 全局作用域
  * 函数作用域
  * 块作用域(ES6)

作用

  * 隔离变量，不同作用域下同名变量不会有冲突

```
var a = 10,
  b = 20
function fn(x) {
  var a = 100,
    c = 300;
  console.log('fn()', a, b, c, x)
  function bar(x) {
    var a = 1000,
      d = 400
    console.log('bar()', a, b, c, d, x)
  }

  bar(100)
  bar(200)
}
fn(10)
// fn() 100 20 300 10
// bar() 1000 20 300 400 100
// bar() 1000 20 300 400 200
```

#### 作用域与执行上下文

区别1

  * 全局作用域之外，每个函数都会创建自己的作用域，作用域在函数定义时就已经确定了。而不是在函数调用时
  * 全局执行上下文环境是在全局作用域确定之后, js代码马上执行之前创建
  * 函数执行上下文是在调用函数时, 函数体代码执行之前创建

区别2

  * 作用域是静态的, 只要函数定义好了就一直存在, 且不会再变化
  * 执行上下文是动态的, 调用函数时创建, 函数调用结束时就会自动释放

联系

  * 执行上下文(对象)是从属于所在的作用域
  * 全局上下文环境==>全局作用域
  * 函数上下文环境==>对应的函数使用域

#### 作用域链

理解

  * 多个上下级关系的作用域形成的链, 它的方向是从下向上的(从内到外)
  * 查找变量时就是沿着作用域链来查找的

查找一个变量的查找规则

  1. 在当前作用域下的执行上下文中查找对应的属性, 如果有直接返回, 否则进入2
  2. 在上一级作用域的执行上下文中查找对应的属性, 如果有直接返回, 否则进入3
  3. 再次执行2的相同操作, 直到全局作用域, 如果还找不到就抛出找不到的异常

```
var a = 1
function fn1() {
  var b = 2
  function fn2() {
    var c = 3
    console.log(c) //3
    console.log(b) //2
    console.log(a) //1
    console.log(d) //报错
  }
  fn2()
}
fn1()
```

#### 面试题

```
var x = 10;
function fn() {
  console.log(x);
}
function show(f) {
  var x = 20;
  f();
}
show(fn);  //10
```

```
var fn = function () {
  console.log(fn)
}
fn()
/*ƒ () {
  console.log(fn)
}*/

var obj = {
  fn2: function () {
   // console.log(fn2) //报错 fn2 is not defined
   console.log(this.fn2)
    /*ƒ () {
      // console.log(fn2) //fn2 is not defined
      console.log(this.fn2)
    }*/
  }
}
obj.fn2()
```

### 4.闭包

如何产生闭包?

  * 当一个嵌套的内部(子)函数引用了嵌套的外部(父)函数的变量(函数)时, 就产生了闭包

闭包到底是什么?

  * 使用chrome调试查看
  * 理解一: 闭包是嵌套的内部函数(绝大部分人)
  * 理解二: 包含被引用变量(函数)的对象(极少数人)
  * 注意: 闭包存在于嵌套的内部函数中

产生闭包的条件?

  * 函数嵌套
  * 内部函数引用了外部函数的数据(变量/函数)

```
function fn1 () {
  var a = 2
  var b = 'abc'
  function fn2 () { //执行函数定义就会产生闭包(不用调用内部函数)
    console.log(a)
  }
  // fn2()
}
fn1()

function fun1() {
  var a = 3
  var fun2 = function () {
    console.log(a)
  }
}
fun1()
```

#### 常见的闭包

1. 将函数作为另一个函数的返回值
2. 将函数作为实参传递给另一个函数调用

```
// 1. 将函数作为另一个函数的返回值
function fn1() {
  var a = 2
  function fn2() {
    a++
    console.log(a)
  }
  return fn2
}
var f = fn1()
f() // 3
f() // 4

// 2. 将函数作为实参传递给另一个函数调用
function showDelay(msg, time) {
  setTimeout(function () {
    alert(msg)
  }, time)
}
showDelay('wxy', 2000)
```

#### 闭包的作用

- 使用函数内部的变量在函数执行完后, 仍然存活在内存中(延长了局部变量的生命周期)
- 让函数外部可以操作(读写)到函数内部的数据(变量/函数)

问题:
  1. 函数执行完后, 函数内部声明的局部变量是否还存在? 

      一般是不存在, 存在于闭中的变量才可能存在

  2. 在函数外部能直接访问函数内部的局部变量吗? 

     不能, 但我们可以通过闭包让外部操作它

```
function fn1() {
  var a = 2
  function fn2() {
    a++
    console.log(a)
    // return a
  }
  function fn3() {
    a--
    console.log(a)
  }
  return fn3
}
var f = fn1()
f() // 1
f() // 0
```

#### 闭包的生命周期

1. 产生: 在嵌套内部函数定义执行完时就产生了(不是在调用)
2. 死亡: 在嵌套的内部函数成为垃圾对象时

```
function fn1() {
  //此时闭包就已经产生了(函数提升, 内部函数对象已经创建了)
  var a = 2
  function fn2 () {
    a++
    console.log(a)
  }
  return fn2
}
var f = fn1()
f() // 3
f() // 4
f = null //闭包死亡(包含闭包的函数对象成为垃圾对象)
```

#### 闭包的应用

定义JS模块
  * 具有特定功能的js文件
  * 将所有的数据和功能都封装在一个函数内部(私有的)
  * 只向外暴露一个包信n个方法的对象或函数
  * 模块的使用者, 只需要通过模块暴露的对象调用方法来实现对应的功能

```
function myModule() {
  //私有数据
  var msg = 'wxy'
  //操作数据的函数
  function doSomething() {
    console.log('doSomething() '+msg.toUpperCase())
  }
  function doOtherthing () {
    console.log('doOtherthing() '+msg.toLowerCase())
  }

  //向外暴露对象(给外部使用的方法)
  return {
    doSomething: doSomething,
    doOtherthing: doOtherthing
  }
}
```

```
(function () {
  //私有数据
  var msg = 'wxy'
  //操作数据的函数
  function doSomething() {
    console.log('doSomething() '+msg.toUpperCase())
  }
  function doOtherthing () {
    console.log('doOtherthing() '+msg.toLowerCase())
  }

  //向外暴露对象(给外部使用的方法)
  window.myModule2 = {
    doSomething: doSomething,
    doOtherthing: doOtherthing
  }
})()
```

#### 闭包的缺陷及解决方案

缺陷：

  * 函数执行完后, 函数内的局部变量没有释放, 占用内存时间会变长
  * 容易造成内存泄露

解决：

  * 能不用闭包就不用
  * 及时释放

```
function fn1() {
  var arr = new Array[100000]
  function fn2() {
    console.log(arr.length)
  }
  return fn2
}
var f = fn1()
f()

f = null //让内部函数成为垃圾对象-->回收闭包
```

#### 面试题

```
var name = "The Window";
var object = {
  name : "My Object",
  getNameFunc : function(){
    return function(){
      return this.name;
    };
  }
};
console.log('obj', object.getNameFunc()());  //  the window
```

```
var name2 = "The Window";
var object2 = {
  name2 : "My Object",
  getNameFunc : function(){
    var that = this;
    return function(){
      console.log(this.name2) //The Window
      return that.name2;
    };
  }
};
console.log('obj2', object2.getNameFunc()()); //  my object
```

```
function fun(n,o) {
  console.log(o)
  return {
    fun:function(m){
      return fun(m,n)
    }
  }
}
var a = fun(0)
a.fun(1)
a.fun(2)
a.fun(3)//undefined,0,0,0

var b = fun(0).fun(1).fun(2).fun(3)//undefined,0,1,2

var c = fun(0).fun(1)
c.fun(2)
c.fun(3)//undefined,0,1,1
```

## 六、对象高级

### 1.对象创建模式

#### Object构造函数模式

  * 套路: 先创建空Object对象, 再动态添加属性/方法
  * 适用场景: 起始时不确定对象内部数据
  * 问题: 语句太多

```
var p = new Object()
p = {}
p.name = 'Tom'
p.age = 12
p.setName = function (name) {
  this.name = name
}
p.setaAge = function (age) {
  this.age = age
}

console.log(p)  //{name: 'Tom', age: 12, setName: ƒ, setaAge: ƒ}
```

#### 对象字面量模式

  * 套路: 使用{}创建对象, 同时指定属性/方法
  * 适用场景: 起始时对象内部数据是确定的
  * 问题: 如果创建多个对象, 有重复代码

```
var p = {
  name: 'Tom',
  age: 23,
  setName: function (name) {
    this.name = name
  }
}
console.log(p.name, p.age) //Tom 23
p.setName('JACK')
console.log(p.name, p.age) //JACK 23

var p2 = {
  name: 'BOB',
  age: 24,
  setName: function (name) {
    this.name = name
  }
}
```

#### 工厂模式

* 套路: 通过工厂函数动态创建对象并返回
* 适用场景: 需要创建多个对象
* 问题: 对象没有一个具体的类型, 都是Object类型

```
function createPerson(name, age) {
  var p = {
    name: name,
    age: age,
    setName: function (name) {
      this.name = name
    }
  }
  return p
}

var p1 = createPerson('Tom', 12)
var p2 = createPerson('JAck', 13)
console.log(p1) //{name: 'Tom', age: 12, setName: ƒ}
console.log(p2) //{name: 'JAck', age: 13, setName: ƒ}
```

#### 自定义构造函数模式

* 套路: 自定义构造函数, 通过new创建对象
* 适用场景: 需要创建多个类型确定的对象
* 问题: 每个对象都有相同的数据, 浪费内存

```
function Person(name, age) {
  this.name = name
  this.age = age
  this.setName = function (name) {
    this.name = name
  }
}

var p1 = new Person('Tom', 12)
var p2 = new Person('Tom2', 13)
console.log(p1, p1 instanceof Person) //Person {name: 'Tom', age: 12, setName: ƒ} true
```

#### 构造函数+原型的组合模式

* 套路: 自定义构造函数, 属性在函数中初始化, 方法添加到原型上
* 适用场景: 需要创建多个类型确定的对象

```
function Person (name, age) {
  this.name = name
  this.age = age
}
Person.prototype.setName = function (name) {
  this.name = name
}
var p1 = new Person('Tom', 12)
var p2 = new Person('JAck', 23)
p1.setName('TOM3')
console.log(p1) //Person {name: 'TOM3', age: 12}

Person.prototype.setAge = function (age) {
  this.age = age
}
p1.setAge(23)
console.log(p1.age) //23

Person.prototype = {}
p1.setAge(34)
console.log(p1) //Person {name: 'TOM3', age: 34}
var p3 = new Person('BOB', 12)
p3.setAge(12) //报错，Uncaught TypeError: p3.setAge is not a function
```

### 2.继承模式

#### 原型继承链

套路

- 定义父类型构造函数
- 给父类型的原型添加方法
- 定义子类型的构造函数
- 创建父类型的对象赋值给子类型的原型
- 将子类型原型的构造属性设置为子类型
- 给子类型原型添加方法
- 创建子类型的对象: 可以调用父类型的方法

**关键**

​	子类型的原型为父类型的一个实例对象

因为父类型的实例能看到父类型原型上的方法，所以子类型的原型必须指向父类型的实例，其中原型指向的都是一个实例对象，而不是一个构造函数

```
function Supper() { //父类型
  this.superProp = 'The super prop'
}
//原型的数据所有的实例对象都可见
Supper.prototype.showSupperProp = function () {
  console.log(this.superProp)
}

function Sub() { //子类型
  this.subProp = 'The sub prop'
}

// 子类的原型为父类的实例
Sub.prototype = new Supper()
// Sub.prototype = Supper()
// 修正Sub.prototype.constructor为Sub本身
Sub.prototype.constructor = Sub

Sub.prototype.showSubProp = function () {
  console.log(this.subProp)
}

// 创建子类型的实例
var sub = new Sub()
// 调用父类型的方法
sub.showSubProp() //The sub prop
// 调用子类型的方法
sub.showSupperProp() //The super prop
console.log(sub.__proto__) //Supper {superProp: 'The super prop', constructor: ƒ, showSubProp: ƒ}
```

![原型链继承](https://raw.githubusercontent.com/weixiaoyun/Images/js%E9%AB%98%E7%BA%A7/%E5%8E%9F%E5%9E%8B%E9%93%BE%E7%BB%A7%E6%89%BF.png)

#### 借用构造函数继承

套路:

- 定义父类型构造函数
- 定义子类型构造函数
- 在子类型构造函数中调用父类型构造

**关键**:

  - 在子类型构造函数中通用super()调用父类型构造函数

```
function Person(name, age) {
  this.name = name
  this.age = age
}

function Student(name, age, price) {
  Person.call(this, name, age)   // this.Person(name, age)
  this.price = price
}

var s = new Student('Tom', 20, 12000)
console.log(s.name, s.age, s.price) //Tom 20 12000
```

#### 组合继承

- 利用原型链实现对父类型对象的方法继承
- 利用call()借用父类型构建函数初始化相同属性

```
function Person(name, age) {
  this.name = name
  this.age = age
}
Person.prototype.setName = function (name) {
  this.name = name
}

function Student(name, age, price) {
  Person.call(this, name, age) //得到父类型的属性
  this.price = price
}
Student.prototype = new Person()  //得到父类型的方法
Student.prototype.constructor = Student
Student.prototype.setPrice = function (price) {
  this.price = price
}

var s = new Student('Tom', 12, 10000)
s.setPrice(11000)
s.setName('Bob')
console.log(s) //Student {name: 'Bob', age: 12, price: 11000}
console.log(s.constructor)
/*ƒ Student(name, age, price) {
  Person.call(this, name, age) //得到父类型的属性
  this.price = price
}
```