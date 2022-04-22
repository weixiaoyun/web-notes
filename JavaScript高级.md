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