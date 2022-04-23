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

### 1.原型（prototype）

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

### 2.显示原型与隐式原型

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

### 3.原型链

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

### 4.instanceof

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

### 5.原型（链）面试题

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

### 6.函数提升与变量提升

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

### 7.执行上下文

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

### 8.执行上下文栈

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

### 9.执行上下文面试题

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