# ES6~ES11

参考：https://es6.ruanyifeng.com/

## 一、简介

### 1.ECMA

ECMA（European Computer Manufacturers Association）中文名称为欧洲计算机制造商协会，这个组织的目标是评估、开发和认可电信和计算机标准。1994 年后该组织改名为 Ecma 国际。

### 2.ECMAScript

ECMAScript 是由 Ecma 国际通过 ECMA-262 标准化的脚本程序设计语言。

### 3.ECMA-262

Ecma 国际制定了许多标准，而 ECMA-262 只是其中的一个，所有标准列表查看

http://www.ecma-international.org/publications/standards/Standard.htm

ECMA-262（ECMAScript）历史版本查看网址

http://www.ecma-international.org/publications/standards/Ecma-262-arch.htm

|   第1版   |      1997 年       | 制定了语言的基本语法                                         |
| :-------: | :----------------: | :----------------------------------------------------------- |
|   第2版   |      1998 年       | 较小改动                                                     |
|   第3版   |      1999 年       | 引入正则、异常处理、格式化输出等。IE 开始支持                |
|   第4版   |      2007 年       | 过于激进，未发布                                             |
|   第5版   |       2009年       | 引入严格模式、JSON，扩展对象、数组、原型、字符串、日期方法   |
| **第6版** |     **2015年**     | **模块化、面向对象语法、Promise、箭头函数、let、const、数组解构赋值等等** |
|   第7版   |       2016年       | 幂运算符、数组扩展、Async/await 关键字                       |
|   第8版   |       2017年       | Async/await、字符串扩展                                      |
|   第9版   |       2018年       | 对象解构赋值、正则扩展                                       |
|  第10版   |       2019年       | 扩展对象、数组方法                                           |
|  ES.next  | 动态指向下一个版本 |                                                              |

**注：从** **ES6** **开始，每年发布一个版本，版本号比年份最后一位大** **1**



TC39（Technical Committee 39）是推进 ECMAScript 发展的委员会。其会员都是公司（其中主要是浏览器厂商，有苹果、谷歌、微软、因特尔等）。TC39 定期召开会议，会议由会员公司的代表与特邀专家出席。也是该机构在维护**ECMA-262**



## 二、ES6

### 1.let

let 关键字用来声明变量，使用 let 声明的变量有几个特点：

- 不允许重复声明
- 块级作用域
- 不存在变量提升
- 不影响作用域链

**应用场景：以后声明变量使用** **let** **就对了**

```
//声明变量
let a;
let b,c,d;
let e = 100;
let f = 521, g = 'iloveyou', h = [];

//1. 变量不能重复声明
let star = '罗志祥';
let star = '小猪';

//2. 块级作用域  全局, 函数, eval
if else while for
{
    let girl = '周扬青';
}
console.log(girl);

//3. 不存在变量提升
console.log(song); //报错 ncaught ReferenceError: Cannot access 'song' before initialization
let song = '恋爱达人';

//4. 不影响作用域链
{
    let name = 'wxy';
    function fn(){
        console.log(name); //wxy
    }
    fn();
}
```

#### 实践案例

```
<div class="container">
    <h2 class="page-header">点击切换颜色</h2>
    <div class="item"></div>
    <div class="item"></div>
    <div class="item"></div>
</div>
<script>
    //获取div元素对象
    let items = document.getElementsByClassName('item');

    //遍历并绑定事件
    for(let i = 0;i<items.length;i++){
        items[i].onclick = function(){
            //修改当前元素的背景颜色
            // this.style.background = 'pink';
            items[i].style.background = 'pink';
        }
    }
    
</script>
```

如果绑定事件时采用var：

```
for(var i = 0;i<items.length;i++){
    items[i].onclick = function(){
        //修改当前元素的背景颜色
        // this.style.background = 'pink';
        items[i].style.background = 'pink';//该处的i为3
    }
}
```

则会报错，因为var定义的i成了一个全局变量，最后i为3，相当于给每一个item（item[0]、item[1]、item[2]）绑定一个事件，该事件使得item[3]的背景颜色修改为pink。然而没有item3这个元素。



### 2.const关键字

const 关键字用来声明常量，const 声明有以下特点

- 声明必须赋初始值
- 标识符一般为大写
- 不允许重复声明
- 值不允许修改
- 块级作用域

**注意：对象属性修改和数组元素变化不会出发 const 错误**

**应用场景：声明对象类型使用 const，非对象类型声明选择 let**

```
//声明常量
const NAME = 'WXY';

//1. 一定要赋初始值
const A;
//2. 一般常量使用大写(潜规则)
const a = 100;
//3. 常量的值不能修改
NAME = 'wxy';
//4. 块儿级作用域
{
    const PLAYER = 'UZI';
}
console.log(PLAYER); //报错 PLAYER is not defined 
//5. 对于数组和对象的元素修改, 不算做对常量的修改, 不会报错
const TEAM = ['UZI','MXLG','Ming','Letme'];
// TEAM.push('Meiko');
```



### 3.变量的解构赋值

ES6 允许按照一定模式，从数组和对象中提取值，对变量进行赋值，这被称为解构赋值。

#### 数组的结构

```
const F4 = ['小沈阳','刘能','赵四','宋小宝'];
let [xiao, liu, zhao, song] = F4;
console.log(xiao); //小沈阳
console.log(liu); //刘能
console.log(zhao); //赵四
console.log(song); //宋小宝
```

#### 对象的解构

```
const zhao = {
    name: '赵本山',
    age: '不详',
    xiaopin: function(){
        console.log("我可以演小品");
    }
};

let {name, age, xiaopin} = zhao;
console.log(name); //赵本山
console.log(age); //不详
console.log(xiaopin); //
                        /*ƒ (){
                            console.log("我可以演小品");
                        }*/
xiaopin(); //我可以演小品
```

```
let {xiaopin} = zhao;
xiaopin();  //我可以演小品
```

复杂结构：

```
let wangfei = {
    name: '王菲',
    age: 18,
    songs: ['红豆', '流年', '暧昧', '传奇'],
    history: [
        {name: '窦唯'},
        {name: '李亚鹏'},
        {name: '谢霆锋'}
    ]
};
let {songs: [one, two, three], history: [first, second, third]} = wangfei;
```



### 4.模板字符串

模板字符串（template string）是增强版的字符串，用反引号（`）标识，特点：

- 字符串中可以出现换行符
- 可以使用 ${xxx} 形式输出变量

```
// ES6 引入新的声明字符串的方式 『``』 '' "" 
//1. 声明
// let str = `我也是一个字符串哦!`;
// console.log(str, typeof str);

//2. 内容中可以直接出现换行符
let str = `<ul>
            <li>沈腾</li>
            <li>玛丽</li>
            <li>魏翔</li>
            <li>艾伦</li>
            </ul>`;
//3. 变量拼接
let lovest = '魏翔';
let out = `${lovest}是我心目中最搞笑的演员!!`;
console.log(out); //魏翔是我心目中最搞笑的演员!!
```

**注意：当遇到字符串与变量拼接的情况使用模板字符串**



### 5.简化对象写法

ES6 允许在大括号里面，直接写入变量和函数，作为对象的属性和方法。这样的书写更加简洁。

```
let name = 'wxy';
let change = function(){
    console.log('我们可以改变你!!');
}

const school = {
    name,
    change,
    improve(){
        console.log("我们可以提高你的技能");
    }
}

console.log(school); //{name: 'wxy', change: ƒ, improve: ƒ}
```

**注意：对象简写形式简化了代码，所以以后用简写就对了**



### 6.箭头函数

ES6 允许使用「箭头」（=>）定义函数。

```
/**
 * 1. 通用写法
 */
let fn = (arg1, arg2, arg3) => {
    return arg1 + arg2 + arg3;
}
```

箭头函数的注意点:

- 如果形参只有一个，则小括号可以省略
- 函数体如果只有一条语句，则花括号可以省略，函数的返回值为该条语句的执行结果
- 箭头函数 this 指向声明时所在作用域下 this 的值
- 箭头函数不能作为构造函数实例化
- 不能使用 arguments

```
//声明一个函数
// let fn = function(){
//
// }
let fn = (a,b) => {
    return a + b;
}
//调用函数
let result = fn(1, 2);
console.log(result); //3
```

this 是静态的. this 始终指向函数声明时所在作用域下的 this 的值

```
function getName(){
    console.log(this.name);
}
let getName2 = () => {
    console.log(this.name);
}
// getName();
// getName2();

//设置 window 对象的 name 属性
window.name = 'WEIXXIAOYUN';
const school = {
    name: "wxy"
}

//直接调用
getName(); //WEIXXIAOYUN
getName2(); //WEIXXIAOYUN
```

```
//call 方法调用
getName.call(school); //wxy
getName2.call(school); //WEIXXIAOYUN
```



不能作为构造实例化对象：

```
let Person = (name, age) => {
    this.name = name;
    this.age = age;
}
let me = new Person('xiao',30);
console.log(me); //报错  Person is not a constructor
```



不能使用 arguments 变量

```
let fn = () => {
    console.log(arguments); //报错 arguments is not defined
}
fn(1,2,3);
```



箭头函数缩写

```
//1) 省略小括号, 当形参有且只有一个的时候
// let add = n => {
//     return n + n;
// }
// console.log(add(9));
//2) 省略花括号, 当代码体只有一条语句的时候, 此时 return 必须省略
// 而且语句的执行结果就是函数的返回值
let pow = n => n * n;

console.log(pow(8));//64
```

**注意：箭头函数不会更改** **this** **指向，用来指定回调函数会非常合适**

#### 实践案例

箭头函数适合与 this 无关的回调. 定时器, 数组的方法回调

箭头函数不适合与 this 有关的回调.  事件回调, 对象的方法

```
<div id="ad"></div>
<script>
    //需求-1  点击 div 2s 后颜色变成『粉色』
    //获取元素
    let ad = document.getElementById('ad');
    //绑定事件
    ad.addEventListener("click", function(){
        //保存 this 的值
        // let _this = this;
        //定时器
        setTimeout(() => {
            //修改背景颜色 this
            // console.log(this);
            // _this.style.background = 'pink';
            this.style.background = 'pink';
        }, 2000);
    });

    //需求-2  从数组中返回偶数的元素
    const arr = [1,6,9,10,100,25];
    // const result = arr.filter(function(item){
    //     if(item % 2 === 0){
    //         return true;
    //     }else{
    //         return false;
    //     }
    // });
    
    const result = arr.filter(item => item % 2 === 0);

    console.log(result);

```

### 7.参数的默认值

ES6 允许给函数参数赋值初始值

1.形参初始值 具有默认值的参数, 一般位置要靠后(潜规则)

```
function add(a,c=10,b) {
    return a + b + c;
}
let result = add(1,2);
console.log(result); //NaN 因为此时2赋值给c
```

2.与解构赋值结合

```
function connect({host="127.0.0.1", username,password, port}){
    console.log(host)
    console.log(username)
    console.log(password)
    console.log(port)
}
connect({
    host: 'wxy.com',
    username: 'root',
    password: 'root',
    port: 3306
})
// wxy.com
// root
// root
// 3306
```

#### 

### 8.rest 参数

ES6 引入 rest 参数，用于获取函数的实参，用来代替 arguments



ES5 获取实参的方式

```
function date(){
    console.log(arguments);
}
date('白芷','阿娇','思慧'); //Arguments(3) ['白芷', '阿娇', '思慧', callee: ƒ, Symbol(Symbol.iterator): ƒ]
```



rest参数

```
function date(...args){
    console.log(args);// filter some every map
}
date('阿娇','柏芝','思慧'); //['阿娇', '柏芝', '思慧']
```



rest 参数必须要放到参数最后

```
function fn(a,b,...args){
    console.log(a); //1
    console.log(b); //2
    console.log(args); //[3, 4, 5, 6]
}
fn(1,2,3,4,5,6);
```

**注意：rest 参数非常适合不定个数参数函数的场景**



### 9.spread 扩展运算符

扩展运算符（spread）也是三个点（...）。它好比 rest 参数的逆运算，将一个数组转为用逗号分隔的参数序列，对数组进行解包。

... 扩展运算符能将『数组』转换为逗号分隔的『参数序列』

```
//声明一个数组 ...
const tfboys = ['易烊千玺','王源','王俊凯'];
// => '易烊千玺','王源','王俊凯'

// 声明一个函数
function chunwan(){
    console.log(arguments);
}

chunwan(...tfboys);// chunwan('易烊千玺','王源','王俊凯')
```

#### 应用

1. 数组的合并

```
const kuaizi = ['王太利','肖央'];
const fenghuang = ['曾毅','玲花'];
// const zuixuanxiaopingguo = kuaizi.concat(fenghuang);
const zuixuanxiaopingguo = [...kuaizi, ...fenghuang];
console.log(zuixuanxiaopingguo); //['王太利', '肖央', '曾毅', '玲花']
```

2. 数组的克隆

```
const sanzhihua = ['E','G','M'];
const sanyecao = [...sanzhihua];//  ['E','G','M']
console.log(sanyecao);
```

3.将伪数组转为真正的数组

```
const divs = document.querySelectorAll('div');
const divArr = [...divs];
console.log(divArr);// arguments
                    //[div, div, div]
```

### 10.Symbol

#### Symbol 基本使用

ES6 引入了一种新的原始数据类型 Symbol，表示独一无二的值。它是JavaScript 语言的第七种数据类型，是一种类似于字符串的数据类型。

**Symbol 特点：**

- Symbol 的值是唯一的，用来解决命名冲突的问题
- Symbol 值不能与其他数据进行运算
- Symbol 定义的对象属性不能使用 for…in 循 环遍 历 ，但是可以使用Reflect.ownKeys 来获取对象的所有键名



变量`s`就是一个独一无二的值。`typeof`运算符的结果，表明变量`s`是 Symbol 数据类型，而不是字符串之类的其他类型。

```
let s = Symbol();
console.log(s, typeof s); //Symbol() 'symbol'
```



`Symbol`函数前不能使用`new`命令，否则会报错。这是因为生成的 Symbol 是一个原始类型的值，不是对象。也就是说，由于 Symbol 值不是对象，所以不能添加属性。基本上，它是一种类似于字符串的数据类型。

`Symbol`函数可以接受一个字符串作为参数，表示对 Symbol 实例的描述，主要是为了在控制台显示，或者转为字符串时，比较容易区分。

其中`s1`和`s2`是两个 Symbol 值。如果不加参数，它们在控制台的输出都是`Symbol()`，不利于区分。有了参数以后，就等于为它们加上了描述，输出的时候就能够分清，到底是哪一个值。

```
let s1 = Symbol('foo');
let s2 = Symbol('bar');

s1 // Symbol(foo)
s2 // Symbol(bar)

s1.toString() // "Symbol(foo)"
s2.toString() // "Symbol(bar)"
```



如果 Symbol 的参数是一个对象，就会调用该对象的`toString`方法，将其转为字符串，然后才生成一个 Symbol 值。

```
const obj = {
    toString() {
        return 'abc';
    }
};
const sym = Symbol(obj);
sym // Symbol(abc)
```

**注意**，`Symbol`函数的参数只是表示对当前 Symbol 值的描述，因此相同参数的`Symbol`函数的返回值是不相等的。

```
// 没有参数的情况
let s1 = Symbol();
let s2 = Symbol();

s1 === s2 // false

// 有参数的情况
let s1 = Symbol('foo');
let s2 = Symbol('foo');

s1 === s2 // false
```



Symbol 值不能与其他类型的值进行运算，会报错。

```
   let result = s + 100;
   let result = s > 100;
   let result = s + s;
let sym = Symbol('My symbol');

"your symbol is " + sym
// TypeError: can't convert symbol to string
`your symbol is ${sym}`
// TypeError: can't convert symbol to string
```



但是，Symbol 值可以显式转为字符串。

```
let sym = Symbol('My symbol');

String(sym) // 'Symbol(My symbol)'
sym.toString() // 'Symbol(My symbol)'
```



另外，Symbol 值也可以转为布尔值，但是不能转为数值。

```
let sym = Symbol();
Boolean(sym) // true
!sym  // false

if (sym) {
    // ...
}

Number(sym) // TypeError
sym + 2 // TypeError
```

**注意: 遇到唯一性的场景时要想到 Symbol**

#### 作为属性名的 Symbol 

由于每一个 Symbol 值都是不相等的，这意味着 Symbol 值可以作为标识符，用于对象的属性名，就能保证不会出现同名的属性。这对于一个对象由多个模块构成的情况非常有用，能防止某一个键被不小心改写或覆盖。

```
let mySymbol = Symbol();

// 第一种写法
let a = {};
a[mySymbol] = 'Hello!';

// 第二种写法
let a = {
    [mySymbol]: 'Hello!'
};

// 第三种写法
let a = {};
Object.defineProperty(a, mySymbol, { value: 'Hello!' });

// 以上写法都得到同样结果
a[mySymbol] // "Hello!"
```

**注意**，Symbol 值作为对象属性名时，不能用点运算符。

因为点运算符后面总是字符串，所以不会读取`mySymbol`作为标识名所指代的那个值，导致`a`的属性名实际上是一个字符串，而不是一个 Symbol 值。

```
const mySymbol = Symbol();
const a = {};

a.mySymbol = 'Hello!';
a[mySymbol] // undefined
a['mySymbol'] // "Hello!"
```

同理，在对象的内部，使用 Symbol 值定义属性时，Symbol 值必须放在方括号之中。

```
let s = Symbol();

/*let obj = {
    [s]: function (arg) { ... }
};*/

let obj = {
    [s](arg) { ... }
};

obj[s](123);
```

Symbol 类型还可以用于定义一组常量，保证这组常量的值都是不相等的。

常量使用 Symbol 值最大的好处，就是其他任何值都不可能有相同的值了，因此可以保证switch语句会按设计的方式工作。

```
const COLOR_RED    = Symbol();
const COLOR_GREEN  = Symbol();

function getComplement(color) {
    switch (color) {
        case COLOR_RED:
            return COLOR_GREEN;
        case COLOR_GREEN:
            return COLOR_RED;
        default:
            throw new Error('Undefined color');
    }
}
```

**注意**，Symbol 值作为属性名时，该属性还是公开属性，不是私有属性。



**作用：消除魔术字符串**

魔术字符串指的是，在代码之中多次出现、与代码形成强耦合的某一个具体的字符串或者数值。风格良好的代码，应该尽量消除魔术字符串，改由含义清晰的变量代替。

```
function getArea(shape, options) {
    let area = 0;

    switch (shape) {
        case 'Triangle': // 魔术字符串
            area = .5 * options.width * options.height;
            break;
        /* ... more code ... */
    }

    return area;
}

getArea('Triangle', { width: 100, height: 100 }); // 魔术字符串
```

上面代码中，字符串`Triangle`就是一个魔术字符串。它多次出现，与代码形成“强耦合”，不利于将来的修改和维护。

常用的消除魔术字符串的方法，就是把它写成一个变量。

```
const shapeType = {
    triangle: 'Triangle'
};

function getArea(shape, options) {
    let area = 0;
    switch (shape) {
        case shapeType.triangle:
            area = .5 * options.width * options.height;
            break;
    }
    return area;
}

getArea(shapeType.triangle, { width: 100, height: 100 });
```

上面代码中，我们把`Triangle`写成`shapeType`对象的`triangle`属性，这样就消除了强耦合。

如果仔细分析，可以发现`shapeType.triangle`等于哪个值并不重要，只要确保不会跟其他`shapeType`属性的值冲突即可。因此，这里就很适合改用 Symbol 值。

```
const shapeType = {
    triangle: Symbol()
};
```

#### 

#### Symbol.prototype.description

读取描述需要采用toString方法将 Symbol 显式转为字符串，不是很方便

[ES2019](https://github.com/tc39/proposal-Symbol-description) 提供了一个实例属性`description`，直接返回 Symbol 的描述。

```
const sym = Symbol('foo');

sym.description // "foo"
```



#### Symbol.for()，Symbol.keyFor()

我们希望重新使用同一个 Symbol 值，`Symbol.for()`方法可以做到这一点。它接受一个字符串作为参数，然后搜索有没有以该参数作为名称的 Symbol 值。如果有，就返回这个 Symbol 值，否则就新建一个以该字符串为名称的 Symbol 值，并将其注册到全局。

```
let s1 = Symbol.for('foo');
let s2 = Symbol.for('foo');

s1 === s2 // true
```

其中，`s1`和`s2`都是 Symbol 值，但是它们都是由同样参数的`Symbol.for`方法生成的，所以实际上是同一个值。

Symbol.for()与Symbol()的区别：

- 前者会被登记在全局环境中供搜索（登记机制），后者不会。
- `Symbol.for()`不会每次调用就返回一个新的 Symbol 类型的值，而是会先检查给定的`key`是否已经存在，如果不存在才会新建一个值。



`Symbol.keyFor()`方法返回一个已登记的 Symbol 类型值的`key`。

```
let s1 = Symbol.for("foo");
Symbol.keyFor(s1) // "foo"

let s2 = Symbol("foo");
Symbol.keyFor(s2) // undefined
```

上面代码中，变量`s2`属于未登记的 Symbol 值，所以返回`undefined`。



**注意**，`Symbol.for()`为 Symbol 值登记的名字，是全局环境的，不管有没有在全局环境运行。

```
function foo() {
    return Symbol.for('bar');
}

const x = foo();
const y = Symbol.for('bar');
console.log(x === y); // true
```

`Symbol.for('bar')`是函数内部运行的，但是生成的 Symbol 值是登记在全局环境的。所以，第二次运行`Symbol.for('bar')`可以取到这个 Symbol 值。



`Symbol.for()`的这个全局登记特性，可以用在不同的 iframe 或 service worker 中取到同一个值。

```
iframe = document.createElement('iframe');
iframe.src = String(window.location);
document.body.appendChild(iframe);

iframe.contentWindow.Symbol.for('foo') === Symbol.for('foo')
// true
```

上面代码中，iframe 窗口生成的 Symbol 值，可以在主页面得到。

```
// USONB  you are so niubility
// u  undefined
// s  string  symbol
// o  object
// n  null number
// b  boolean
```



#### Symbol内置值

除了定义自己使用的 Symbol 值以外，ES6 还提供了 11 个内置的 Symbol 值，指向语言内部使用的方法。可以称这些方法为魔术方法，因为它们会在特定的场景下自动执行。

| Symbol.hasInstance        | 当其他对象使用 instanceof 运算符，判断是否为该对象的实例时，会调用这个方法 |
| ------------------------- | ------------------------------------------------------------ |
| Symbol.isConcatSpreadable | 对象的 Symbol.isConcatSpreadable 属性等于的是一个布尔值，表示该对象用于 Array.prototype.concat()时，是否可以展开。 |
| Symbol.species            | 创建衍生对象时，会使用该属性                                 |
| Symbol.match              | 当执行 str.match(myObject) 时，如果该属性存在，会调用它，返回该方法的返回值。 |
| Symbol.replace            | 当该对象被 str.replace(myObject)方法调用时，会返回该方法的返回值。 |
| Symbol.search             | 当该对象被 str.search (myObject)方法调用时，会返回该方法的返回值。 |
| Symbol.split              | 当该对象被 str.split(myObject)方法调用时，会返回该方法的返回值。 |
| Symbol.iterator           | 对象进行 for...of 循环时，会调用 Symbol.iterator 方法，返回该对象的默认遍历器 |
| Symbol.toPrimitive        | 该对象被转为原始类型的值时，会调用这个方法，返回该对象对应的原始类型值。 |
| Symbol. toStringTag       | 在该对象上面调用 toString 方法时，返回该方法的返回值         |
| Symbol. unscopables       | 该对象指定了使用 with 关键字时，哪些属性会被 with环境排除。  |

#### Symbol.hasInstance

对象的`Symbol.hasInstance`属性，指向一个内部方法。当其他对象使用`instanceof`运算符，判断是否为该对象的实例时，会调用这个方法。

比如，`foo instanceof Foo`在语言内部，实际调用的是`Foo[Symbol.hasInstance](foo)`。

```
class MyClass {
    [Symbol.hasInstance](foo) {
        return foo instanceof Array;
    }
}

[1, 2, 3] instanceof new MyClass() // true
```

上面代码中，`MyClass`是一个类，`new MyClass()`会返回一个实例。该实例的`Symbol.hasInstance`方法，会在进行`instanceof`运算时自动调用，判断左侧的运算子是否为`Array`的实例。



```
class Even {
    static [Symbol.hasInstance](obj) {
        return Number(obj) % 2 === 0;
    }
}

// 等同于
const Even = {
    [Symbol.hasInstance](obj) {
        return Number(obj) % 2 === 0;
    }
};

1 instanceof Even // false
2 instanceof Even // true
12345 instanceof Even // false
```



#### Symbol.isConcatSpreadable

对象的`Symbol.isConcatSpreadable`属性等于一个布尔值，表示该对象用于`Array.prototype.concat()`时，是否可以展开。

```
let arr1 = ['c', 'd'];
['a', 'b'].concat(arr1, 'e') // ['a', 'b', 'c', 'd', 'e']
arr1[Symbol.isConcatSpreadable] // undefined

let arr2 = ['c', 'd'];
arr2[Symbol.isConcatSpreadable] = false;
['a', 'b'].concat(arr2, 'e') // ['a', 'b', ['c','d'], 'e']
```

上面代码说明，数组的默认行为是可以展开，`Symbol.isConcatSpreadable`默认等于`undefined`。该属性等于`true`时，也有展开的效果。

类似数组的对象正好相反，默认不展开。它的`Symbol.isConcatSpreadable`属性设为`true`，才可以展开。

```
let obj = {length: 2, 0: 'c', 1: 'd'};
['a', 'b'].concat(obj, 'e') // ['a', 'b', obj, 'e']

obj[Symbol.isConcatSpreadable] = true;
['a', 'b'].concat(obj, 'e') // ['a', 'b', 'c', 'd', 'e']
```

`Symbol.isConcatSpreadable`属性也可以定义在类里面。

**注意**，`Symbol.isConcatSpreadable`的位置差异，`A1`是定义在实例上，`A2`是定义在类本身，效果相同。

```
class A1 extends Array {
    constructor(args) {
        super(args);
        this[Symbol.isConcatSpreadable] = true;
    }
}
class A2 extends Array {
    constructor(args) {
        super(args);
    }
    get [Symbol.isConcatSpreadable] () {
        return false;
    }
}
let a1 = new A1();
a1[0] = 3;
a1[1] = 4;
let a2 = new A2();
a2[0] = 5;
a2[1] = 6;
[1, 2].concat(a1).concat(a2)
// [1, 2, 3, 4, [5, 6]]
```

#### Symbol.species

对象的`Symbol.species`属性，指向一个构造函数。创建衍生对象时，会使用该属性。

```
class MyArray extends Array {
}

const a = new MyArray(1, 2, 3);
const b = a.map(x => x);
const c = a.filter(x => x > 1);

b instanceof MyArray // true
c instanceof MyArray // true
```

上面代码中，子类`MyArray`继承了父类`Array`，`a`是`MyArray`的实例，`b`和`c`是`a`的衍生对象。你可能会认为，`b`和`c`都是调用数组方法生成的，所以应该是数组（`Array`的实例），但实际上它们也是`MyArray`的实例。

`Symbol.species`属性就是为了解决这个问题而提供的。现在，我们可以为`MyArray`设置`Symbol.species`属性。

```javascript
class MyArray extends Array {
  static get [Symbol.species]() { return Array; }
}
```

上面代码中，由于定义了`Symbol.species`属性，创建衍生对象时就会使用这个属性返回的函数，作为构造函数。这个例子也说明，定义`Symbol.species`属性要采用`get`取值器。默认的`Symbol.species`属性等同于下面的写法。

```javascript
static get [Symbol.species]() {
  return this;
}
```



```javascript
class MyArray extends Array {
  static get [Symbol.species]() { return Array; }
}

const a = new MyArray();
const b = a.map(x => x);

b instanceof MyArray // false
b instanceof Array // true
```

上面代码中，`a.map(x => x)`生成的衍生对象，就不是`MyArray`的实例，而直接就是`Array`的实例。

```javascript
class T1 extends Promise {
}

class T2 extends Promise {
  static get [Symbol.species]() {
    return Promise;
  }
}

new T1(r => r()).then(v => v) instanceof T1 // true
new T2(r => r()).then(v => v) instanceof T2 // false
```

上面代码中，`T2`定义了`Symbol.species`属性，`T1`没有。结果就导致了创建衍生对象时（`then`方法），`T1`调用的是自身的构造方法，而`T2`调用的是`Promise`的构造方法。

总之，`Symbol.species`的作用在于，实例对象在运行过程中，需要再次调用自身的构造函数时，会调用该属性指定的构造函数。它主要的用途是，有些类库是在基类的基础上修改的，那么子类使用继承的方法时，作者可能希望返回基类的实例，而不是子类的实例。



#### Symbol.match

对象的`Symbol.match`属性，指向一个函数。当执行`str.match(myObject)`时，如果该属性存在，会调用它，返回该方法的返回值。

```javascript
String.prototype.match(regexp)
// 等同于
regexp[Symbol.match](this)

class MyMatcher {
  [Symbol.match](string) {
    return 'hello world'.indexOf(string);
  }
}

'e'.match(new MyMatcher()) // 1
```

同样：

```
var matcher = new MyMatcher();
console.log(matcher[Symbol.match]('e')) //1
```

#### Symbol.replace

对象的`Symbol.replace`属性，指向一个方法，当该对象被`String.prototype.replace`方法调用时，会返回该方法的返回值。

```javascript
String.prototype.replace(searchValue, replaceValue)
// 等同于
searchValue[Symbol.replace](this, replaceValue)
```

```javascript
const x = {};
x[Symbol.replace] = (...s) => console.log(s);

'Hello'.replace(x, 'World') // ["Hello", "World"]
```

`Symbol.replace`方法会收到两个参数，第一个参数是`replace`方法正在作用的对象，上面例子是`Hello`，第二个参数是替换后的值，上面例子是`World`。



#### Symbol.search

对象的`Symbol.search`属性，指向一个方法，当该对象被`String.prototype.search`方法调用时，会返回该方法的返回值。

```javascript
String.prototype.search(regexp)
// 等同于
regexp[Symbol.search](this)

class MySearch {
  constructor(value) {
    this.value = value;
  }
  [Symbol.search](string) {
    return string.indexOf(this.value);
  }
}
'foobar'.search(new MySearch('foo')) // 0
```

#### Symbol.split

对象的`Symbol.split`属性，指向一个方法，当该对象被`String.prototype.split`方法调用时，会返回该方法的返回值。

```javascript
String.prototype.split(separator, limit)
// 等同于
separator[Symbol.split](this, limit)
```

```javascript
class MySplitter {
  constructor(value) {
    this.value = value;
  }
  [Symbol.split](string) {
    let index = string.indexOf(this.value);
    if (index === -1) {
      return string;
    }
    return [
      string.substr(0, index),
      string.substr(index + this.value.length)
    ];
  }
}

'foobar'.split(new MySplitter('foo'))
// ['', 'bar']

'foobar'.split(new MySplitter('bar'))
// ['foo', '']

'foobar'.split(new MySplitter('baz'))
// 'foobar'
```

上面方法使用`Symbol.split`方法，重新定义了字符串对象的`split`方法的行为

#### Symbol.iterator

对象的`Symbol.iterator`属性，指向该对象的默认遍历器方法。

```javascript
const myIterable = {};
myIterable[Symbol.iterator] = function* () {
  yield 1;
  yield 2;
  yield 3;
};

[...myIterable] // [1, 2, 3]
```

对象进行`for...of`循环时，会调用`Symbol.iterator`方法，返回该对象的默认遍历器，详细介绍参见《Iterator 和 for...of 循环》

```javascript
class Collection {
  *[Symbol.iterator]() {
    let i = 0;
    while(this[i] !== undefined) {
      yield this[i];
      ++i;
    }
  }
}

let myCollection = new Collection();
myCollection[0] = 1;
myCollection[1] = 2;

for(let value of myCollection) {
  console.log(value);
}
// 1
// 2
```

#### Symbol.toPrimitive

对象的`Symbol.toPrimitive`属性，指向一个方法。该对象被转为原始类型的值时，会调用这个方法，返回该对象对应的原始类型值。

`Symbol.toPrimitive`被调用时，会接受一个字符串参数，表示当前运算的模式，一共有三种模式。

- Number：该场合需要转成数值
- String：该场合需要转成字符串
- Default：该场合可以转成数值，也可以转成字符串

```javascript
let obj = {
  [Symbol.toPrimitive](hint) {
    switch (hint) {
      case 'number':
        return 123;
      case 'string':
        return 'str';
      case 'default':
        return 'default';
      default:
        throw new Error();
     }
   }
};

2 * obj // 246
3 + obj // '3default'
obj == 'default' // true
String(obj) // 'str'
```

#### Symbol.toStringTag

对象的`Symbol.toStringTag`属性，指向一个方法。在该对象上面调用`Object.prototype.toString`方法时，如果这个属性存在，它的返回值会出现在`toString`方法返回的字符串之中，表示对象的类型。也就是说，这个属性可以用来定制`[object Object]`或`[object Array]`中`object`后面的那个字符串。

```javascript
// 例一
({[Symbol.toStringTag]: 'Foo'}.toString())
// "[object Foo]"

// 例二
class Collection {
  get [Symbol.toStringTag]() {
    return 'xxx';
  }
}
let x = new Collection();
Object.prototype.toString.call(x) // "[object xxx]"
```

### 11.迭代器（遍历器）

#### Iterator（遍历器）的概念

遍历器（Iterator）就是一种机制。它是一种接口，为各种不同的数据结构提供统一的访问机制。任何数据结构只要部署 Iterator 接口，就可以完成遍历操作。

Iterator 的作用有三个：

- 为各种数据结构，提供一个统一的、简便的访问接口；
- 使得数据结构的成员能够按某种次序排列；
- ES6 创造了一种新的遍历命令`for...of`循环，Iterator 接口主要供`for...of`消费。

工作原理：

- 创建一个指针对象，指向当前数据结构的起始位置。也就是说，遍历器对象本质上，就是一个指针对象。
- 第一次调用指针对象的`next`方法，可以将指针指向数据结构的第一个成员。
- 第二次调用指针对象的`next`方法，指针就指向数据结构的第二个成员。
- 不断调用指针对象的`next`方法，直到它指向数据结构的结束位置。

每一次调用`next`方法，都会返回数据结构的当前成员的信息。具体来说，就是返回一个包含`value`和`done`两个属性的对象。其中，`value`属性是当前成员的值，`done`属性是一个布尔值，表示遍历是否结束。

```
//声明一个数组
const xiyou = ['唐僧','孙悟空','猪八戒','沙僧'];

//使用 for...of 遍历数组
// for(let v of xiyou){
//     console.log(v);
// }

let iterator = xiyou[Symbol.iterator]();

//调用对象的next方法
console.log(iterator.next()); //{value: '唐僧', done: false}
console.log(iterator.next()); //{value: '孙悟空', done: false}
console.log(iterator.next()); //{value: '猪八戒', done: false}
console.log(iterator.next()); //{value: '沙僧', done: false}
console.log(iterator.next()); //{value: undefined, done: true}
```



```javascript
var it = makeIterator(['a', 'b']);

it.next() // { value: "a", done: false }
it.next() // { value: "b", done: false }
it.next() // { value: undefined, done: true }

function makeIterator(array) {
  var nextIndex = 0;
  return {
    next: function() {
      return nextIndex < array.length ?
        {value: array[nextIndex++], done: false} :
        {value: undefined, done: true};
    }
  };
}
```

上面代码定义了一个`makeIterator`函数，它是一个遍历器生成函数，作用就是返回一个遍历器对象。对数组`['a', 'b']`执行这个函数，就会返回该数组的遍历器对象（即指针对象）`it`。

可以简写为：

```javascript
function makeIterator(array) {
  var nextIndex = 0;
  return {
    next: function() {
      return nextIndex < array.length ?
        {value: array[nextIndex++]} :
        {done: true};
    }
  };
}
```

#### 默认 Iterator 接口

Iterator 接口的目的，就是为所有数据结构，提供了一种统一的访问机制，即`for...of`循环。当使用`for...of`循环遍历某种数据结构时，该循环会自动去寻找 Iterator 接口。

一种数据结构只要部署了 Iterator 接口，我们就称这种数据结构是“可遍历的”（iterable）。

`Symbol.iterator`属性本身是一个函数，就是当前数据结构默认的遍历器生成函数。执行这个函数，就会返回一个遍历器。至于属性名`Symbol.iterator`，它是一个表达式，返回`Symbol`对象的`iterator`属性，这是一个预定义好的、类型为 Symbol 的特殊值，所以要放在方括号内

```javascript
const obj = {
  [Symbol.iterator] : function () {
    return {
      next: function () {
        return {
          value: 1,
          done: true
        };
      }
    };
  }
};
```

面代码中，对象`obj`是可遍历的（iterable），因为具有`Symbol.iterator`属性。执行这个属性，会返回一个遍历器对象。该对象的根本特征就是具有`next`方法。每次调用`next`方法，都会返回一个代表当前成员的信息对象，具有`value`和`done`两个属性。

ES6 的有些数据结构原生具备 Iterator 接口（比如数组），即不用任何处理，就可以被`for...of`循环遍历。原因在于，这些数据结构原生部署了`Symbol.iterator`属性（详见下文），另外一些数据结构没有（比如对象）。凡是部署了`Symbol.iterator`属性的数据结构，就称为部署了遍历器接口。调用这个接口，就会返回一个遍历器对象。

```
//声明一个对象
const banji = {
    name: "终极一班",
    stus: [
        'xiaoming',
        'xiaoning',
        'xiaotian',
        'knight'
    ],
    [Symbol.iterator]() {
        //索引变量
        let index = 0;
        //
        let _this = this;
        return {
            next: function () {
                if (index < _this.stus.length) {
                    const result = { value: _this.stus[index], done: false };
                    //下标自增
                    index++;
                    //返回结果
                    return result;
                }else{
                    return {value: undefined, done: true};
                }
            }
        };
    }
}

//遍历这个对象
for (let v of banji) {
    console.log(v);
}
//xiaoming
//xiaoning
//xiaotian
//knight
```

原生具备 Iterator 接口的数据结构如下。

- Array
- Map
- Set
- String
- TypedArray
- 函数的 arguments 对象
- NodeList 对象

```javascript
let arr = ['a', 'b', 'c'];
let iter = arr[Symbol.iterator]();

iter.next() // { value: 'a', done: false }
iter.next() // { value: 'b', done: false }
iter.next() // { value: 'c', done: false }
iter.next() // { value: undefined, done: true }
```

上面代码中，变量`arr`是一个数组，原生就具有遍历器接口，部署在`arr`的`Symbol.iterator`属性上面。所以，调用这个属性，就得到遍历器对象。

对于原生部署 Iterator 接口的数据结构，不用自己写遍历器生成函数，`for...of`循环会自动遍历它们。除此之外，其他数据结构（主要是对象）的 Iterator 接口，都需要自己在`Symbol.iterator`属性上面部署，这样才会被`for...of`循环遍历。

对象（Object）之所以没有默认部署 Iterator 接口，是因为对象的哪个属性先遍历，哪个属性后遍历是不确定的，需要开发者手动指定。本质上，遍历器是一种线性处理，对于任何非线性的数据结构，部署遍历器接口，就等于部署一种线性转换。不过，严格地说，对象部署遍历器接口并不是很必要，因为这时对象实际上被当作 Map 结构使用，ES5 没有 Map 结构，而 ES6 原生提供了。

一个对象如果要具备可被`for...of`循环调用的 Iterator 接口，就必须在`Symbol.iterator`的属性上部署遍历器生成方法（原型链上的对象具有该方法也可）。

```javascript
class RangeIterator {
  constructor(start, stop) {
    this.value = start;
    this.stop = stop;
  }

  [Symbol.iterator]() { return this; }

  next() {
    var value = this.value;
    if (value < this.stop) {
      this.value++;
      return {done: false, value: value};
    }
    return {done: true, value: undefined};
  }
}

function range(start, stop) {
  return new RangeIterator(start, stop);
}

for (var value of range(0, 3)) {
  console.log(value); // 0, 1, 2
}
```

下面是通过遍历器实现“链表”结构的例子。

```javascript
function Obj(value) {
  this.value = value;
  this.next = null;
}

Obj.prototype[Symbol.iterator] = function() {
  var iterator = { next: next };

  var current = this;

  function next() {
    if (current) {
      var value = current.value;
      current = current.next;
      return { done: false, value: value };
    }
    return { done: true };
  }
  return iterator;
}

var one = new Obj(1);
var two = new Obj(2);
var three = new Obj(3);

one.next = two;
two.next = three;

for (var i of one){
  console.log(i); // 1, 2, 3
}
```

上面代码首先在构造函数的原型链上部署`Symbol.iterator`方法，调用该方法会返回遍历器对象`iterator`，调用该对象的`next`方法，在返回一个值的同时，自动将内部指针移到下一个实例。

```javascript
let obj = {
  data: [ 'hello', 'world' ],
  [Symbol.iterator]() {
    const self = this;
    let index = 0;
    return {
      next() {
        if (index < self.data.length) {
          return {
            value: self.data[index++],
            done: false
          };
        }
        return { value: undefined, done: true };
      }
    };
  }
};
```

对于类似数组的对象（存在数值键名和`length`属性），部署 Iterator 接口，有一个简便方法，就是`Symbol.iterator`方法直接引用数组的 Iterator 接口。

```javascript
NodeList.prototype[Symbol.iterator] = Array.prototype[Symbol.iterator];
// 或者
NodeList.prototype[Symbol.iterator] = [][Symbol.iterator];

[...document.querySelectorAll('div')] // 可以执行了
```

NodeList 对象是类似数组的对象，本来就具有遍历接口，可以直接遍历。上面代码中，我们将它的遍历接口改成数组的`Symbol.iterator`属性，可以看到没有任何影响。

下面是另一个类似数组的对象调用数组的`Symbol.iterator`方法的例子。

```javascript
let iterable = {
  0: 'a',
  1: 'b',
  2: 'c',
  length: 3,
  [Symbol.iterator]: Array.prototype[Symbol.iterator]
};
for (let item of iterable) {
  console.log(item); // 'a', 'b', 'c'
}
```

注意，普通对象部署数组的`Symbol.iterator`方法，并无效果。

```javascript
let iterable = {
  a: 'a',
  b: 'b',
  c: 'c',
  length: 3,
  [Symbol.iterator]: Array.prototype[Symbol.iterator]
};
for (let item of iterable) {
  console.log(item); // undefined, undefined, undefined
}
```

如果`Symbol.iterator`方法对应的不是遍历器生成函数（即会返回一个遍历器对象），解释引擎将会报错。

```javascript
var obj = {};

obj[Symbol.iterator] = () => 1;

[...obj] // TypeError: [] is not a function
```

有了遍历器接口，数据结构就可以用`for...of`循环遍历（详见下文），也可以使用`while`循环遍历。

```javascript
var $iterator = ITERABLE[Symbol.iterator]();
var $result = $iterator.next();
while (!$result.done) {
  var x = $result.value;
  // ...
  $result = $iterator.next();
}
```

上面代码中，`ITERABLE`代表某种可遍历的数据结构，`$iterator`是它的遍历器对象。遍历器对象每次移动指针（`next`方法），都检查一下返回值的`done`属性，如果遍历还没结束，就移动遍历器对象的指针到下一步（`next`方法），不断循环。

#### 调用 Iterator 接口的场合

有一些场合会默认调用 Iterator 接口（即`Symbol.iterator`方法），除了下文会介绍的`for...of`循环，还有几个别的场合。

**解构赋值**

对数组和 Set 结构进行解构赋值时，会默认调用`Symbol.iterator`方法。

```javascript
let set = new Set().add('a').add('b').add('c');

let [x,y] = set;
// x='a'; y='b'

let [first, ...rest] = set;
// first='a'; rest=['b','c'];
```

**扩展运算符**

扩展运算符（...）也会调用默认的 Iterator 接口。

```javascript
// 例一
var str = 'hello';
[...str] //  ['h','e','l','l','o']

// 例二
let arr = ['b', 'c'];
['a', ...arr, 'd']
// ['a', 'b', 'c', 'd']
```

上面代码的扩展运算符内部就调用 Iterator 接口。

实际上，这提供了一种简便机制，可以将任何部署了 Iterator 接口的数据结构，转为数组。也就是说，只要某个数据结构部署了 Iterator 接口，就可以对它使用扩展运算符，将其转为数组。

```javascript
let arr = [...iterable];
```

**yield**

`yield*`后面跟的是一个可遍历的结构，它会调用该结构的遍历器接口。

```javascript
let generator = function* () {
  yield 1;
  yield* [2,3,4];
  yield 5;
};

var iterator = generator();

iterator.next() // { value: 1, done: false }
iterator.next() // { value: 2, done: false }
iterator.next() // { value: 3, done: false }
iterator.next() // { value: 4, done: false }
iterator.next() // { value: 5, done: false }
iterator.next() // { value: undefined, done: true }
```

**其他场合**

由于数组的遍历会调用遍历器接口，所以任何接受数组作为参数的场合，其实都调用了遍历器接口。下面是一些例子。

- for...of
- Array.from()
- Map(), Set(), WeakMap(), WeakSet()（比如`new Map([['a',1],['b',2]])`）
- Promise.all()
- Promise.race()

### 12.生成器（Generator）

Generator 函数是 ES6 提供的一种异步编程解决方案，语法行为与传统函数完全不同。

语法上，首先可以把它理解成，Generator 函数是一个状态机，封装了多个内部状态。

执行 Generator 函数会返回一个遍历器对象，也就是说，Generator 函数除了状态机，还是一个遍历器对象生成函数。返回的遍历器对象，可以依次遍历 Generator 函数内部的每一个状态。

形式上，Generator 函数是一个普通函数，但是有两个特征。一是，`function`关键字与函数名之间有一个星号；二是，函数体内部使用`yield`表达式，定义不同的内部状态（`yield`在英语里的意思就是“产出”）。

```javascript
function* helloWorldGenerator() {
  yield 'hello';
  yield 'world';
  return 'ending';
}

var hw = helloWorldGenerator();
```

Generator 函数`helloWorldGenerator`，它内部有两个`yield`表达式（`hello`和`world`），即该函数有三个状态：hello，world 和 return 语句（结束执行）。

然后，Generator 函数的调用方法与普通函数一样，也是在函数名后面加上一对圆括号。不同的是，调用 Generator 函数后，该函数并不执行，返回的也不是函数运行结果，而是一个指向内部状态的指针对象，也就是遍历器对象（Iterator Object）。

下一步，必须调用遍历器对象的`next`方法，使得指针移向下一个状态。也就是说，每次调用`next`方法，内部指针就从函数头部或上一次停下来的地方开始执行，直到遇到下一个`yield`表达式（或`return`语句）为止。换言之，Generator 函数是分段执行的，`yield`表达式是暂停执行的标记，而`next`方法可以恢复执行。

```javascript
hw.next()
// { value: 'hello', done: false }

hw.next()
// { value: 'world', done: false }

hw.next()
// { value: 'ending', done: true }

hw.next()
// { value: undefined, done: true }
```

**总结**：调用 Generator 函数，返回一个遍历器对象，代表 Generator 函数的内部指针。以后，每次调用遍历器对象的`next`方法，就会返回一个有着`value`和`done`两个属性的对象。`value`属性表示当前的内部状态的值，是`yield`表达式后面那个表达式的值；`done`属性是一个布尔值，表示是否遍历结束。

ES6 没有规定，`function`关键字与函数名之间的星号，写在哪个位置。这导致下面的写法都能通过。

```javascript
function * foo(x, y) { ··· }
function *foo(x, y) { ··· }
function* foo(x, y) { ··· }
function*foo(x, y) { ··· }
```

由于 Generator 函数仍然是普通函数，所以一般的写法是上面的第三种，即星号紧跟在`function`关键字后面。

代码说明：

* *的位置没有限制

- 生成器函数返回的结果是迭代器对象，调用迭代器对象的 next 方法可以得到yield 语句后的值
- yield 相当于函数的暂停标记，也可以认为是函数的分隔符，每调用一次 next方法，执行一段代码
- next 方法可以传递实参，作为 yield 语句的返回值

#### yield 表达式

Generator 函数返回的遍历器对象，只有调用`next`方法才会遍历下一个内部状态，所以其实提供了一种可以暂停执行的函数。`yield`表达式就是暂停标志。

遍历器对象的`next`方法的运行逻辑如下。

- 遇到`yield`表达式，就暂停执行后面的操作，并将紧跟在`yield`后面的那个表达式的值，作为返回的对象的`value`属性值。
- 下一次调用`next`方法时，再继续往下执行，直到遇到下一个`yield`表达式。
- 如果没有再遇到新的`yield`表达式，就一直运行到函数结束，直到`return`语句为止，并将`return`语句后面的表达式的值，作为返回的对象的`value`属性值。
- 如果该函数没有`return`语句，则返回的对象的`value`属性值为`undefined`。

需要注意的是，`yield`表达式后面的表达式，只有当调用`next`方法、内部指针指向该语句时才会执行，因此等于为 JavaScript 提供了手动的“惰性求值”（Lazy Evaluation）的语法功能。

```javascript
function* gen() {
  yield  123 + 456;
}
```

`yield`后面的表达式`123 + 456`，不会立即求值，只会在`next`方法将指针移到这一句时，才会求值。

`yield`表达式与`return`语句：

- 相似之处在于：都能返回紧跟在语句后面的那个表达式的值。

- 区别在于：

  每次遇到`yield`，函数暂停执行，下一次再从该位置继续向后执行，而`return`语句不具备位置记忆的功能。一个函数里面，只能执行一次（或者说一个）`return`语句，但是可以执行多次（或者说多个）`yield`表达式。

  正常函数只能返回一个值，因为只能执行一次`return`；Generator 函数可以返回一系列的值，因为可以有任意多个`yield`。从另一个角度看，也可以说 Generator 生成了一系列的值



Generator 函数可以不用`yield`表达式，这时就变成了一个单纯的暂缓执行函数。

```javascript
function* f() {
  console.log('执行了！')
}

var generator = f();

setTimeout(function () {
  generator.next()
}, 2000);
```

上面代码中，函数`f`如果是普通函数，在为变量`generator`赋值时就会执行。但是，函数`f`是一个 Generator 函数，就变成只有调用`next`方法时，函数`f`才会执行。

`forEach`方法的参数是一个普通函数，但是在里面使用了`yield`表达式（这个函数里面还使用了`yield*`表达式，详细介绍见后文）。一种修改方法是改用`for`循环。

```javascript
var arr = [1, [[2, 3], 4], [5, 6]];

var flat = function* (a) {
  var length = a.length;
  for (var i = 0; i < length; i++) {
    var item = a[i];
    if (typeof item !== 'number') {
      yield* flat(item);
    } else {
      yield item;
    }
  }
};

for (var f of flat(arr)) {
  console.log(f);
}
// 1, 2, 3, 4, 5, 6
```

```
function * gen(){
    // console.log(111);
    yield '一只没有耳朵';
    // console.log(222);
    yield '一只没有尾部';
    // console.log(333);
    yield '真奇怪';
    // console.log(444);
}

let iterator = gen();
console.log(iterator.next()); //{value: '一只没有耳朵', done: false}
console.log(iterator.next()); //{value: '一只没有尾部', done: false}
console.log(iterator.next()); //{value: '真奇怪', done: false}
console.log(iterator.next()); //{value: undefined, done: true}

// 遍历
for(let v of gen()){
    console.log(v);
                    /*一只没有耳朵
                    一只没有尾部
                    真奇怪*/
}
```

另外，`yield`表达式如果用在另一个表达式之中，必须放在圆括号里面。

```javascript
function* demo() {
  console.log('Hello' + yield); // SyntaxError
  console.log('Hello' + yield 123); // SyntaxError

  console.log('Hello' + (yield)); // OK
  console.log('Hello' + (yield 123)); // OK
}
```

`yield`表达式用作函数参数或放在赋值表达式的右边，可以不加括号。

```javascript
function* demo() {
  foo(yield 'a', yield 'b'); // OK
  let input = yield; // OK
}
```

#### 与 Iterator 接口的关系

任意一个对象的`Symbol.iterator`方法，等于该对象的遍历器生成函数，调用该函数会返回该对象的一个遍历器对象。

由于 Generator 函数就是遍历器生成函数，因此可以把 Generator 赋值给对象的`Symbol.iterator`属性，从而使得该对象具有 Iterator 接口。

```javascript
var myIterable = {};
myIterable[Symbol.iterator] = function* () {
  yield 1;
  yield 2;
  yield 3;
};

[...myIterable] // [1, 2, 3]
```

上面代码中，Generator 函数赋值给`Symbol.iterator`属性，从而使得`myIterable`对象具有了 Iterator 接口，可以被`...`运算符遍历了。

Generator 函数执行后，返回一个遍历器对象。该对象本身也具有`Symbol.iterator`属性，执行后返回自身。

```javascript
function* gen(){
  // some code
}

var g = gen();

g[Symbol.iterator]() === g
// true
```

上面代码中，`gen`是一个 Generator 函数，调用它会生成一个遍历器对象`g`。它的`Symbol.iterator`属性，也是一个遍历器对象生成函数，执行后返回它自己。

#### 生成器函数的参数

`yield`表达式本身没有返回值，或者说总是返回`undefined`。`next`方法可以带一个参数，该参数就会被当作**上一个**`yield`表达式的返回值。

```javascript
function* f() {
  for(var i = 0; true; i++) {
    var reset = yield i;
    if(reset) { i = -1; }
  }
}

var g = f();

g.next() // { value: 0, done: false }
g.next() // { value: 1, done: false }
g.next(true) // { value: 0, done: false }
```

上面代码先定义了一个可以无限运行的 Generator 函数`f`，如果`next`方法没有参数，每次运行到`yield`表达式，变量`reset`的值总是`undefined`。当`next`方法带一个参数`true`时，变量`reset`就被重置为这个参数（即`true`），因此`i`会等于`-1`，下一轮循环就会从`-1`开始递增。

```
function * gen(arg){
    console.log(arg);
    let one = yield 111;
    console.log(one);
    let two = yield 222;
    console.log(two);
    let three = yield 333;
    console.log(three);
}

//执行获取迭代器对象
let iterator = gen('AAA');
console.log(iterator.next());
//next方法可以传入实参
console.log(iterator.next('BBB'));
console.log(iterator.next('CCC'));
console.log(iterator.next('DDD'));
//AAA
//{value: 111, done: false}
//BBB
//{value: 222, done: false}
//CCC
//{value: 333, done: false}
//DDD
//{value: undefined, done: true}
```

Generator 函数从暂停状态到恢复运行，它的上下文状态（context）是不变的。通过`next`方法的参数，就有办法在 Generator 函数开始运行之后，继续向函数体内部注入值。也就是说，可以在 Generator 函数运行的不同阶段，从外部向内部注入不同的值，从而调整函数行为。

```javascript
function* foo(x) {
  var y = 2 * (yield (x + 1));
  var z = yield (y / 3);
  return (x + y + z);
}

var a = foo(5);
a.next() // Object{value:6, done:false}
a.next() // Object{value:NaN, done:false}
a.next() // Object{value:NaN, done:true}

var b = foo(5);
b.next() // { value:6, done:false }
b.next(12) // { value:8, done:false }
b.next(13) // { value:42, done:true }
```

上面代码中，第二次运行`next`方法的时候不带参数，导致 y 的值等于`2 * undefined`（即`NaN`），除以 3 以后还是`NaN`，因此返回对象的`value`属性也等于`NaN`。

如果向`next`方法提供参数，返回结果就完全不一样了。上面代码第一次调用`b`的`next`方法时，返回`x+1`的值`6`；第二次调用`next`方法，将上一次`yield`表达式的值设为`12`，因此`y`等于`24`，返回`y / 3`的值`8`

通过`next`方法的参数，向 Generator 函数内部输入值：

```javascript
function* dataConsumer() {
  console.log('Started');
  console.log(`1. ${yield}`);
  console.log(`2. ${yield}`);
  return 'result';
}

let genObj = dataConsumer();
genObj.next();
// Started
genObj.next('a')
// 1. a
genObj.next('b')
// 2. b
```

如果想要第一次调用`next`方法时，就能够输入值，可以在 Generator 函数外面再包一层。

```javascript
function wrapper(generatorFunction) {
  return function (...args) {
    let generatorObject = generatorFunction(...args);
    generatorObject.next();
    return generatorObject;
  };
}

const wrapped = wrapper(function* () {
  console.log(`First input: ${yield}`);
  return 'DONE';
});

wrapped().next('hello!')
// First input: hello!
```

上面代码中，Generator 函数如果不用`wrapper`先包一层，是无法第一次调用`next`方法，就输入参数的。

#### for...of 循环

`for...of`循环可以自动遍历 Generator 函数运行时生成的`Iterator`对象，且此时不再需要调用`next`方法。

```javascript
function* foo() {
  yield 1;
  yield 2;
  yield 3;
  yield 4;
  yield 5;
  return 6;
}

for (let v of foo()) {
  console.log(v);
}
// 1 2 3 4 5
```

上面代码使用`for...of`循环，依次显示 5 个`yield`表达式的值。这里需要注意，一旦`next`方法的返回对象的`done`属性为`true`，`for...of`循环就会中止，且不包含该返回对象，所以上面代码的`return`语句返回的`6`，不包括在`for...of`循环之中。

除了`for...of`循环以外，扩展运算符（`...`）、解构赋值和`Array.from`方法内部调用的，都是遍历器接口。这意味着，它们都可以将 Generator 函数返回的 Iterator 对象，作为参数。

```javascript
function* numbers () {
  yield 1
  yield 2
  return 3
  yield 4
}

// 扩展运算符
[...numbers()] // [1, 2]

// Array.from 方法
Array.from(numbers()) // [1, 2]

// 解构赋值
let [x, y] = numbers();
x // 1
y // 2

// for...of 循环
for (let n of numbers()) {
  console.log(n)
}
// 1
// 2
```

#### yield* 表达式

如果在 Generator 函数内部，调用另一个 Generator 函数。需要在前者的函数体内部，自己手动完成遍历。

```javascript
function* foo() {
  yield 'a';
  yield 'b';
}

function* bar() {
  yield 'x';
  // 手动遍历 foo()
  for (let i of foo()) {
    console.log(i);
  }
  yield 'y';
}

for (let v of bar()){
  console.log(v);
}
// x
// a
// b
// y
```

ES6 提供了`yield*`表达式，作为解决办法，用来在一个 Generator 函数里面执行另一个 Generator 函数。

```javascript
function* bar() {
  yield 'x';
  yield* foo();
  yield 'y';
}

// 等同于
function* bar() {
  yield 'x';
  yield 'a';
  yield 'b';
  yield 'y';
}

// 等同于
function* bar() {
  yield 'x';
  for (let v of foo()) {
    yield v;
  }
  yield 'y';
}

for (let v of bar()){
  console.log(v);
}
// "x"
// "a"
// "b"
// "y"
```

从语法角度看，如果`yield`表达式后面跟的是一个遍历器对象，需要在`yield`表达式后面加上星号，表明它返回的是一个遍历器对象。这被称为`yield*`表达式。

```javascript
function* gen(){
  yield* ["a", "b", "c"];
}

gen().next() // { value:"a", done:false }
```

上面代码中，`yield`命令后面如果不加星号，返回的是整个数组，加了星号就表示返回的是数组的遍历器对象。

实际上，任何数据结构只要有 Iterator 接口，就可以被`yield*`遍历。

```javascript
let read = (function* () {
  yield 'hello';
  yield* 'hello';
})();

read.next().value // "hello"
read.next().value // "h"
```

上面代码中，`yield`表达式返回整个字符串，`yield*`语句返回单个字符。因为字符串具有 Iterator 接口，所以被`yield*`遍历。

如果被代理的 Generator 函数有`return`语句，那么就可以向代理它的 Generator 函数返回数据。

```javascript
function* foo() {
  yield 2;
  yield 3;
  return "foo";
}

function* bar() {
  yield 1;
  var v = yield* foo();
  console.log("v: " + v);
  yield 4;
}

var it = bar();

it.next()
// {value: 1, done: false}
it.next()
// {value: 2, done: false}
it.next()
// {value: 3, done: false}
it.next();
// "v: foo"
// {value: 4, done: false}
it.next()
// {value: undefined, done: true}
```

上面代码在第四次调用`next`方法的时候，屏幕上会有输出，这是因为函数`foo`的`return`语句，向函数`bar`提供了返回值。

### 13.Promise

Promise 是 ES6 引入的异步编程的新解决方案。语法上 Promise 是一个构造函数，用来封装异步操作并可以获取其成功或失败的结果。

`Promise`对象有以下两个特点：

- 对象的状态不受外界影响。`Promise`对象代表一个异步操作，有三种状态：`pending`（进行中）、`fulfilled`（已成功）和`rejected`（已失败）。只有异步操作的结果，可以决定当前是哪一种状态，任何其他操作都无法改变这个状态。这也是`Promise`这个名字的由来，它的英语意思就是“承诺”，表示其他手段无法改变。
- 一旦状态改变，就不会再变，任何时候都可以得到这个结果。`Promise`对象的状态改变，只有两种可能：从`pending`变为`fulfilled`和从`pending`变为`rejected`。只要这两种情况发生，状态就凝固了，不会再变了，会一直保持这个结果，这时就称为 resolved（已定型）。如果改变已经发生了，你再对`Promise`对象添加回调函数，也会立即得到这个结果。这与事件（Event）完全不同，事件的特点是，如果你错过了它，再去监听，是得不到结果的。

`Promise`也有一些缺点：

- 首先，无法取消`Promise`，一旦新建它就会立即执行，无法中途取消。
- 其次，如果不设置回调函数，`Promise`内部抛出的错误，不会反应到外部。
- 第三，当处于`pending`状态时，无法得知目前进展到哪一个阶段（刚刚开始还是即将完成）。

#### 基本用法

`Promise`构造函数接受一个函数作为参数，该函数的两个参数分别是`resolve`和`reject`。它们是两个函数，由 JavaScript 引擎提供，不用自己部署。

`resolve`函数的作用是，将`Promise`对象的状态从“未完成”变为“成功”（即从 pending 变为 resolved），在异步操作成功时调用，并将异步操作的结果，作为参数传递出去；`reject`函数的作用是，将`Promise`对象的状态从“未完成”变为“失败”（即从 pending 变为 rejected），在异步操作失败时调用，并将异步操作报出的错误，作为参数传递出去。

```javascript
const promise = new Promise(function(resolve, reject) {
  // ... some code

  if (/* 异步操作成功 */){
    resolve(value);
  } else {
    reject(error);
  }
});
```

`Promise`实例生成以后，可以用`then`方法分别指定`resolved`状态和`rejected`状态的回调函数。

```javascript
promise.then(function(value) {
  // success
}, function(error) {
  // failure
});
```

`then`方法可以接受两个回调函数作为参数。第一个回调函数是`Promise`对象的状态变为`resolved`时调用，第二个回调函数是`Promise`对象的状态变为`rejected`时调用。这两个函数都是可选的，不一定要提供。它们都接受`Promise`对象传出的值作为参数。

```javascript
function timeout(ms) {
  return new Promise((resolve, reject) => {
    setTimeout(resolve, ms, 'done');
  });
}

timeout(100).then((value) => {
  console.log(value);
});
```

上面代码中，`timeout`方法返回一个`Promise`实例，表示一段时间以后才会发生的结果。过了指定的时间（`ms`参数）以后，`Promise`实例的状态变为`resolved`，就会触发`then`方法绑定的回调函数。

```javascript
let promise = new Promise(function(resolve, reject) {
  console.log('Promise');
  resolve();
});

promise.then(function() {
  console.log('resolved.');
});

console.log('Hi!');

// Promise
// Hi!
// resolved
```

上面代码中，Promise 新建后立即执行，所以首先输出的是`Promise`。然后，`then`方法指定的回调函数，将在当前脚本所有同步任务执行完才会执行，所以`resolved`最后输出。



如果调用`resolve`函数和`reject`函数时带有参数，那么它们的参数会被传递给回调函数。`reject`函数的参数通常是`Error`对象的实例，表示抛出的错误；`resolve`函数的参数除了正常的值以外，还可能是另一个 Promise 实例，比如像下面这样。

```javascript
const p1 = new Promise(function (resolve, reject) {
  // ...
});

const p2 = new Promise(function (resolve, reject) {
  // ...
  resolve(p1);
})
```

上面代码中，`p1`和`p2`都是 Promise 的实例，但是`p2`的`resolve`方法将`p1`作为参数，即一个异步操作的结果是返回另一个异步操作。

注意，这时`p1`的状态就会传递给`p2`，也就是说，`p1`的状态决定了`p2`的状态。如果`p1`的状态是`pending`，那么`p2`的回调函数就会等待`p1`的状态改变；如果`p1`的状态已经是`resolved`或者`rejected`，那么`p2`的回调函数将会立刻执行。

```javascript
const p1 = new Promise(function (resolve, reject) {
  setTimeout(() => reject(new Error('fail')), 3000)
})

const p2 = new Promise(function (resolve, reject) {
  setTimeout(() => resolve(p1), 1000)
})

p2
  .then(result => console.log(result))
  .catch(error => console.log(error))
// Error: fail
```

上面代码中，`p1`是一个 Promise，3 秒之后变为`rejected`。`p2`的状态在 1 秒之后改变，`resolve`方法返回的是`p1`。由于`p2`返回的是另一个 Promise，导致`p2`自己的状态无效了，由`p1`的状态决定`p2`的状态。所以，后面的`then`语句都变成针对后者（`p1`）。又过了 2 秒，`p1`变为`rejected`，导致触发`catch`方法指定的回调函数。

注意，调用`resolve`或`reject`并不会终结 Promise 的参数函数的执行。

```javascript
new Promise((resolve, reject) => {
  resolve(1);
  console.log(2);
}).then(r => {
  console.log(r);
});
// 2
// 1
```

上面代码中，调用`resolve(1)`以后，后面的`console.log(2)`还是会执行，并且会首先打印出来。这是因为立即 resolved 的 Promise 是在本轮事件循环的末尾执行，总是晚于本轮循环的同步任务。

一般来说，调用`resolve`或`reject`以后，Promise 的使命就完成了，后继操作应该放到`then`方法里面，而不应该直接写在`resolve`或`reject`的后面。所以，最好在它们前面加上`return`语句，这样就不会有意外。

```javascript
new Promise((resolve, reject) => {
  return resolve(1);
  // 后面的语句不会执行
  console.log(2);
})
```



#### Promise封装AJAX

```
// 接口地址: https://api.apiopen.top/getJoke
const p = new Promise((resolve, reject) => {
    //1. 创建对象
    const xhr = new XMLHttpRequest();

    //2. 初始化
    xhr.open("GET", "https://api.apiopen.top/getJ");

    //3. 发送
    xhr.send();

    //4. 绑定事件, 处理响应结果
    xhr.onreadystatechange = function () {
        //判断
        if (xhr.readyState === 4) {
            //判断响应状态码 200-299
            if (xhr.status >= 200 && xhr.status < 300) {
                //表示成功
                resolve(xhr.response);
            } else {
                //如果失败
                reject(xhr.status);
            }
        }
    }
})

//指定回调
p.then(function(value){
    console.log(value);
}, function(reason){
    console.error(reason);
});
```



#### Promise.prototype.then() 

Promise 实例具有`then`方法，也就是说，`then`方法是定义在原型对象`Promise.prototype`上的。它的作用是为 Promise 实例添加状态改变时的回调函数。

`then`方法返回的是一个新的`Promise`实例（注意，不是原来那个`Promise`实例）。因此可以采用链式写法，即`then`方法后面再调用另一个`then`方法。

```javascript
getJSON("/posts.json").then(function(json) {
  return json.post;
}).then(function(post) {
  // ...
});
```

上面的代码使用`then`方法，依次指定了两个回调函数。**第一个回调函数完成以后，会将返回结果作为参数，传入第二个回调函数**。

采用链式的`then`，可以指定一组按照次序调用的回调函数。这时，前一个回调函数，有可能返回的还是一个`Promise`对象（即有异步操作），这时后一个回调函数，就会等待该`Promise`对象的状态发生变化，才会被调用。

```javascript
getJSON("/post/1.json").then(function(post) {
  return getJSON(post.commentURL);
}).then(function (comments) {
  console.log("resolved: ", comments);
}, function (err){
  console.log("rejected: ", err);
});
```

第一个`then`方法**指定的回调函数**，返回的是另一个`Promise`对象。这时，第二个`then`方法指定的回调函数，就会等待这个新的`Promise`对象状态发生变化。如果变为`resolved`，就调用第一个回调函数，如果状态变为`rejected`，就调用第二个回调函数。

或者采用箭头函数：

```javascript
getJSON("/post/1.json").then(
  post => getJSON(post.commentURL)
).then(
  comments => console.log("resolved: ", comments),
  err => console.log("rejected: ", err)
);
```

```
//创建 promise 对象
const p = new Promise((resolve, reject)=>{
    setTimeout(()=>{
        resolve('用户数据');
        // reject('出错啦');
    }, 1000)
});

//调用 then 方法  then方法的返回结果是 Promise 对象, 对象状态由回调函数的执行结果决定
//1. 如果回调函数中返回的结果是 非 promise 类型的属性, 状态为成功, 返回值为对象的成功的值

// const result = p.then(value => {
//     console.log(value);
//     //1. 非 promise 类型的属性
//     // return 'iloveyou';
//     //2. 是 promise 对象
//     // return new Promise((resolve, reject)=>{
//     //     // resolve('ok');
//     //     reject('error');
//     // });
//     //3. 抛出错误
//     // throw new Error('出错啦!');
//     throw '出错啦!';
// }, reason=>{
//     console.warn(reason);
// });

//链式调用
p.then(value=>{

}).then(value=>{

});
```

#### Promise.prototype.catch() 

`Promise.prototype.catch()`方法是`.then(null, rejection)`或`.then(undefined, rejection)`的别名，用于指定发生错误时的回调函数。

```javascript
getJSON('/posts.json').then(function(posts) {
  // ...
}).catch(function(error) {
  // 处理 getJSON 和 前一个回调函数运行时发生的错误
  console.log('发生错误！', error);
});
```

上面代码中，`getJSON()`方法返回一个 Promise 对象，如果该对象状态变为`resolved`，则会调用`then()`方法指定的回调函数；如果异步操作抛出错误，状态就会变为`rejected`，就会调用`catch()`方法指定的回调函数，处理这个错误。另外，`then()`方法指定的回调函数，如果运行中抛出错误，也会被`catch()`方法捕获。

```javascript
p.then((val) => console.log('fulfilled:', val))
  .catch((err) => console.log('rejected', err));

// 等同于
p.then((val) => console.log('fulfilled:', val))
  .then(null, (err) => console.log("rejected:", err));
```

`promise`抛出一个错误，就被`catch()`方法指定的回调函数捕获：

```javascript
const promise = new Promise(function(resolve, reject) {
  throw new Error('test');
});
promise.catch(function(error) {
  console.log(error);
});
// Error: test
```

与下面两种写法等价：

```javascript
// 写法一
const promise = new Promise(function(resolve, reject) {
  try {
    throw new Error('test');
  } catch(e) {
    reject(e);
  }
});
promise.catch(function(error) {
  console.log(error);
});

// 写法二
const promise = new Promise(function(resolve, reject) {
  reject(new Error('test'));
});
promise.catch(function(error) {
  console.log(error);
});
```

可以发现`reject()`方法的作用，等同于抛出错误



如果 Promise 状态已经变成`resolved`，再抛出错误是无效的。因为 Promise 的状态一旦改变，就永久保持该状态，不会再变了。

```javascript
const promise = new Promise(function(resolve, reject) {
  resolve('ok');
  throw new Error('test');
});
promise
  .then(function(value) { console.log(value) })
  .catch(function(error) { console.log(error) });
// ok
```



Promise 对象的错误具有“冒泡”性质，会一直向后传递，直到被捕获为止。也就是说，错误总是会被下一个`catch`语句捕获。

```javascript
getJSON('/post/1.json').then(function(post) {
  return getJSON(post.commentURL);
}).then(function(comments) {
  // some code
}).catch(function(error) {
  // 处理前面三个Promise产生的错误
});
```

上面代码中，一共有三个 Promise 对象：一个由`getJSON()`产生，两个由`then()`产生。它们之中任何一个抛出的错误，都会被最后一个`catch()`捕获。

一般来说，不要在`then()`方法里面定义 Reject 状态的回调函数（即`then`的第二个参数），总是使用`catch`方法。

```javascript
// bad
promise
  .then(function(data) {
    // success
  }, function(err) {
    // error
  });

// good
promise
  .then(function(data) { //cb
    // success
  })
  .catch(function(err) {
    // error
  });
```

上面代码中，第二种写法要好于第一种写法，理由是第二种写法可以捕获前面`then`方法执行中的错误，也更接近同步的写法（`try/catch`）。因此，建议总是使用`catch()`方法，而不使用`then()`方法的第二个参数。



跟传统的`try/catch`的区别：如果没有使用`catch()`方法指定错误处理的回调函数，Promise 对象抛出的错误不会传递到外层代码，即不会有任何反应。

```javascript
const someAsyncThing = function() {
  return new Promise(function(resolve, reject) {
    // 下面一行会报错，因为x没有声明
    resolve(x + 2);
  });
};

someAsyncThing().then(function() {
  console.log('everything is great');
});

setTimeout(() => { console.log(123) }, 2000);
// Uncaught (in promise) ReferenceError: x is not defined
// 123
```

上面代码中，`someAsyncThing()`函数产生的 Promise 对象，内部有语法错误。浏览器运行到这一行，会打印出错误提示`ReferenceError: x is not defined`，但是不会退出进程、终止脚本执行，2 秒之后还是会输出`123`。这就是说，Promise 内部的错误不会影响到 Promise 外部的代码，通俗的说法就是“Promise 会吃掉错误”。

一般总是建议，Promise 对象后面要跟`catch()`方法，这样可以处理 Promise 内部发生的错误。`catch()`方法返回的还是一个 Promise 对象，因此后面还可以接着调用`then()`方法。

```javascript
const someAsyncThing = function() {
  return new Promise(function(resolve, reject) {
    // 下面一行会报错，因为x没有声明
    resolve(x + 2);
  });
};

someAsyncThing()
.catch(function(error) {
  console.log('oh no', error);
})
.then(function() {
  console.log('carry on');
});
// oh no [ReferenceError: x is not defined]
// carry on
```

### 14.Set

ES6 提供了新的数据结构 Set。它类似于数组，但是成员的值都是唯一的，没有重复的值。

`Set`本身是一个构造函数，用来生成 Set 数据结构。

```javascript
const s = new Set();

[2, 3, 5, 4, 5, 2, 2].forEach(x => s.add(x));

for (let i of s) {
  console.log(i);
}
// 2 3 5 4
```

`Set`函数可以接受一个数组（或者具有 iterable 接口的其他数据结构）作为参数，用来初始化。

```javascript
// 例一
const set = new Set([1, 2, 3, 4, 4]);
[...set]
// [1, 2, 3, 4]

// 例二
const items = new Set([1, 2, 3, 4, 5, 5, 5, 5]);
items.size // 5

// 例三
const set = new Set(document.querySelectorAll('div'));
set.size // 56

// 类似于
const set = new Set();
document
 .querySelectorAll('div')
 .forEach(div => set.add(div));
set.size // 56
```

去除数组重复成员的方法：

```javascript
// 去除数组的重复成员
[...new Set(array)]
```

去除字符串里面的重复字符：

```javascript
[...new Set('ababbc')].join('')
// "abc"
```

 Set 内部，两个`NaN`是相等的：

```javascript
let set = new Set();
let a = NaN;
let b = NaN;
set.add(a);
set.add(b);
set // Set {NaN}
```

两个对象总是不相等的：

```javascript
let set = new Set();

set.add({});
set.size // 1

set.add({});
set.size // 2
```

#### Set 实例的属性和方法

Set 结构的实例有以下属性。

- `Set.prototype.constructor`：构造函数，默认就是`Set`函数。
- `Set.prototype.size`：返回`Set`实例的成员总数。

Set 实例的方法分为两大类：操作方法（用于操作数据）和遍历方法（用于遍历成员）。下面先介绍四个操作方法。

- `Set.prototype.add(value)`：添加某个值，返回 Set 结构本身。
- `Set.prototype.delete(value)`：删除某个值，返回一个布尔值，表示删除是否成功。
- `Set.prototype.has(value)`：返回一个布尔值，表示该值是否为`Set`的成员。
- `Set.prototype.clear()`：清除所有成员，没有返回值。

上面这些属性和方法的实例如下。

```javascript
s.add(1).add(2).add(2);
// 注意2被加入了两次

s.size // 2

s.has(1) // true
s.has(2) // true
s.has(3) // false

s.delete(2);
s.has(2) // false
```

下面是一个对比，看看在判断是否包括一个键上面，`Object`结构和`Set`结构的写法不同。

```javascript
// 对象的写法
const properties = {
  'width': 1,
  'height': 1
};

if (properties[someName]) {
  // do something
}

// Set的写法
const properties = new Set();

properties.add('width');
properties.add('height');

if (properties.has(someName)) {
  // do something
}
```

`Array.from`方法可以将 Set 结构转为数组。

```javascript
const items = new Set([1, 2, 3, 4, 5]);
const array = Array.from(items);
```

这就提供了去除数组重复成员的另一种方法。

```javascript
function dedupe(array) {
  return Array.from(new Set(array));
}

dedupe([1, 1, 2, 3]) // [1, 2, 3]
```

#### 遍历操作

Set 结构的实例有四个遍历方法，可以用于遍历成员。

- `Set.prototype.keys()`：返回键名的遍历器
- `Set.prototype.values()`：返回键值的遍历器
- `Set.prototype.entries()`：返回键值对的遍历器
- `Set.prototype.forEach()`：使用回调函数遍历每个成员

需要特别指出的是，`Set`的遍历顺序就是插入顺序。这个特性有时非常有用，比如使用 Set 保存一个回调函数列表，调用时就能保证按照添加顺序调用。

**（1）`keys()`，`values()`，`entries()`**

`keys`方法、`values`方法、`entries`方法返回的都是遍历器对象（详见《Iterator 对象》一章）。由于 Set 结构没有键名，只有键值（或者说键名和键值是同一个值），所以`keys`方法和`values`方法的行为完全一致。

```javascript
let set = new Set(['red', 'green', 'blue']);

for (let item of set.keys()) {
  console.log(item);
}
// red
// green
// blue

for (let item of set.values()) {
  console.log(item);
}
// red
// green
// blue

for (let item of set.entries()) {
  console.log(item);
}
// ["red", "red"]
// ["green", "green"]
// ["blue", "blue"]
```

上面代码中，`entries`方法返回的遍历器，同时包括键名和键值，所以每次输出一个数组，它的两个成员完全相等。

Set 结构的实例默认可遍历，它的默认遍历器生成函数就是它的`values`方法。

```javascript
Set.prototype[Symbol.iterator] === Set.prototype.values
// true
```

这意味着，可以省略`values`方法，直接用`for...of`循环遍历 Set。

```javascript
let set = new Set(['red', 'green', 'blue']);

for (let x of set) {
  console.log(x);
}
// red
// green
// blue
```

**（2）`forEach()`**

Set 结构的实例与数组一样，也拥有`forEach`方法，用于对每个成员执行某种操作，没有返回值。

```javascript
let set = new Set([1, 4, 9]);
set.forEach((value, key) => console.log(key + ' : ' + value))
// 1 : 1
// 4 : 4
// 9 : 9
```

上面代码说明，`forEach`方法的参数就是一个处理函数。该函数的参数与数组的`forEach`一致，依次为键值、键名、集合本身（上例省略了该参数）。这里需要注意，Set 结构的键名就是键值（两者是同一个值），因此第一个参数与第二个参数的值永远都是一样的。

另外，`forEach`方法还可以有第二个参数，表示绑定处理函数内部的`this`对象。

**（3）遍历的应用**

扩展运算符（`...`）内部使用`for...of`循环，所以也可以用于 Set 结构。

```javascript
let set = new Set(['red', 'green', 'blue']);
let arr = [...set];
// ['red', 'green', 'blue']
```

扩展运算符和 Set 结构相结合，就可以去除数组的重复成员。

```javascript
let arr = [3, 5, 2, 2, 5, 5];
let unique = [...new Set(arr)];
// [3, 5, 2]
```

而且，数组的`map`和`filter`方法也可以间接用于 Set 了。

```javascript
let set = new Set([1, 2, 3]);
set = new Set([...set].map(x => x * 2));
// 返回Set结构：{2, 4, 6}

let set = new Set([1, 2, 3, 4, 5]);
set = new Set([...set].filter(x => (x % 2) == 0));
// 返回Set结构：{2, 4}
```

因此使用 Set 可以很容易地实现并集（Union）、交集（Intersect）和差集（Difference）。

```javascript
let a = new Set([1, 2, 3]);
let b = new Set([4, 3, 2]);

// 并集
let union = new Set([...a, ...b]);
// Set {1, 2, 3, 4}

// 交集
let intersect = new Set([...a].filter(x => b.has(x)));
// set {2, 3}

// （a 相对于 b 的）差集
let difference = new Set([...a].filter(x => !b.has(x)));
// Set {1}
```

如果想在遍历操作中，同步改变原来的 Set 结构，目前没有直接的方法，但有两种变通方法。一种是利用原 Set 结构映射出一个新的结构，然后赋值给原来的 Set 结构；另一种是利用`Array.from`方法。

```javascript
// 方法一
let set = new Set([1, 2, 3]);
set = new Set([...set].map(val => val * 2));
// set的值是2, 4, 6

// 方法二
let set = new Set([1, 2, 3]);
set = new Set(Array.from(set, val => val * 2));
// set的值是2, 4, 6
```

上面代码提供了两种方法，直接在遍历操作中改变原来的 Set 结构。

#### WeakSet

WeakSet 结构与 Set 类似，也是不重复的值的集合。但是，它与 Set 有两个区别。

- 首先，WeakSet 的成员只能是对象，而不能是其他类型的值。

```javascript
const ws = new WeakSet();
ws.add(1)
// TypeError: Invalid value used in weak set
ws.add(Symbol())
// TypeError: invalid value used in weak set
```



- 其次，WeakSet 中的对象都是弱引用，即垃圾回收机制不考虑 WeakSet 对该对象的引用，也就是说，如果其他对象都不再引用该对象，那么垃圾回收机制会自动回收该对象所占用的内存，不考虑该对象还存在于 WeakSet 之中。

由于上面这个特点，WeakSet 的成员是不适合引用的，因为它会随时消失。另外，由于 WeakSet 内部有多少个成员，取决于垃圾回收机制有没有运行，运行前后很可能成员个数是不一样的，而垃圾回收机制何时运行是不可预测的，因此 ES6 规定 WeakSet 不可遍历。

**语法**：

WeakSet 是一个构造函数，可以使用`new`命令，创建 WeakSet 数据结构。

```javascript
const ws = new WeakSet();
```

作为构造函数，WeakSet 可以接受一个数组或类似数组的对象作为参数。（实际上，任何具有 Iterable 接口的对象，都可以作为 WeakSet 的参数。）该数组的所有成员，都会自动成为 WeakSet 实例对象的成员。

```javascript
const a = [[1, 2], [3, 4]];
const ws = new WeakSet(a);
// WeakSet {[1, 2], [3, 4]}
```

上面代码中，`a`是一个数组，它有两个成员，也都是数组。将`a`作为 WeakSet 构造函数的参数，`a`的成员会自动成为 WeakSet 的成员。

注意，是`a`数组的成员成为 WeakSet 的成员，而不是`a`数组本身。这意味着，数组的成员只能是对象。

```javascript
const b = [3, 4];
const ws = new WeakSet(b);
// Uncaught TypeError: Invalid value used in weak set(…)
```

上面代码中，数组`b`的成员不是对象，加入 WeakSet 就会报错。

WeakSet 结构有以下三个方法。

- **WeakSet.prototype.add(value)**：向 WeakSet 实例添加一个新成员。
- **WeakSet.prototype.delete(value)**：清除 WeakSet 实例的指定成员。
- **WeakSet.prototype.has(value)**：返回一个布尔值，表示某个值是否在 WeakSet 实例之中。



```javascript
const ws = new WeakSet();
const obj = {};
const foo = {};

ws.add(window);
ws.add(obj);

ws.has(window); // true
ws.has(foo);    // false

ws.delete(window);
ws.has(window);    // false
```

WeakSet 没有`size`属性，没有办法遍历它的成员。

```javascript
ws.size // undefined
ws.forEach // undefined

ws.forEach(function(item){ console.log('WeakSet has ' + item)})
// TypeError: undefined is not a function
```



WeakSet 不能遍历，是因为成员都是弱引用，随时可能消失，遍历机制无法保证成员的存在，很可能刚刚遍历结束，成员就取不到了。WeakSet 的一个用处，是储存 DOM 节点，而不用担心这些节点从文档移除时，会引发内存泄漏。



```javascript
const foos = new WeakSet()
class Foo {
  constructor() {
    foos.add(this)
  }
  method () {
    if (!foos.has(this)) {
      throw new TypeError('Foo.prototype.method 只能在Foo的实例上调用！');
    }
  }
}
```

上面代码保证了`Foo`的实例方法，只能在`Foo`的实例上调用。这里使用 WeakSet 的好处是，`foos`对实例的引用，不会被计入内存回收机制，所以删除实例的时候，不用考虑`foos`，也不会出现内存泄漏。

### 15.Map

JavaScript 的对象（Object），本质上是键值对的集合（Hash 结构），但是传统上只能用字符串当作键。这给它的使用带来了很大的限制。

ES6 提供了 Map 数据结构。它类似于对象，也是键值对的集合，但是“键”的范围不限于字符串，各种类型的值（包括对象）都可以当作键。也就是说，Object 结构提供了“字符串—值”的对应，Map 结构提供了“值—值”的对应，是一种更完善的 Hash 结构实现。如果你需要“键值对”的数据结构，Map 比 Object 更合适。

使用 Map 结构的`set`方法，将对象`o`当作`m`的一个键，然后又使用`get`方法读取这个键，接着使用`delete`方法删除了这个键：

```javascript
const m = new Map();
const o = {p: 'Hello World'};

m.set(o, 'content')
m.get(o) // "content"

m.has(o) // true
m.delete(o) // true
m.has(o) // false
```



Map 也可以接受一个数组作为参数。该数组的成员是一个个表示键值对的数组。

```javascript
const map = new Map([
  ['name', '张三'],
  ['title', 'Author']
]);

map.size // 2
map.has('name') // true
map.get('name') // "张三"
map.has('title') // true
map.get('title') // "Author"
```

上面代码在新建 Map 实例时，就指定了两个键`name`和`title`。

`Map`构造函数接受数组作为参数，实际上执行的是下面的算法。

```javascript
const items = [
  ['name', '张三'],
  ['title', 'Author']
];

const map = new Map();

items.forEach(
  ([key, value]) => map.set(key, value)
);
```

事实上，不仅仅是数组，任何具有 Iterator 接口、且每个成员都是一个双元素的数组的数据结构都可以当作`Map`构造函数的参数。这就是说，`Set`和`Map`都可以用来生成新的 Map。

```javascript
const set = new Set([
  ['foo', 1],
  ['bar', 2]
]);
const m1 = new Map(set);
m1.get('foo') // 1

const m2 = new Map([['baz', 3]]);
const m3 = new Map(m2);
m3.get('baz') // 3
```



如果对同一个键多次赋值，后面的值将覆盖前面的值：

```javascript
const map = new Map();

map
.set(1, 'aaa')
.set(1, 'bbb');

map.get(1) // "bbb"
```



如果读取一个未知的键，则返回`undefined`：

```javascript
new Map().get('asfddfsasadf')
// undefined
```

**注意**，只有对同一个对象的引用，Map 结构才将其视为同一个键。这一点要非常小心。

```javascript
const map = new Map();

map.set(['a'], 555);
map.get(['a']) // undefined
```

上面代码的`set`和`get`方法，表面是针对同一个键，但实际上这是两个不同的数组实例，内存地址是不一样的，因此`get`方法无法读取该键，返回`undefined`。

同理，同样的值的两个实例，在 Map 结构中被视为两个键。

```javascript
const map = new Map();

const k1 = ['a'];
const k2 = ['a'];

map
.set(k1, 111)
.set(k2, 222);

map.get(k1) // 111
map.get(k2) // 222
```

上面代码中，变量`k1`和`k2`的值是一样的，但是它们在 Map 结构中被视为两个键。

由上可知，Map 的键实际上是跟内存地址绑定的，只要内存地址不一样，就视为两个键。这就解决了同名属性碰撞（clash）的问题，我们扩展别人的库的时候，如果使用对象作为键名，就不用担心自己的属性与原作者的属性同名。

如果 Map 的键是一个简单类型的值（数字、字符串、布尔值），则只要两个值严格相等，Map 将其视为一个键，比如`0`和`-0`就是一个键，布尔值`true`和字符串`true`则是两个不同的键。另外，`undefined`和`null`也是两个不同的键。虽然`NaN`不严格相等于自身，但 Map 将其视为同一个键。

```javascript
let map = new Map();

map.set(-0, 123);
map.get(+0) // 123

map.set(true, 1);
map.set('true', 2);
map.get(true) // 1

map.set(undefined, 3);
map.set(null, 4);
map.get(undefined) // 3

map.set(NaN, 123);
map.get(NaN) // 123
```

#### 实例的属性和操作方法

Map 结构的实例有以下属性和操作方法。

**（1）size 属性**

`size`属性返回 Map 结构的成员总数。

```javascript
const map = new Map();
map.set('foo', true);
map.set('bar', false);

map.size // 2
```

**（2）Map.prototype.set(key, value)**

`set`方法设置键名`key`对应的键值为`value`，然后返回整个 Map 结构。如果`key`已经有值，则键值会被更新，否则就新生成该键。

```javascript
const m = new Map();

m.set('edition', 6)        // 键是字符串
m.set(262, 'standard')     // 键是数值
m.set(undefined, 'nah')    // 键是 undefined
```

`set`方法返回的是当前的`Map`对象，因此可以采用链式写法。

```javascript
let map = new Map()
  .set(1, 'a')
  .set(2, 'b')
  .set(3, 'c');
```

**（3）Map.prototype.get(key)**

`get`方法读取`key`对应的键值，如果找不到`key`，返回`undefined`。

```javascript
const m = new Map();

const hello = function() {console.log('hello');};
m.set(hello, 'Hello ES6!') // 键是函数

m.get(hello)  // Hello ES6!
```

**（4）Map.prototype.has(key)**

`has`方法返回一个布尔值，表示某个键是否在当前 Map 对象之中。

```javascript
const m = new Map();

m.set('edition', 6);
m.set(262, 'standard');
m.set(undefined, 'nah');

m.has('edition')     // true
m.has('years')       // false
m.has(262)           // true
m.has(undefined)     // true
```

**（5）Map.prototype.delete(key)**

`delete`方法删除某个键，返回`true`。如果删除失败，返回`false`。

```javascript
const m = new Map();
m.set(undefined, 'nah');
m.has(undefined)     // true

m.delete(undefined)
m.has(undefined)       // false
```

**（6）Map.prototype.clear()**

`clear`方法清除所有成员，没有返回值。

```javascript
let map = new Map();
map.set('foo', true);
map.set('bar', false);

map.size // 2
map.clear()
map.size // 0
```

#### 遍历方法

Map 结构原生提供三个遍历器生成函数和一个遍历方法。

- `Map.prototype.keys()`：返回键名的遍历器。
- `Map.prototype.values()`：返回键值的遍历器。
- `Map.prototype.entries()`：返回所有成员的遍历器。
- `Map.prototype.forEach()`：遍历 Map 的所有成员。

需要特别注意的是，Map 的遍历顺序就是插入顺序。

```javascript
const map = new Map([
  ['F', 'no'],
  ['T',  'yes'],
]);

for (let key of map.keys()) {
  console.log(key);
}
// "F"
// "T"

for (let value of map.values()) {
  console.log(value);
}
// "no"
// "yes"

for (let item of map.entries()) {
  console.log(item[0], item[1]);
}
// "F" "no"
// "T" "yes"

// 或者
for (let [key, value] of map.entries()) {
  console.log(key, value);
}
// "F" "no"
// "T" "yes"

// 等同于使用map.entries()
for (let [key, value] of map) {
  console.log(key, value);
}
// "F" "no"
// "T" "yes"
```

上面代码最后的那个例子，表示 Map 结构的默认遍历器接口（`Symbol.iterator`属性），就是`entries`方法。

```javascript
map[Symbol.iterator] === map.entries
// true
```

Map 结构转为数组结构，比较快速的方法是使用扩展运算符（`...`）。

```javascript
const map = new Map([
  [1, 'one'],
  [2, 'two'],
  [3, 'three'],
]);

[...map.keys()]
// [1, 2, 3]

[...map.values()]
// ['one', 'two', 'three']

[...map.entries()]
// [[1,'one'], [2, 'two'], [3, 'three']]

[...map]
// [[1,'one'], [2, 'two'], [3, 'three']]
```

结合数组的`map`方法、`filter`方法，可以实现 Map 的遍历和过滤（Map 本身没有`map`和`filter`方法）。

```javascript
const map0 = new Map()
  .set(1, 'a')
  .set(2, 'b')
  .set(3, 'c');

const map1 = new Map(
  [...map0].filter(([k, v]) => k < 3)
);
// 产生 Map 结构 {1 => 'a', 2 => 'b'}

const map2 = new Map(
  [...map0].map(([k, v]) => [k * 2, '_' + v])
    );
// 产生 Map 结构 {2 => '_a', 4 => '_b', 6 => '_c'}
```

此外，Map 还有一个`forEach`方法，与数组的`forEach`方法类似，也可以实现遍历。

```javascript
map.forEach(function(value, key, map) {
  console.log("Key: %s, Value: %s", key, value);
});
```

`forEach`方法还可以接受第二个参数，用来绑定`this`。

```javascript
const reporter = {
  report: function(key, value) {
    console.log("Key: %s, Value: %s", key, value);
  }
};

map.forEach(function(value, key, map) {
  this.report(key, value);
}, reporter);
```

上面代码中，`forEach`方法的回调函数的`this`，就指向`reporter`。

#### 与其他数据结构的互相转换

**（1）Map 转为数组**

前面已经提过，Map 转为数组最方便的方法，就是使用扩展运算符（`...`）。

```javascript
const myMap = new Map()
  .set(true, 7)
  .set({foo: 3}, ['abc']);
[...myMap]
// [ [ true, 7 ], [ { foo: 3 }, [ 'abc' ] ] ]
```

**（2）数组 转为 Map**

将数组传入 Map 构造函数，就可以转为 Map。

```javascript
new Map([
  [true, 7],
  [{foo: 3}, ['abc']]
])
// Map {
//   true => 7,
//   Object {foo: 3} => ['abc']
// }
```

**（3）Map 转为对象**

如果所有 Map 的键都是字符串，它可以无损地转为对象。

```javascript
function strMapToObj(strMap) {
  let obj = Object.create(null);
  for (let [k,v] of strMap) {
    obj[k] = v;
  }
  return obj;
}

const myMap = new Map()
  .set('yes', true)
  .set('no', false);
strMapToObj(myMap)
// { yes: true, no: false }
```

如果有非字符串的键名，那么这个键名会被转成字符串，再作为对象的键名。

**（4）对象转为 Map**

对象转为 Map 可以通过`Object.entries()`。

```javascript
let obj = {"a":1, "b":2};
let map = new Map(Object.entries(obj));
```

此外，也可以自己实现一个转换函数。

```javascript
function objToStrMap(obj) {
  let strMap = new Map();
  for (let k of Object.keys(obj)) {
    strMap.set(k, obj[k]);
  }
  return strMap;
}

objToStrMap({yes: true, no: false})
// Map {"yes" => true, "no" => false}
```

**（5）Map 转为 JSON**

Map 转为 JSON 要区分两种情况。一种情况是，Map 的键名都是字符串，这时可以选择转为对象 JSON。

```javascript
function strMapToJson(strMap) {
  return JSON.stringify(strMapToObj(strMap));
}

let myMap = new Map().set('yes', true).set('no', false);
strMapToJson(myMap)
// '{"yes":true,"no":false}'
```

另一种情况是，Map 的键名有非字符串，这时可以选择转为数组 JSON。

```javascript
function mapToArrayJson(map) {
  return JSON.stringify([...map]);
}

let myMap = new Map().set(true, 7).set({foo: 3}, ['abc']);
mapToArrayJson(myMap)
// '[[true,7],[{"foo":3},["abc"]]]'
```

**（6）JSON 转为 Map**

JSON 转为 Map，正常情况下，所有键名都是字符串。

```javascript
function jsonToStrMap(jsonStr) {
  return objToStrMap(JSON.parse(jsonStr));
}

jsonToStrMap('{"yes": true, "no": false}')
// Map {'yes' => true, 'no' => false}
```

但是，有一种特殊情况，整个 JSON 就是一个数组，且每个数组成员本身，又是一个有两个成员的数组。这时，它可以一一对应地转为 Map。这往往是 Map 转为数组 JSON 的逆操作。

```javascript
function jsonToMap(jsonStr) {
  return new Map(JSON.parse(jsonStr));
}

jsonToMap('[[true,7],[{"foo":3},["abc"]]]')
// Map {true => 7, Object {foo: 3} => ['abc']}
```

#### WeakMap

`WeakMap`结构与`Map`结构类似，也是用于生成键值对的集合。

```javascript
// WeakMap 可以使用 set 方法添加成员
const wm1 = new WeakMap();
const key = {foo: 1};
wm1.set(key, 2);
wm1.get(key) // 2

// WeakMap 也可以接受一个数组，
// 作为构造函数的参数
const k1 = [1, 2, 3];
const k2 = [4, 5, 6];
const wm2 = new WeakMap([[k1, 'foo'], [k2, 'bar']]);
wm2.get(k2) // "bar"
```

`WeakMap`与`Map`的区别有两点。

- `WeakMap`只接受对象作为键名（`null`除外），不接受其他类型的值作为键名。

```javascript
const map = new WeakMap();
map.set(1, 2)
// TypeError: 1 is not an object!
map.set(Symbol(), 2)
// TypeError: Invalid value used as weak map key
map.set(null, 2)
// TypeError: Invalid value used as weak map key
```

- 其次，`WeakMap`的键名所指向的对象，不计入垃圾回收机制。

`WeakMap`的设计目的在于，有时我们想在某个对象上面存放一些数据，但是这会形成对于这个对象的引用。请看下面的例子。

```javascript
const e1 = document.getElementById('foo');
const e2 = document.getElementById('bar');
const arr = [
  [e1, 'foo 元素'],
  [e2, 'bar 元素'],
];
```

上面代码中，`e1`和`e2`是两个对象，我们通过`arr`数组对这两个对象添加一些文字说明。这就形成了`arr`对`e1`和`e2`的引用。

一旦不再需要这两个对象，我们就必须手动删除这个引用，否则垃圾回收机制就不会释放`e1`和`e2`占用的内存。

```javascript
// 不需要 e1 和 e2 的时候
// 必须手动删除引用
arr [0] = null;
arr [1] = null;
```

上面这样的写法显然很不方便。一旦忘了写，就会造成内存泄露。

WeakMap 就是为了解决这个问题而诞生的，它的键名所引用的对象都是弱引用，即垃圾回收机制不将该引用考虑在内。因此，只要所引用的对象的其他引用都被清除，垃圾回收机制就会释放该对象所占用的内存。也就是说，一旦不再需要，WeakMap 里面的键名对象和所对应的键值对会自动消失，不用手动删除引用。

基本上，如果你要往对象上添加数据，又不想干扰垃圾回收机制，就可以使用 WeakMap。一个典型应用场景是，在网页的 DOM 元素上添加数据，就可以使用`WeakMap`结构。当该 DOM 元素被清除，其所对应的`WeakMap`记录就会自动被移除。

```javascript
const wm = new WeakMap();

const element = document.getElementById('example');

wm.set(element, 'some information');
wm.get(element) // "some information"
```

总之，`WeakMap`的专用场合就是，它的键所对应的对象，可能会在将来消失。`WeakMap`结构有助于防止内存泄漏。

注意，WeakMap 弱引用的只是键名，而不是键值。键值依然是正常引用。

```javascript
const wm = new WeakMap();
let key = {};
let obj = {foo: 1};

wm.set(key, obj);
obj = null;
wm.get(key)
// Object {foo: 1}
```

键值`obj`是正常引用。所以，即使在 WeakMap 外部消除了`obj`的引用，WeakMap 内部的引用依然存在。

**WeakMap 的语法**：

WeakMap 与 Map 在 API 上的区别主要是两个，一是没有遍历操作（即没有`keys()`、`values()`和`entries()`方法），也没有`size`属性。因为没有办法列出所有键名，某个键名是否存在完全不可预测，跟垃圾回收机制是否运行相关。这一刻可以取到键名，下一刻垃圾回收机制突然运行了，这个键名就没了，为了防止出现不确定性，就统一规定不能取到键名。二是无法清空，即不支持`clear`方法。因此，`WeakMap`只有四个方法可用：`get()`、`set()`、`has()`、`delete()`。

```javascript
const wm = new WeakMap();

// size、forEach、clear 方法都不存在
wm.size // undefined
wm.forEach // undefined
wm.clear // undefined
```

### 16.Class

ES6 提供了更接近传统语言的写法，引入了 Class（类）这个概念，作为对象的模板。通过`class`关键字，可以定义类。

基本上，ES6 的`class`可以看作只是一个语法糖，它的绝大部分功能，ES5 都可以做到，新的`class`写法只是让对象原型的写法更加清晰、更像面向对象编程的语法而已。

- class 声明类
- constructor 定义构造函数初始化
- extends 继承父类
- super 调用父级构造方法
- static 定义静态方法和属性
- 父类方法可以重写

```javascript
function Point(x, y) {
  this.x = x;
  this.y = y;
}

Point.prototype.toString = function () {
  return '(' + this.x + ', ' + this.y + ')';
};

var p = new Point(1, 2);
```

用 ES6 的`class`改写：

```javascript
class Point {
  constructor(x, y) {
    this.x = x;
    this.y = y;
  }

  toString() {
    return '(' + this.x + ', ' + this.y + ')';
  }
}
```

ES6 的类，可以看作构造函数的另一种写法。

```javascript
class Point {
  // ...
}

typeof Point // "function"
Point === Point.prototype.constructor // true
```

类的所有方法都定义在类的`prototype`属性上面。

```javascript
class Point {
  constructor() {
    // ...
  }

  toString() {
    // ...
  }

  toValue() {
    // ...
  }
}

// 等同于

Point.prototype = {
  constructor() {},
  toString() {},
  toValue() {},
};
```

```javascript
class B {}
const b = new B();

b.constructor === B.prototype.constructor // true
```

上面代码中，`b`是`B`类的实例，它的`constructor()`方法就是`B`类原型的`constructor()`方法。

由于类的方法都定义在`prototype`对象上面，所以类的新方法可以添加在`prototype`对象上面。`Object.assign()`方法可以很方便地一次向类添加多个方法。

```javascript
class Point {
  constructor(){
    // ...
  }
}

Object.assign(Point.prototype, {
  toString(){},
  toValue(){}
});
```

`prototype`对象的`constructor()`属性，直接指向“类”的本身，这与 ES5 的行为是一致的。

```javascript
Point.prototype.constructor === Point // true
```

另外，类的内部所有定义的方法，都是不可枚举的（non-enumerable）。

```javascript
class Point {
  constructor(x, y) {
    // ...
  }

  toString() {
    // ...
  }
}

Object.keys(Point.prototype)
// []
Object.getOwnPropertyNames(Point.prototype)
// ["constructor","toString"]
```

上面代码中，`toString()`方法是`Point`类内部定义的方法，它是不可枚举的。这一点与 ES5 的行为不一致。

```javascript
var Point = function (x, y) {
  // ...
};

Point.prototype.toString = function () {
  // ...
};

Object.keys(Point.prototype)
// ["toString"]
Object.getOwnPropertyNames(Point.prototype)
// ["constructor","toString"]
```

上面代码采用 ES5 的写法，`toString()`方法就是可枚举的。

#### constructor 方法 

`constructor()`方法是类的默认方法，通过`new`命令生成对象实例时，自动调用该方法。一个类必须有`constructor()`方法，如果没有显式定义，一个空的`constructor()`方法会被默认添加。

```javascript
class Point {
}

// 等同于
class Point {
  constructor() {}
}
```

`constructor()`方法默认返回实例对象（即`this`），完全可以指定返回另外一个对象。

```javascript
class Foo {
  constructor() {
    return Object.create(null);
  }
}

new Foo() instanceof Foo
// false
```

类必须使用`new`调用，否则会报错。这是它跟普通构造函数的一个主要区别，后者不用`new`也可以执行。

```javascript
class Foo {
  constructor() {
    return Object.create(null);
  }
}

Foo()
// TypeError: Class constructor Foo cannot be invoked without 'new'
```

#### 类的实例

```javascript
class Point {
  // ...
}

// 报错
var point = Point(2, 3);

// 正确
var point = new Point(2, 3);
```

与 ES5 一样，实例的属性除非显式定义在其本身（即定义在`this`对象上），否则都是定义在原型上（即定义在`class`上）。

```javascript
//定义类
class Point {

  constructor(x, y) {
    this.x = x;
    this.y = y;
  }

  toString() {
    return '(' + this.x + ', ' + this.y + ')';
  }

}

var point = new Point(2, 3);

point.toString() // (2, 3)

point.hasOwnProperty('x') // true
point.hasOwnProperty('y') // true
point.hasOwnProperty('toString') // false
point.__proto__.hasOwnProperty('toString') // true
```

类的所有实例共享一个原型对象。

```javascript
var p1 = new Point(2,3);
var p2 = new Point(3,2);

p1.__proto__ === p2.__proto__
//true
```

这也意味着，可以通过实例的`__proto__`属性为“类”添加方法。

`__proto__` 并不是语言本身的特性，这是各大厂商具体实现时添加的私有属性，虽然目前很多现代浏览器的 JS 引擎中都提供了这个私有属性，但依旧不建议在生产中使用该属性，避免对环境产生依赖。生产环境中，我们可以使用 `Object.getPrototypeOf` 方法来获取实例对象的原型，然后再来为原型添加方法/属性。

```javascript
var p1 = new Point(2,3);
var p2 = new Point(3,2);

p1.__proto__.printName = function () { return 'Oops' };

p1.printName() // "Oops"
p2.printName() // "Oops"

var p3 = new Point(4,2);
p3.printName() // "Oops"
```

使用实例的`__proto__`属性改写原型，必须相当谨慎，不推荐使用，因为这会改变“类”的原始定义，影响到所有实例。

#### 取值函数（getter）和存值函数（setter）

与 ES5 一样，在“类”的内部可以使用`get`和`set`关键字，对某个属性设置存值函数和取值函数，拦截该属性的存取行为。

```javascript
class MyClass {
  constructor() {
    // ...
  }
  get prop() {
    return 'getter';
  }
  set prop(value) {
    console.log('setter: '+value);
  }
}

let inst = new MyClass();

inst.prop = 123;
// setter: 123

inst.prop
// 'getter'
```

存值函数和取值函数是设置在属性的 Descriptor 对象上的。

```javascript
class CustomHTMLElement {
  constructor(element) {
    this.element = element;
  }

  get html() {
    return this.element.innerHTML;
  }

  set html(value) {
    this.element.innerHTML = value;
  }
}

var descriptor = Object.getOwnPropertyDescriptor(
  CustomHTMLElement.prototype, "html"
);

"get" in descriptor  // true
"set" in descriptor  // true
```

上面代码中，存值函数和取值函数是定义在`html`属性的描述对象上面，这与 ES5 完全一致。

类的属性名，可以采用表达式。

```javascript
let methodName = 'getArea';

class Square {
  constructor(length) {
    // ...
  }

  [methodName]() {
    // ...
  }
}
```

上面代码中，`Square`类的方法名`getArea`，是从表达式得到的。

#### Class 表达式

与函数一样，类也可以使用表达式的形式定义。

```javascript
const MyClass = class Me {
  getClassName() {
    return Me.name;
  }
};
```

上面代码使用表达式定义了一个类。需要注意的是，这个类的名字是`Me`，但是`Me`只在 Class 的内部可用，指代当前类。在 Class 外部，这个类只能用`MyClass`引用。

```javascript
let inst = new MyClass();
inst.getClassName() // Me
Me.name // ReferenceError: Me is not defined
```

上面代码表示，`Me`只在 Class 内部有定义。

如果类的内部没用到的话，可以省略`Me`，也就是可以写成下面的形式。

```javascript
const MyClass = class { /* ... */ };
```

采用 Class 表达式，可以写出立即执行的 Class。

```javascript
let person = new class {
  constructor(name) {
    this.name = name;
  }

  sayName() {
    console.log(this.name);
  }
}('张三');

person.sayName(); // "张三"
```

上面代码中，`person`是一个立即执行的类的实例。

#### 注意点

**（1）严格模式**

类和模块的内部，默认就是严格模式，所以不需要使用`use strict`指定运行模式。只要你的代码写在类或模块之中，就只有严格模式可用。考虑到未来所有的代码，其实都是运行在模块之中，所以 ES6 实际上把整个语言升级到了严格模式。

**（2）不存在提升**

类不存在变量提升（hoist），这一点与 ES5 完全不同。

```javascript
new Foo(); // ReferenceError
class Foo {}
```

上面代码中，`Foo`类使用在前，定义在后，这样会报错，因为 ES6 不会把类的声明提升到代码头部。这种规定的原因与下文要提到的继承有关，必须保证子类在父类之后定义。

```javascript
{
  let Foo = class {};
  class Bar extends Foo {
  }
}
```

上面的代码不会报错，因为`Bar`继承`Foo`的时候，`Foo`已经有定义了。但是，如果存在`class`的提升，上面代码就会报错，因为`class`会被提升到代码头部，而`let`命令是不提升的，所以导致`Bar`继承`Foo`的时候，`Foo`还没有定义。

**（3）name 属性**

由于本质上，ES6 的类只是 ES5 的构造函数的一层包装，所以函数的许多特性都被`Class`继承，包括`name`属性。

```javascript
class Point {}
Point.name // "Point"
```

`name`属性总是返回紧跟在`class`关键字后面的类名。

**（4）Generator 方法**

如果某个方法之前加上星号（`*`），就表示该方法是一个 Generator 函数。

```javascript
class Foo {
  constructor(...args) {
    this.args = args;
  }
  * [Symbol.iterator]() {
    for (let arg of this.args) {
      yield arg;
    }
  }
}

for (let x of new Foo('hello', 'world')) {
  console.log(x);
}
// hello
// world
```

上面代码中，`Foo`类的`Symbol.iterator`方法前有一个星号，表示该方法是一个 Generator 函数。`Symbol.iterator`方法返回一个`Foo`类的默认遍历器，`for...of`循环会自动调用这个遍历器。

**（5）this 的指向**

类的方法内部如果含有`this`，它默认指向类的实例。但是，必须非常小心，一旦单独使用该方法，很可能报错。

```javascript
class Logger {
  printName(name = 'there') {
    this.print(`Hello ${name}`);
  }

  print(text) {
    console.log(text);
  }
}

const logger = new Logger();
const { printName } = logger;
printName(); // TypeError: Cannot read property 'print' of undefined
```

上面代码中，`printName`方法中的`this`，默认指向`Logger`类的实例。但是，如果将这个方法提取出来单独使用，`this`会指向该方法运行时所在的环境（由于 class 内部是严格模式，所以 this 实际指向的是`undefined`），从而导致找不到`print`方法而报错。

一个比较简单的解决方法是，在构造方法中绑定`this`，这样就不会找不到`print`方法了。

```javascript
class Logger {
  constructor() {
    this.printName = this.printName.bind(this);
  }

  // ...
}
```

另一种解决方法是使用箭头函数。

```javascript
class Obj {
  constructor() {
    this.getThis = () => this;
  }
}

const myObj = new Obj();
myObj.getThis() === myObj // true
```

箭头函数内部的`this`总是指向定义时所在的对象。上面代码中，箭头函数位于构造函数内部，它的定义生效的时候，是在构造函数执行的时候。这时，箭头函数所在的运行环境，肯定是实例对象，所以`this`会总是指向实例对象。

还有一种解决方法是使用`Proxy`，获取方法的时候，自动绑定`this`。

```javascript
function selfish (target) {
  const cache = new WeakMap();
  const handler = {
    get (target, key) {
      const value = Reflect.get(target, key);
      if (typeof value !== 'function') {
        return value;
      }
      if (!cache.has(value)) {
        cache.set(value, value.bind(target));
      }
      return cache.get(value);
    }
  };
  const proxy = new Proxy(target, handler);
  return proxy;
}

const logger = selfish(new Logger());
```

#### 静态方法

类相当于实例的原型，所有在类中定义的方法，都会被实例继承。如果在一个方法前，加上`static`关键字，就表示该方法不会被实例继承，而是直接通过类来调用，这就称为“静态方法”。

```javascript
class Foo {
  static classMethod() {
    return 'hello';
  }
}

Foo.classMethod() // 'hello'

var foo = new Foo();
foo.classMethod()
// TypeError: foo.classMethod is not a function
```

注意，如果静态方法包含`this`关键字，这个`this`指的是类，而不是实例。另外，静态方法可以与非静态方法重名。

```javascript
class Foo {
  static bar() {
    this.baz();
  }
  static baz() {
    console.log('hello');
  }
  baz() {
    console.log('world');
  }
}

Foo.bar() // hello
```

父类的静态方法，可以被子类继承。

```javascript
class Foo {
  static classMethod() {
    return 'hello';
  }
}

class Bar extends Foo {
}

Bar.classMethod() // 'hello'
```

静态方法也是可以从`super`对象上调用的。

```javascript
class Foo {
  static classMethod() {
    return 'hello';
  }
}

class Bar extends Foo {
  static classMethod() {
    return super.classMethod() + ', too';
  }
}

Bar.classMethod() // "hello, too"
```

#### 实例属性的新写法

实例属性除了定义在`constructor()`方法里面的`this`上面，也可以定义在类的最顶层。

```javascript
class IncreasingCounter {
  constructor() {
    this._count = 0;
  }
  get value() {
    console.log('Getting the current value!');
    return this._count;
  }
  increment() {
    this._count++;
  }
}
```

上面代码中，实例属性`this._count`定义在`constructor()`方法里面。另一种写法是，这个属性也可以定义在类的最顶层，其他都不变。

```javascript
class IncreasingCounter {
  _count = 0;
  get value() {
    console.log('Getting the current value!');
    return this._count;
  }
  increment() {
    this._count++;
  }
}
```

种新写法的好处是，所有实例对象自身的属性都定义在类的头部，看上去比较整齐，一眼就能看出这个类有哪些实例属性。

```javascript
class foo {
  bar = 'hello';
  baz = 'world';

  constructor() {
    // ...
  }
}
```

上面的代码，一眼就能看出，`foo`类有两个实例属性，一目了然。另外，写起来也比较简洁。

#### 静态属性

静态属性指的是 Class 本身的属性，即`Class.propName`，而不是定义在实例对象（`this`）上的属性。

```javascript
class Foo {
}

Foo.prop = 1;
Foo.prop // 1
```

上面的写法为`Foo`类定义了一个静态属性`prop`。

目前，只有这种写法可行，因为 ES6 明确规定，Class 内部只有静态方法，没有静态属性。现在有一个[提案](https://github.com/tc39/proposal-class-fields)提供了类的静态属性，写法是在实例属性的前面，加上`static`关键字。

```javascript
class MyClass {
  static myStaticProp = 42;

  constructor() {
    console.log(MyClass.myStaticProp); // 42
  }
}
```

这个新写法大大方便了静态属性的表达。

#### 私有方法和私有属性

私有方法和私有属性，是只能在类的内部访问的方法和属性，外部不能访问。这是常见需求，有利于代码的封装，但 ES6 不提供，只能通过变通方法模拟实现。

一种做法是在命名上加以区别。

```javascript
class Widget {

  // 公有方法
  foo (baz) {
    this._bar(baz);
  }

  // 私有方法
  _bar(baz) {
    return this.snaf = baz;
  }

  // ...
}
```

上面代码中，`_bar()`方法前面的下划线，表示这是一个只限于内部使用的私有方法。但是，这种命名是不保险的，在类的外部，还是可以调用到这个方法。

另一种方法就是索性将私有方法移出类，因为类内部的所有方法都是对外可见的。

```javascript
class Widget {
  foo (baz) {
    bar.call(this, baz);
  }

  // ...
}

function bar(baz) {
  return this.snaf = baz;
```

`foo`是公开方法，内部调用了`bar.call(this, baz)`。这使得`bar()`实际上成为了当前类的私有方法。

还有一种方法是利用`Symbol`值的唯一性，将私有方法的名字命名为一个`Symbol`值。

```javascript
const bar = Symbol('bar');
const snaf = Symbol('snaf');

export default class myClass{

  // 公有方法
  foo(baz) {
    this[bar](baz);
  }

  // 私有方法
  [bar](baz) {
    return this[snaf] = baz;
  }

  // ...
};
```

上面代码中，`bar`和`snaf`都是`Symbol`值，一般情况下无法获取到它们，因此达到了私有方法和私有属性的效果。但是也不是绝对不行，`Reflect.ownKeys()`依然可以拿到它们。

```javascript
const inst = new myClass();

Reflect.ownKeys(myClass.prototype)
// [ 'constructor', 'foo', Symbol(bar) ]
```

上面代码中，Symbol 值的属性名依然可以从类的外部拿到。

#### 私有属性的提案

目前，有一个[提案](https://github.com/tc39/proposal-private-methods)，为`class`加了私有属性。方法是在属性名之前，使用`#`表示。

```javascript
class IncreasingCounter {
  #count = 0;
  get value() {
    console.log('Getting the current value!');
    return this.#count;
  }
  increment() {
    this.#count++;
  }
}
```

上面代码中，`#count`就是私有属性，只能在类的内部使用（`this.#count`）。如果在类的外部使用，就会报错。

```javascript
const counter = new IncreasingCounter();
counter.#count // 报错
counter.#count = 42 // 报错
```

`#x`就是私有属性，在`Point`类之外是读取不到这个属性的。由于井号`#`是属性名的一部分，使用时必须带有`#`一起使用，所以`#x`和`x`是两个不同的属性。

之所以要引入一个新的前缀`#`表示私有属性，而没有采用`private`关键字，是因为 JavaScript 是一门动态语言，没有类型声明，使用独立的符号似乎是唯一的比较方便可靠的方法，能够准确地区分一种属性是否为私有属性。另外，Ruby 语言使用`@`表示私有属性，ES6 没有用这个符号而使用`#`，是因为`@`已经被留给了 Decorator。

这种写法不仅可以写私有属性，还可以用来写私有方法。

```javascript
class Foo {
  #a;
  #b;
  constructor(a, b) {
    this.#a = a;
    this.#b = b;
  }
  #sum() {
    return this.#a + this.#b;
  }
  printSum() {
    console.log(this.#sum());
  }
}
```

上面代码中，`#sum()`就是一个私有方法。

另外，私有属性也可以设置 getter 和 setter 方法。

```javascript
class Counter {
  #xValue = 0;

  constructor() {
    super();
    // ...
  }

  get #x() { return #xValue; }
  set #x(value) {
    this.#xValue = value;
  }
}
```

上面代码中，`#x`是一个私有属性，它的读写都通过`get #x()`和`set #x()`来完成。

私有属性不限于从`this`引用，只要是在类的内部，实例也可以引用私有属性。

```javascript
class Foo {
  #privateValue = 42;
  static getPrivateValue(foo) {
    return foo.#privateValue;
  }
}

Foo.getPrivateValue(new Foo()); // 42
```

上面代码允许从实例`foo`上面引用私有属性。

私有属性和私有方法前面，也可以加上`static`关键字，表示这是一个静态的私有属性或私有方法。

```javascript
class FakeMath {
  static PI = 22 / 7;
  static #totallyRandomNumber = 4;

  static #computeRandomNumber() {
    return FakeMath.#totallyRandomNumber;
  }

  static random() {
    console.log('I heard you like random numbers…')
    return FakeMath.#computeRandomNumber();
  }
}

FakeMath.PI // 3.142857142857143
FakeMath.random()
// I heard you like random numbers…
// 4
FakeMath.#totallyRandomNumber // 报错
FakeMath.#computeRandomNumber() // 报错
```

上面代码中，`#totallyRandomNumber`是私有属性，`#computeRandomNumber()`是私有方法，只能在`FakeMath`这个类的内部调用，外部调用就会报错。

#### in 运算符

`try...catch`结构可以用来判断是否存在某个私有属性。

```javascript
class A {
  use(obj) {
    try {
      obj.#foo;
    } catch {
      // 私有属性 #foo 不存在
    }
  }
}

const a = new A();
a.use(a); // 报错
```

这样的写法很麻烦，可读性很差，V8 引擎改进了`in`运算符，使它也可以用来判断私有属性。

```javascript
class A {
  use(obj) {
    if (#foo in obj) {
      // 私有属性 #foo 存在
    } else {
      // 私有属性 #foo 不存在
    }
  }
}
```

上面示例中，`in`运算符判断当前类`A`的实例，是否有私有属性`#foo`，如果有返回`true`，否则返回`false`。

`in`也可以跟`this`一起配合使用。

```javascript
class A {
  #foo = 0;
  m() {
    console.log(#foo in this); // true
    console.log(#bar in this); // false
  }
}
```

注意，判断私有属性时，`in`只能用在定义该私有属性的类的内部。

```javascript
class A {
  #foo = 0;
  static test(obj) {
    console.log(#foo in obj);
  }
}

A.test(new A()) // true
A.test({}) // false

class B {
  #foo = 0;
}

A.test(new B()) // false
```

上面示例中，类`A`的私有属性`#foo`，只能在类`A`内部使用`in`运算符判断，而且只对`A`的实例返回`true`，对于其他对象都返回`false`。

子类从父类继承的私有属性，也可以使用`in`运算符来判断。

```javascript
class A {
  #foo = 0;
  static test(obj) {
    console.log(#foo in obj);
  }
}

class SubA extends A {};

A.test(new SubA()) // true
```

注意，`in`运算符对于`Object.create()`、`Object.setPrototypeOf`形成的继承，是无效的，因为这种继承不会传递私有属性。

```javascript
class A {
  #foo = 0;
  static test(obj) {
    console.log(#foo in obj);
  }
}
const a = new A();

const o1 = Object.create(a);
A.test(o1) // false
A.test(o1.__proto__) // true

const o2 = {};
Object.setPrototypeOf(o2, a);
A.test(o2) // false
A.test(o2.__proto__) // true
```

上面示例中，对于修改原型链形成的继承，子类都取不到父类的私有属性，所以`in`运算符无效。

### 17.Class 的继承

Class 可以通过`extends`关键字实现继承，让子类继承父类的属性和方法。extends 的写法比 ES5 的原型链继承，要清晰和方便很多。

```javascript
class Point {
}

class ColorPoint extends Point {
}
```

上面示例中，`Point`是父类，`ColorPoint`是子类，它通过`extends`关键字，继承了`Point`类的所有属性和方法。但是由于没有部署任何代码，所以这两个类完全一样，等于复制了一个`Point`类。

```javascript
class Point { /* ... */ }

class ColorPoint extends Point {
  constructor(x, y, color) {
    super(x, y); // 调用父类的constructor(x, y)
    this.color = color;
  }

  toString() {
    return this.color + ' ' + super.toString(); // 调用父类的toString()
  }
}
```

上面示例中，`constructor()`方法和`toString()`方法内部，都出现了`super`关键字。`super`在这里表示父类的构造函数，用来新建一个父类的实例对象。

ES6 规定，子类必须在`constructor()`方法中调用`super()`，否则就会报错。这是因为子类自己的`this`对象，必须先通过父类的构造函数完成塑造，得到与父类同样的实例属性和方法，然后再对其进行加工，添加子类自己的实例属性和方法。如果不调用`super()`方法，子类就得不到自己的`this`对象。

```javascript
class Point { /* ... */ }

class ColorPoint extends Point {
  constructor() {
  }
}

let cp = new ColorPoint(); // ReferenceError
```

为什么子类的构造函数，一定要调用`super()`？原因就在于 ES6 的继承机制，与 ES5 完全不同。ES5 的继承机制，是先创造一个独立的子类的实例对象，然后再将父类的方法添加到这个对象上面，即“实例在前，继承在后”。ES6 的继承机制，则是先将父类的属性和方法，加到一个空的对象上面，然后再将该对象作为子类的实例，即“继承在前，实例在后”。这就是为什么 ES6 的继承必须先调用`super()`方法，因为这一步会生成一个继承父类的`this`对象，没有这一步就无法继承父类。

注意，这意味着新建子类实例时，父类的构造函数必定会先运行一次。

```javascript
class Foo {
  constructor() {
    console.log(1);
  }
}

class Bar extends Foo {
  constructor() {
    super();
    console.log(2);
  }
}

const bar = new Bar();
// 1
// 2
```

另一个需要注意的地方是，在子类的构造函数中，只有调用`super()`之后，才可以使用`this`关键字，否则会报错。这是因为子类实例的构建，必须先完成父类的继承，只有`super()`方法才能让子类实例继承父类。

```javascript
class Point {
  constructor(x, y) {
    this.x = x;
    this.y = y;
  }
}

class ColorPoint extends Point {
  constructor(x, y, color) {
    this.color = color; // ReferenceError
    super(x, y);
    this.color = color; // 正确
  }
}
```

如果子类没有定义`constructor()`方法，这个方法会默认添加，并且里面会调用`super()`。也就是说，不管有没有显式定义，任何一个子类都有`constructor()`方法。

```javascript
class ColorPoint extends Point {
}

// 等同于
class ColorPoint extends Point {
  constructor(...args) {
    super(...args);
  }
}
```

除了私有属性，父类的所有属性和方法，都会被子类继承，其中包括静态方法。

```javascript
class A {
  static hello() {
    console.log('hello world');
  }
}

class B extends A {
}

B.hello()  // hello world
```

子类无法继承父类的私有属性，或者说，私有属性只能在定义它的 class 里面使用。

```javascript
class Foo {
  #p = 1;
  #m() {
    console.log('hello');
  }
}

class Bar extends Foo {
  constructor() {
    super();
    console.log(this.#p); // 报错
    this.#m(); // 报错
  }
}
```

如果父类定义了私有属性的读写方法，子类就可以通过这些方法，读写私有属性。

```javascript
class Foo {
  #p = 1;
  getP() {
    return this.#p;
  }
}

class Bar extends Foo {
  constructor() {
    super();
    console.log(this.getP()); // 1
  }
}
```

#### Object.getPrototypeOf()

`Object.getPrototypeOf()`方法可以用来从子类上获取父类。

```javascript
class Point { /*...*/ }

class ColorPoint extends Point { /*...*/ }

Object.getPrototypeOf(ColorPoint) === Point
// true
```

因此，可以使用这个方法判断，一个类是否继承了另一个类。

#### super 关键字

`super`这个关键字，既可以当作函数使用，也可以当作对象使用。在这两种情况下，它的用法完全不同。

第一种情况，`super`作为函数调用时，代表父类的构造函数。ES6 要求，子类的构造函数必须执行一次`super`函数。

```javascript
class A {}

class B extends A {
  constructor() {
    super();
  }
}
```

`super()`在这里相当于`A.prototype.constructor.call(this)`。

```javascript
class A {
  constructor() {
    console.log(new.target.name);
  }
}
class B extends A {
  constructor() {
    super();
  }
}
new A() // A
new B() // B
```

作为函数时，`super()`只能用在子类的构造函数之中，用在其他地方就会报错。

```javascript
class A {}

class B extends A {
  m() {
    super(); // 报错
  }
}
```

第二种情况，`super`作为对象时，在普通方法中，指向父类的原型对象；在静态方法中，指向父类。

```javascript
class A {
  p() {
    return 2;
  }
}

class B extends A {
  constructor() {
    super();
    console.log(super.p()); // 2
  }
}

let b = new B();
```

上面代码中，子类`B`当中的`super.p()`，就是将`super`当作一个对象使用。这时，`super`在普通方法之中，指向`A.prototype`，所以`super.p()`就相当于`A.prototype.p()`。

这里需要注意，由于`super`指向父类的原型对象，所以定义在父类实例上的方法或属性，是无法通过`super`调用的。

```javascript
class A {
  constructor() {
    this.p = 2;
  }
}

class B extends A {
  get m() {
    return super.p;
  }
}

let b = new B();
b.m // undefined
```

如果属性定义在父类的原型对象上，`super`就可以取到。

```javascript
class A {}
A.prototype.x = 2;

class B extends A {
  constructor() {
    super();
    console.log(super.x) // 2
  }
}

let b = new B();
```

ES6 规定，在子类普通方法中通过`super`调用父类的方法时，**方法内部的`this`**指向当前的子类实例。

```javascript
class A {
  constructor() {
    this.x = 1;
  }
  print() {
    console.log(this.x);
  }
}

class B extends A {
  constructor() {
    super();
    this.x = 2;
  }
  m() {
    super.print();
  }
}

let b = new B();
b.m() // 2
```

上面代码中，`super.print()`虽然调用的是`A.prototype.print()`，但是`A.prototype.print()`内部的`this`指向子类`B`的实例，导致输出的是`2`，而不是`1`。也就是说，实际上执行的是`super.print.call(this)`。

由于`this`指向子类实例，所以如果通过`super`对某个属性赋值，这时`super`就是`this`，赋值的属性会变成子类实例的属性。

```javascript
class A {
  constructor() {
    this.x = 1;
  }
}

class B extends A {
  constructor() {
    super();
    this.x = 2;
    super.x = 3;
    console.log(super.x); // undefined
    console.log(this.x); // 3
  }
}

let b = new B();
```

如果`super`作为对象，用在静态方法之中，这时`super`将指向父类，而不是父类的原型对象。

```javascript
class Parent {
  static myMethod(msg) {
    console.log('static', msg);
  }

  myMethod(msg) {
    console.log('instance', msg);
  }
}

class Child extends Parent {
  static myMethod(msg) {
    super.myMethod(msg);
  }

  myMethod(msg) {
    super.myMethod(msg);
  }
}

Child.myMethod(1); // static 1

var child = new Child();
child.myMethod(2); // instance 2
```

另外，在子类的静态方法中通过`super`调用父类的方法时，**方法内部的`this`**指向当前的子类，而不是子类的实例。

```javascript
class A {
  constructor() {
    this.x = 1;
  }
  static print() {
    console.log(this.x);
  }
}

class B extends A {
  constructor() {
    super();
    this.x = 2;
  }
  static m() {
    super.print();
  }
}

B.x = 3;
B.m() // 3
```

注意，使用`super`的时候，必须显式指定是作为函数、还是作为对象使用，否则会报错。

```javascript
class A {}

class B extends A {
  constructor() {
    super();
    console.log(super); // 报错
  }
}
```

上面代码中，`console.log(super)`当中的`super`，无法看出是作为函数使用，还是作为对象使用，所以 JavaScript 引擎解析代码的时候就会报错。这时，如果能清晰地表明`super`的数据类型，就不会报错。

```javascript
class A {}

class B extends A {
  constructor() {
    super();
    console.log(super.valueOf() instanceof B); // true
  }
}

let b = new B();
```

上面代码中，`super.valueOf()`表明`super`是一个对象，因此就不会报错。同时，由于`super`使得`this`指向`B`的实例，所以`super.valueOf()`返回的是一个`B`的实例。

最后，由于对象总是继承其他对象的，所以可以在任意一个对象中，使用`super`关键字。

```javascript
var obj = {
  toString() {
    return "MyObject: " + super.toString();
  }
};

obj.toString(); // MyObject: [object Object]
```

#### 类的 prototype 属性和__proto__属性

大多数浏览器的 ES5 实现之中，每一个对象都有`__proto__`属性，指向对应的构造函数的`prototype`属性。Class 作为构造函数的语法糖，同时有`prototype`属性和`__proto__`属性，因此同时存在两条继承链。

（1）子类的`__proto__`属性，表示构造函数的继承，总是指向父类。

（2）子类`prototype`属性的`__proto__`属性，表示方法的继承，总是指向父类的`prototype`属性。

```javascript
class A {
}

class B extends A {
}

B.__proto__ === A // true
B.prototype.__proto__ === A.prototype // true
```

这样的结果是因为，类的继承是按照下面的模式实现的。

```javascript
class A {
}

class B {
}

// B 的实例继承 A 的实例
Object.setPrototypeOf(B.prototype, A.prototype);

// B 继承 A 的静态属性
Object.setPrototypeOf(B, A);

const b = new B();
```

`Object.setPrototypeOf`方法的实现。

```javascript
Object.setPrototypeOf = function (obj, proto) {
  obj.__proto__ = proto;
  return obj;
}
```

因此，就得到了上面的结果。

```javascript
Object.setPrototypeOf(B.prototype, A.prototype);
// 等同于
B.prototype.__proto__ = A.prototype;

Object.setPrototypeOf(B, A);
// 等同于
B.__proto__ = A;
```

这两条继承链，可以这样理解：作为一个对象，子类（`B`）的原型（`__proto__`属性）是父类（`A`）；作为一个构造函数，子类（`B`）的原型对象（`prototype`属性）是父类的原型对象（`prototype`属性）的实例。

```javascript
B.prototype = Object.create(A.prototype);
// 等同于
B.prototype.__proto__ = A.prototype;
```

#### 实例的 __proto__ 属性

子类实例的`__proto__`属性的`__proto__`属性，指向父类实例的`__proto__`属性。也就是说，子类的原型的原型，是父类的原型。

```javascript
var p1 = new Point(2, 3);
var p2 = new ColorPoint(2, 3, 'red');

p2.__proto__ === p1.__proto__ // false
p2.__proto__.__proto__ === p1.__proto__ // true
```

因此，通过子类实例的`__proto__.__proto__`属性，可以修改父类实例的行为。

```javascript
p2.__proto__.__proto__.printName = function () {
  console.log('Ha');
};

p1.printName() // "Ha"
```

#### 原生构造函数的继承

原生构造函数是指语言内置的构造函数，通常用来生成数据结构。ECMAScript 的原生构造函数大致有下面这些。

- Boolean()
- Number()
- String()
- Array()
- Date()
- Function()
- RegExp()
- Error()
- Object()

以前，这些原生构造函数是无法继承的，比如，不能自己定义一个`Array`的子类。

```javascript
function MyArray() {
  Array.apply(this, arguments);
}

MyArray.prototype = Object.create(Array.prototype, {
  constructor: {
    value: MyArray,
    writable: true,
    configurable: true,
    enumerable: true
  }
});
```

上面代码定义了一个继承 Array 的`MyArray`类。但是，这个类的行为与`Array`完全不一致。

```javascript
var colors = new MyArray();
colors[0] = "red";
colors.length  // 0

colors.length = 0;
colors[0]  // "red"
```

之所以会发生这种情况，是因为子类无法获得原生构造函数的内部属性，通过`Array.apply()`或者分配给原型对象都不行。原生构造函数会忽略`apply`方法传入的`this`，也就是说，原生构造函数的`this`无法绑定，导致拿不到内部属性。

ES6 允许继承原生构造函数定义子类，因为 ES6 是先新建父类的实例对象`this`，然后再用子类的构造函数修饰`this`，使得父类的所有行为都可以继承。下面是一个继承`Array`的例子。

```javascript
class MyArray extends Array {
  constructor(...args) {
    super(...args);
  }
}

var arr = new MyArray();
arr[0] = 12;
arr.length // 1

arr.length = 0;
arr[0] // undefined
```

上面代码定义了一个`MyArray`类，继承了`Array`构造函数，因此就可以从`MyArray`生成数组的实例。这意味着，ES6 可以自定义原生数据结构（比如`Array`、`String`等）的子类，这是 ES5 无法做到的。

#### Mixin 模式的实现

Mixin 指的是多个对象合成一个新的对象，新对象具有各个组成成员的接口。它的最简单实现如下。

```javascript
const a = {
  a: 'a'
};
const b = {
  b: 'b'
};
const c = {...a, ...b}; // {a: 'a', b: 'b'}
```

上面代码中，`c`对象是`a`对象和`b`对象的合成，具有两者的接口。

下面是一个更完备的实现，将多个类的接口“混入”（mix in）另一个类。

```javascript
function mix(...mixins) {
  class Mix {
    constructor() {
      for (let mixin of mixins) {
        copyProperties(this, new mixin()); // 拷贝实例属性
      }
    }
  }

  for (let mixin of mixins) {
    copyProperties(Mix, mixin); // 拷贝静态属性
    copyProperties(Mix.prototype, mixin.prototype); // 拷贝原型属性
  }

  return Mix;
}

function copyProperties(target, source) {
  for (let key of Reflect.ownKeys(source)) {
    if ( key !== 'constructor'
      && key !== 'prototype'
      && key !== 'name'
    ) {
      let desc = Object.getOwnPropertyDescriptor(source, key);
      Object.defineProperty(target, key, desc);
    }
  }
}
```

上面代码的`mix`函数，可以将多个对象合成为一个类。使用的时候，只要继承这个类即可。

```javascript
class DistributedEdit extends mix(Loggable, Serializable) {
  // ...
}
```

### 18.数值扩展

#### 二进制和八进制表示法

ES6 提供了二进制和八进制数值的新的写法，分别用前缀`0b`（或`0B`）和`0o`（或`0O`）表示。

```javascript
0b111110111 === 503 // true
0o767 === 503 // true
```

从 ES5 开始，在严格模式之中，八进制就不再允许使用前缀`0`表示，ES6 进一步明确，要使用前缀`0o`表示。

```javascript
// 非严格模式
(function(){
  console.log(0o11 === 011);
})() // true

// 严格模式
(function(){
  'use strict';
  console.log(0o11 === 011);
})() // Uncaught SyntaxError: Octal literals are not allowed in strict mode.
```

如果要将`0b`和`0o`前缀的字符串数值转为十进制，要使用`Number`方法。

```javascript
Number('0b111')  // 7
Number('0o10')  // 8
```

#### 数值分隔符

欧美语言中，较长的数值允许每三位添加一个分隔符（通常是一个逗号），增加数值的可读性。比如，`1000`可以写作`1,000`。

[ES2021](https://github.com/tc39/proposal-numeric-separator)，允许 JavaScript 的数值使用下划线（`_`）作为分隔符。

```javascript
let budget = 1_000_000_000_000;
budget === 10 ** 12 // true
```

这个数值分隔符没有指定间隔的位数，也就是说，可以每三位添加一个分隔符，也可以每一位、每两位、每四位添加一个。

```javascript
123_00 === 12_300 // true

12345_00 === 123_4500 // true
12345_00 === 1_234_500 // true
```

小数和科学计数法也可以使用数值分隔符。

```javascript
// 小数
0.000_001

// 科学计数法
1e10_000
```

数值分隔符有几个使用注意点。

- 不能放在数值的最前面（leading）或最后面（trailing）。
- 不能两个或两个以上的分隔符连在一起。
- 小数点的前后不能有分隔符。
- 科学计数法里面，表示指数的`e`或`E`前后不能有分隔符。

```javascript
// 全部报错
3_.141
3._141
1_e12
1e_12
123__456
_1464301
1464301_
```

除了十进制，其他进制的数值也可以使用分隔符。

```javascript
// 二进制
0b1010_0001_1000_0101
// 十六进制
0xA0_B0_C0
```

**注意**，分隔符不能紧跟着进制的前缀`0b`、`0B`、`0o`、`0O`、`0x`、`0X`。

```javascript
// 报错
0_b111111000
0b_111111000
```

数值分隔符只是一种书写便利，对于 JavaScript 内部数值的存储和输出，并没有影响。

```javascript
let num = 12_345;

num // 12345
num.toString() // 12345
```

下面三个将字符串转成数值的函数，不支持数值分隔符。主要原因是语言的设计者认为，数值分隔符主要是为了编码时书写数值的方便，而不是为了处理外部输入的数据。

- Number()
- parseInt()
- parseFloat()

```javascript
Number('123_456') // NaN
parseInt('123_456') // 123
```

#### Number.isFinite(), Number.isNaN()

ES6 在`Number`对象上，新提供了`Number.isFinite()`和`Number.isNaN()`两个方法。

`Number.isFinite()`用来检查一个数值是否为有限的（finite），即不是`Infinity`。

```javascript
Number.isFinite(15); // true
Number.isFinite(0.8); // true
Number.isFinite(NaN); // false
Number.isFinite(Infinity); // false
Number.isFinite(-Infinity); // false
Number.isFinite('foo'); // false
Number.isFinite('15'); // false
Number.isFinite(true); // false
```

**注意**，如果参数类型不是数值，`Number.isFinite`一律返回`false`。

`Number.isNaN()`用来检查一个值是否为`NaN`。

```javascript
Number.isNaN(NaN) // true
Number.isNaN(15) // false
Number.isNaN('15') // false
Number.isNaN(true) // false
Number.isNaN(9/NaN) // true
Number.isNaN('true' / 0) // true
Number.isNaN('true' / 'true') // true
```

如果参数类型不是`NaN`，`Number.isNaN`一律返回`false`。

**与传统的全局方法`isFinite()`和`isNaN()`的区别**：

- 传统方法先调用`Number()`将非数值的值转为数值，再进行判断，而这两个新方法只对数值有效
- `Number.isFinite()`对于非数值一律返回`false`, `Number.isNaN()`只有对于`NaN`才返回`true`，非`NaN`一律返回`false`。

```javascript
isFinite(25) // true
isFinite("25") // true
Number.isFinite(25) // true
Number.isFinite("25") // false

isNaN(NaN) // true
isNaN("NaN") // true
Number.isNaN(NaN) // true
Number.isNaN("NaN") // false
Number.isNaN(1) // false
```

#### Number.parseInt(), Number.parseFloat() 

ES6 将全局方法`parseInt()`和`parseFloat()`，移植到`Number`对象上面，行为完全保持不变。

```javascript
// ES5的写法
parseInt('12.34') // 12
parseFloat('123.45#') // 123.45

// ES6的写法
Number.parseInt('12.34') // 12
Number.parseFloat('123.45#') // 123.45
```

这样做的目的，是逐步减少全局性方法，使得语言逐步模块化。

```javascript
Number.parseInt === parseInt // true
Number.parseFloat === parseFloat // true
```

#### Number.isInteger()

`Number.isInteger()`用来判断一个数值是否为整数。

```javascript
Number.isInteger(25) // true
Number.isInteger(25.1) // false
```

JavaScript 内部，整数和浮点数采用的是同样的储存方法，所以 25 和 25.0 被视为同一个值。

```javascript
Number.isInteger(25) // true
Number.isInteger(25.0) // true
```

如果参数不是数值，`Number.isInteger`返回`false`。

```javascript
Number.isInteger() // false
Number.isInteger(null) // false
Number.isInteger('15') // false
Number.isInteger(true) // false
```

**注意**，由于 JavaScript 采用 IEEE 754 标准，数值存储为64位双精度格式，数值精度最多可以达到 53 个二进制位（1 个隐藏位与 52 个有效位）。如果数值的精度超过这个限度，第54位及后面的位就会被丢弃，这种情况下，`Number.isInteger`可能会误判。

```javascript
Number.isInteger(3.0000000000000002) // true
```

`Number.isInteger`的参数明明不是整数，但是会返回`true`。原因就是这个小数的精度达到了小数点后16个十进制位，转成二进制位超过了53个二进制位，导致最后的那个`2`被丢弃了。

类似的情况还有，如果一个数值的绝对值小于`Number.MIN_VALUE`（5E-324），即小于 JavaScript 能够分辨的最小值，会被自动转为 0。这时，`Number.isInteger`也会误判。

```javascript
Number.isInteger(5E-324) // false
Number.isInteger(5E-325) // true
```

总之，如果对数据精度的要求较高，不建议使用`Number.isInteger()`判断一个数值是否为整数。

#### Number.EPSILON

ES6 在`Number`对象上面，新增一个极小的常量`Number.EPSILON`。根据规格，它表示 1 与大于 1 的最小浮点数之间的差。

对于 64 位浮点数来说，大于 1 的最小浮点数相当于二进制的`1.00..001`，小数点后面有连续 51 个零。这个值减去 1 之后，就等于 2 的 -52 次方。

```javascript
Number.EPSILON === Math.pow(2, -52)
// true
Number.EPSILON
// 2.220446049250313e-16
Number.EPSILON.toFixed(20)
// "0.00000000000000022204"
```

`Number.EPSILON`实际上是 JavaScript 能够表示的最小精度。误差如果小于这个值，就可以认为已经没有意义了，即不存在误差了。

引入一个这么小的量的目的，在于为浮点数计算，设置一个误差范围。我们知道浮点数计算是不精确的。

```javascript
0.1 + 0.2
// 0.30000000000000004

0.1 + 0.2 - 0.3
// 5.551115123125783e-17

5.551115123125783e-17.toFixed(20)
// '0.00000000000000005551'
```

上面代码解释了，为什么比较`0.1 + 0.2`与`0.3`得到的结果是`false`。

```javascript
0.1 + 0.2 === 0.3 // false
```

`Number.EPSILON`可以用来设置“能够接受的误差范围”。比如，误差范围设为 2 的-50 次方（即`Number.EPSILON * Math.pow(2, 2)`），即如果两个浮点数的差小于这个值，我们就认为这两个浮点数相等。

```javascript
5.551115123125783e-17 < Number.EPSILON * Math.pow(2, 2)
// true
```

因此，`Number.EPSILON`的实质是一个可以接受的最小误差范围。

```javascript
function withinErrorMargin (left, right) {
  return Math.abs(left - right) < Number.EPSILON * Math.pow(2, 2);
}

0.1 + 0.2 === 0.3 // false
withinErrorMargin(0.1 + 0.2, 0.3) // true

1.1 + 1.3 === 2.4 // false
withinErrorMargin(1.1 + 1.3, 2.4) // true
```

上面的代码为浮点数运算，部署了一个误差检查函数。

#### Math.trunc()

`Math.trunc`方法用于去除一个数的小数部分，返回整数部分。

```javascript
Math.trunc(4.1) // 4
Math.trunc(4.9) // 4
Math.trunc(-4.1) // -4
Math.trunc(-4.9) // -4
Math.trunc(-0.1234) // -0
```

对于非数值，`Math.trunc`内部使用`Number`方法将其先转为数值。

```javascript
Math.trunc('123.456') // 123
Math.trunc(true) //1
Math.trunc(false) // 0
Math.trunc(null) // 0
```

对于空值和无法截取整数的值，返回`NaN`。

```javascript
Math.trunc(NaN);      // NaN
Math.trunc('foo');    // NaN
Math.trunc();         // NaN
Math.trunc(undefined) // NaN
```

对于没有部署这个方法的环境，可以用下面的代码模拟。

```javascript
Math.trunc = Math.trunc || function(x) {
  return x < 0 ? Math.ceil(x) : Math.floor(x);
};
```

#### Math.sign()

`Math.sign`方法用来判断一个数到底是正数、负数、还是零。对于非数值，会先将其转换为数值。

它会返回五种值。

- 参数为正数，返回`+1`；
- 参数为负数，返回`-1`；
- 参数为 0，返回`0`；
- 参数为-0，返回`-0`;
- 其他值，返回`NaN`。

```javascript
Math.sign(-5) // -1
Math.sign(5) // +1
Math.sign(0) // +0
Math.sign(-0) // -0
Math.sign(NaN) // NaN
```

如果参数是非数值，会自动转为数值。对于那些无法转为数值的值，会返回`NaN`。

```javascript
Math.sign('')  // 0
Math.sign(true)  // +1
Math.sign(false)  // 0
Math.sign(null)  // 0
Math.sign('9')  // +1
Math.sign('foo')  // NaN
Math.sign()  // NaN
Math.sign(undefined)  // NaN
```

对于没有部署这个方法的环境，可以用下面的代码模拟。

```javascript
Math.sign = Math.sign || function(x) {
  x = +x; // convert to a number
  if (x === 0 || isNaN(x)) {
    return x;
  }
  return x > 0 ? 1 : -1;
};
```

### 19.对象扩展

#### 属性的简洁表示法

ES6 允许在大括号里面，直接写入变量和函数，作为对象的属性和方法。这样的书写更加简洁。

```javascript
const foo = 'bar';
const baz = {foo};
baz // {foo: "bar"}

// 等同于
const baz = {foo: foo};
```

```javascript
function f(x, y) {
  return {x, y};
}

// 等同于

function f(x, y) {
  return {x: x, y: y};
}

f(1, 2) // Object {x: 1, y: 2}
```

除了属性简写，方法也可以简写。

```javascript
const o = {
  method() {
    return "Hello!";
  }
};

// 等同于

const o = {
  method: function() {
    return "Hello!";
  }
};
```

这种写法用于函数的返回值，将会非常方便。

```javascript
function getPoint() {
  const x = 1;
  const y = 10;
  return {x, y};
}

getPoint()
// {x:1, y:10}
```

CommonJS 模块输出一组变量，就非常合适使用简洁写法。

```javascript
let ms = {};

function getItem (key) {
  return key in ms ? ms[key] : null;
}

function setItem (key, value) {
  ms[key] = value;
}

function clear () {
  ms = {};
}

module.exports = { getItem, setItem, clear };
// 等同于
module.exports = {
  getItem: getItem,
  setItem: setItem,
  clear: clear
};
```

属性的赋值器（setter）和取值器（getter），事实上也是采用这种写法。

```javascript
const cart = {
  _wheels: 4,

  get wheels () {
    return this._wheels;
  },

  set wheels (value) {
    if (value < this._wheels) {
      throw new Error('数值太小了！');
    }
    this._wheels = value;
  }
}
```

简洁写法在打印对象时也很有用。

```javascript
let user = {
  name: 'test'
};

let foo = {
  bar: 'baz'
};

console.log(user, foo)
// {name: "test"} {bar: "baz"}
console.log({user, foo})
// {user: {name: "test"}, foo: {bar: "baz"}}
```

**注意**，简写的对象方法不能用作构造函数，会报错。

```javascript
const obj = {
  f() {
    this.foo = 'bar';
  }
};

new obj.f() // 报错
```

上面代码中，`f`是一个简写的对象方法，所以`obj.f`不能当作构造函数使用。

#### 属性名表达式

avaScript 定义对象的属性，有两种方法。

```javascript
// 方法一
obj.foo = true;

// 方法二
obj['a' + 'bc'] = 123;
```

- 方法一是直接用标识符作为属性名，
- 方法二是用表达式作为属性名，这时要将表达式放在方括号之内

ES6 允许字面量定义对象时，用方法二（表达式）作为对象的属性名，即把表达式放在方括号内。

```javascript
let propKey = 'foo';

let obj = {
  [propKey]: true,
  ['a' + 'bc']: 123
};
```

**注意**，属性名表达式如果是一个对象，默认情况下会自动将对象转为字符串`[object Object]`，这一点要特别小心。

```javascript
const keyA = {a: 1};
const keyB = {b: 2};

const myObject = {
  [keyA]: 'valueA',
  [keyB]: 'valueB'
};

myObject // Object {[object Object]: "valueB"}
```

上面代码中，`[keyA]`和`[keyB]`得到的都是`[object Object]`，所以`[keyB]`会把`[keyA]`覆盖掉，而`myObject`最后只有一个`[object Object]`属性。

#### 方法的 name 属性

函数的`name`属性，返回函数名。对象方法也是函数，因此也有`name`属性。

```javascript
const person = {
  sayName() {
    console.log('hello!');
  },
};

person.sayName.name   // "sayName"
```

上面代码中，方法的`name`属性返回函数名（即方法名）。

如果对象的方法使用了取值函数（`getter`）和存值函数（`setter`），则`name`属性不是在该方法上面，而是该方法的属性的描述对象的`get`和`set`属性上面，返回值是方法名前加上`get`和`set`。

```javascript
const obj = {
  get foo() {},
  set foo(x) {}
};

obj.foo.name
// TypeError: Cannot read property 'name' of undefined

const descriptor = Object.getOwnPropertyDescriptor(obj, 'foo');

descriptor.get.name // "get foo"
descriptor.set.name // "set foo"
```

有两种特殊情况：`bind`方法创造的函数，`name`属性返回`bound`加上原函数的名字；`Function`构造函数创造的函数，`name`属性返回`anonymous`。

```javascript
(new Function()).name // "anonymous"

var doSomething = function() {
  // ...
};
doSomething.bind().name // "bound doSomething"
```

如果对象的方法是一个 Symbol 值，那么`name`属性返回的是这个 Symbol 值的描述。

```javascript
const key1 = Symbol('description');
const key2 = Symbol();
let obj = {
  [key1]() {},
  [key2]() {},
};
obj[key1].name // "[description]"
obj[key2].name // ""
```

上面代码中，`key1`对应的 Symbol 值有描述，`key2`没有。

#### 属性的遍历

ES6 一共有 5 种方法可以遍历对象的属性。

**（1）for...in**

`for...in`循环遍历对象自身的和继承的可枚举属性（不含 Symbol 属性）。

**（2）Object.keys(obj)**

`Object.keys`返回一个数组，包括对象自身的（不含继承的）所有可枚举属性（不含 Symbol 属性）的键名。

**（3）Object.getOwnPropertyNames(obj)**

`Object.getOwnPropertyNames`返回一个数组，包含对象自身的所有属性（不含 Symbol 属性，但是包括不可枚举属性）的键名。

**（4）Object.getOwnPropertySymbols(obj)**

`Object.getOwnPropertySymbols`返回一个数组，包含对象自身的所有 Symbol 属性的键名。

**（5）Reflect.ownKeys(obj)**

`Reflect.ownKeys`返回一个数组，包含对象自身的（不含继承的）所有键名，不管键名是 Symbol 或字符串，也不管是否可枚举。

以上的 5 种方法遍历对象的键名，都遵守同样的属性遍历的次序规则。

- 首先遍历所有数值键，按照数值升序排列。
- 其次遍历所有字符串键，按照加入时间升序排列。
- 最后遍历所有 Symbol 键，按照加入时间升序排列。

```javascript
Reflect.ownKeys({ [Symbol()]:0, b:0, 10:0, 2:0, a:0 })
// ['2', '10', 'b', 'a', Symbol()]
```

上面代码中，`Reflect.ownKeys`方法返回一个数组，包含了参数对象的所有属性。这个数组的属性次序是这样的，首先是数值属性`2`和`10`，其次是字符串属性`b`和`a`，最后是 Symbol 属性。

#### Object.is

比较两个值是否严格相等，与『===』行为基本一致（区别于+0 与 NaN）

```
console.log(Object.is(120, 120));// true
console.log(Object.is(NaN, NaN));// true
console.log(NaN === NaN);// false
```

#### Object.assign

Object.assign 对象的合并，将源对象的所有可枚举属性，复制到目标对象

```
const config1 = {
    host: 'localhost',
    port: 3306,
    name: 'root',
    pass: 'root',
    test: 'test'
};
const config2 = {
    host: 'http://baidu.com',
    port: 33060,
    name: 'baidu.com',
    pass: 'iloveyou',
    test2: 'test2'
}
console.log(Object.assign(config1, config2));
//{host: 'http://baidu.com', port: 33060, name: 'baidu.com', pass: 'iloveyou', test: 'test', test2: "test2"}
```

#### Object.setPrototypeOf

__ proto __、setPrototypeOf, setPrototypeOf 可以直接设置对象的原型

```
const person = {
    name: 'wxy'
}
const cities = {
    xiaoqu: ['北京','上海','深圳']
}
Object.setPrototypeOf(person, cities);
console.log(Object.getPrototypeOf(person)); //{xiaoqu: Array(3)}
console.log(person); //{name: 'wxy'}
```

#### 对象的扩展运算符

##### 解构赋值

对象的解构赋值用于从一个对象取值，相当于将目标对象自身的所有可遍历的（enumerable）、但尚未被读取的属性，分配到指定的对象上面。所有的键和它们的值，都会拷贝到新对象上面。

```javascript
let { x, y, ...z } = { x: 1, y: 2, a: 3, b: 4 };
x // 1
y // 2
z // { a: 3, b: 4 }
```

由于解构赋值要求等号右边是一个对象，所以如果等号右边是`undefined`或`null`，就会报错，因为它们无法转为对象。

```javascript
let { ...z } = null; // 运行时错误
let { ...z } = undefined; // 运行时错误
```

解构赋值必须是最后一个参数，否则会报错。

```javascript
let { ...x, y, z } = someObject; // 句法错误
let { x, ...y, ...z } = someObject; // 句法错误
```

注意，解构赋值的拷贝是浅拷贝，即如果一个键的值是复合类型的值（数组、对象、函数）、那么解构赋值拷贝的是这个值的引用，而不是这个值的副本。

```javascript
let obj = { a: { b: 1 } };
let { ...x } = obj;
obj.a.b = 2;
x.a.b // 2
```

另外，**扩展运算符的解构赋值**，不能复制继承自原型对象的属性。

```javascript
let o1 = { a: 1 };
let o2 = { b: 2 };
o2.__proto__ = o1;
let { ...o3 } = o2;
o3 // { b: 2 }
o3.a // undefined
```



```javascript
const o = Object.create({ x: 1, y: 2 });
o.z = 3;

let { x, ...newObj } = o;
let { y, z } = newObj;
x // 1
y // undefined
z // 3
```

上面代码中，变量`x`是单纯的解构赋值，所以可以读取对象`o`继承的属性；变量`y`和`z`是扩展运算符的解构赋值，只能读取对象`o`自身的属性，所以变量`z`可以赋值成功，变量`y`取不到值。

ES6 规定，变量声明语句之中，如果使用解构赋值，扩展运算符后面必须是一个变量名，而不能是一个解构赋值表达式，所以上面代码引入了中间变量`newObj`，如果写成下面这样会报错。

```javascript
let { x, ...{ y, z } } = o;
// SyntaxError: ... must be followed by an identifier in declaration contexts
```

解构赋值的一个用处，是扩展某个函数的参数，引入其他操作。

```javascript
function baseFunction({ a, b }) {
  // ...
}
function wrapperFunction({ x, y, ...restConfig }) {
  // 使用 x 和 y 参数进行操作
  // 其余参数传给原始函数
  return baseFunction(restConfig);
}
```

上面代码中，原始函数`baseFunction`接受`a`和`b`作为参数，函数`wrapperFunction`在`baseFunction`的基础上进行了扩展，能够接受多余的参数，并且保留原始函数的行为。

##### 扩展运算符

对象的扩展运算符（`...`）用于取出参数对象的所有可遍历属性，拷贝到当前对象之中。

```javascript
let z = { a: 3, b: 4 };
let n = { ...z };
n // { a: 3, b: 4 }
```

由于数组是特殊的对象，所以对象的扩展运算符也可以用于数组。

```javascript
let foo = { ...['a', 'b', 'c'] };
foo
// {0: "a", 1: "b", 2: "c"}
```

如果扩展运算符后面是一个空对象，则没有任何效果。

```javascript
{...{}, a: 1}
// { a: 1 }
```

如果扩展运算符后面不是对象，则会自动将其转为对象。

```javascript
// 等同于 {...Object(1)}
{...1} // {}
```

```javascript
// 等同于 {...Object(true)}
{...true} // {}

// 等同于 {...Object(undefined)}
{...undefined} // {}

// 等同于 {...Object(null)}
{...null} // {}
```

如果扩展运算符后面是字符串，它会自动转成一个类似数组的对象，因此返回的不是空对象。

```javascript
{...'hello'}
// {0: "h", 1: "e", 2: "l", 3: "l", 4: "o"}
```

对象的扩展运算符，只会返回参数对象自身的、可枚举的属性，这一点要特别小心，尤其是用于类的实例对象时。

```javascript
class C {
  p = 12;
  m() {}
}

let c = new C();
let clone = { ...c };

clone.p; // ok
clone.m(); // 报错
```

上面示例中，`c`是`C`类的实例对象，对其进行扩展运算时，只会返回`c`自身的属性`c.p`，而不会返回`c`的方法`c.m()`，因为这个方法定义在`C`的原型对象上

对象的扩展运算符等同于使用`Object.assign()`方法。

```javascript
let aClone = { ...a };
// 等同于
let aClone = Object.assign({}, a);
```

上面的例子只是拷贝了对象实例的属性，如果想完整克隆一个对象，还拷贝对象原型的属性，可以采用下面的写法。

```javascript
// 写法一
const clone1 = {
  __proto__: Object.getPrototypeOf(obj),
  ...obj
};

// 写法二
const clone2 = Object.assign(
  Object.create(Object.getPrototypeOf(obj)),
  obj
);

// 写法三
const clone3 = Object.create(
  Object.getPrototypeOf(obj),
  Object.getOwnPropertyDescriptors(obj)
)
```

上面代码中，写法一的`__proto__`属性在非浏览器的环境不一定部署，因此推荐使用写法二和写法三。

扩展运算符可以用于合并两个对象。

```javascript
let ab = { ...a, ...b };
// 等同于
let ab = Object.assign({}, a, b);
```

如果用户自定义的属性，放在扩展运算符后面，则扩展运算符内部的同名属性会被覆盖掉。

```javascript
let aWithOverrides = { ...a, x: 1, y: 2 };
// 等同于
let aWithOverrides = { ...a, ...{ x: 1, y: 2 } };
// 等同于
let x = 1, y = 2, aWithOverrides = { ...a, x, y };
// 等同于
let aWithOverrides = Object.assign({}, a, { x: 1, y: 2 });
```

上面代码中，`a`对象的`x`属性和`y`属性，拷贝到新对象后会被覆盖掉。

这可以用来修改现有对象部分的属性

```javascript
let newVersion = {
  ...previousVersion,
  name: 'New Name' // Override the name property
};
```

`newVersion`对象自定义了`name`属性，其他属性全部复制自`previousVersion`对象。

如果把自定义属性放在扩展运算符前面，就变成了设置新对象的默认属性值。

```javascript
let aWithDefaults = { x: 1, y: 2, ...a };
// 等同于
let aWithDefaults = Object.assign({}, { x: 1, y: 2 }, a);
// 等同于
let aWithDefaults = Object.assign({ x: 1, y: 2 }, a);
```

与数组的扩展运算符一样，对象的扩展运算符后面可以跟表达式。

```javascript
const obj = {
  ...(x > 1 ? {a: 1} : {}),
  b: 2,
};
```

扩展运算符的参数对象之中，如果有取值函数`get`，这个函数是会执行的。

```javascript
let a = {
  get x() {
    throw new Error('not throw yet');
  }
}

let aWithXGetter = { ...a }; // 报错
```

取值函数`get`在扩展`a`对象时会自动执行，导致报错。



### 20.模块化

模块化是指将一个大的程序文件，拆分成许多小的文件，然后将小文件组合起来。

#### 模块化的好处

模块化的优势有以下几点：

- 防止命名冲突
- 代码复用
- 高维护性

#### 模块化规范产品

ES6 之前的模块化规范有：

- CommonJS => NodeJS、Browserify
- AMD => requireJS
- CMD => seaJS

#### ES6 模块化语法

模块功能主要由两个命令构成：export 和 import。 

- export 命令用于规定模块的对外接口
- import 命令用于输入其他模块提供的功能

#### 严格模式

ES6 的模块自动采用严格模式，不管你有没有在模块头部加上`"use strict";`。

严格模式主要有以下限制。

- 变量必须声明后再使用
- 函数的参数不能有同名属性，否则报错
- 不能使用`with`语句
- 不能对只读属性赋值，否则报错
- 不能使用前缀 0 表示八进制数，否则报错
- 不能删除不可删除的属性，否则报错
- 不能删除变量`delete prop`，会报错，只能删除属性`delete global[prop]`
- `eval`不会在它的外层作用域引入变量
- `eval`和`arguments`不能被重新赋值
- `arguments`不会自动反映函数参数的变化
- 不能使用`arguments.callee`
- 不能使用`arguments.caller`
- 禁止`this`指向全局对象
- 不能使用`fn.caller`和`fn.arguments`获取函数调用的堆栈
- 增加了保留字（比如`protected`、`static`和`interface`）

上面这些限制，模块都必须遵守。严格模式是 ES5 引入的，不属于 ES6

其中，尤其需要注意`this`的限制。ES6 模块之中，顶层的`this`指向`undefined`，即不应该在顶层代码使用`this`。



模块功能主要由两个命令构成：`export`和`import`。`export`命令用于规定模块的对外接口，`import`命令用于输入其他模块提供的功能。

#### export 命令

一个模块就是一个独立的文件。该文件内部的所有变量，外部无法获取。如果你希望外部能够读取模块内部的某个变量，就必须使用`export`关键字输出该变量。

**多行暴露：**

```javascript
// profile.js
export var firstName = 'Michael';
export var lastName = 'Jackson';
export var year = 1958;
```

还有另外一种。**统一暴露：**

```javascript
// profile.js
var firstName = 'Michael';
var lastName = 'Jackson';
var year = 1958;

export { firstName, lastName, year };
```

`export`命令除了输出变量，还可以输出函数或类（class）。

```javascript
export function multiply(x, y) {
  return x * y;
};
```

通常情况下，`export`输出的变量就是本来的名字，但是可以使用`as`关键字重命名。

```javascript
function v1() { ... }
function v2() { ... }

export {
  v1 as streamV1,
  v2 as streamV2,
  v2 as streamLatestVersion
};
```

**需要特别注意的是，**`export`命令规定的是对外的接口，必须与模块内部的变量建立一一对应关系。

```javascript
// 报错
export 1;

// 报错
var m = 1;
export m;
```

上面两种写法都会报错，因为没有提供对外的接口。第一种写法直接输出 1，第二种写法通过变量`m`，还是直接输出 1。`1`只是一个值，不是接口。正确的写法是下面这样。

```javascript
// 写法一
export var m = 1;

// 写法二
var m = 1;
export {m};

// 写法三
var n = 1;
export {n as m};
```

上面三种写法都是正确的，规定了对外的接口`m`。其他脚本可以通过这个接口，取到值`1`。它们的实质是，在接口名与模块内部变量之间，建立了一一对应的关系。

`function`和`class`的输出，也必须遵守这样的写法。

```javascript
// 报错
function f() {}
export f;

// 正确
export function f() {};

// 正确
function f() {}
export {f};
```

另外，`export`语句输出的接口，与其对应的值是动态绑定关系，即通过该接口，可以取到模块内部实时的值。

```javascript
export var foo = 'bar';
setTimeout(() => foo = 'baz', 500);
```

上面代码输出变量`foo`，值为`bar`，500 毫秒之后变成`baz`。

这一点与 CommonJS 规范完全不同。CommonJS 模块输出的是值的缓存，不存在动态更新。

最后，`export`命令可以出现在模块的任何位置，只要处于模块顶层就可以。如果处于块级作用域内，就会报错，`import`命令也是如此。这是因为处于条件代码块之中，就没法做静态优化了，违背了 ES6 模块的设计初衷。

```javascript
function foo() {
  export default 'bar' // SyntaxError
}
foo()
```

最后，还有**默认暴露：export default**

使用`import`命令的时候，用户需要知道所要加载的变量名或函数名，否则无法加载。但是，用户肯定希望快速上手，未必愿意阅读文档，去了解模块有哪些属性和方法。

为了给用户提供方便，让他们不用阅读文档就能加载模块，就要用到`export default`命令，为模块指定默认输出。

```javascript
// export-default.js
export default function () {
  console.log('foo');
}
```

它的默认输出是一个函数

其他模块加载该模块时，`import`命令可以为该匿名函数指定任意名字。

```javascript
// import-default.js
import customName from './export-default';
customName(); // 'foo'
```

`export default`命令用在非匿名函数前，也是可以的。

```javascript
// export-default.js
export default function foo() {
  console.log('foo');
}

// 或者写成

function foo() {
  console.log('foo');
}

export default foo;
```

比较一下默认输出和正常输出。

```javascript
// 第一组
export default function crc32() { // 输出
  // ...
}

import crc32 from 'crc32'; // 输入

// 第二组
export function crc32() { // 输出
  // ...
};

import {crc32} from 'crc32'; // 输入
```

上面代码的两组写法，第一组是使用`export default`时，对应的`import`语句不需要使用大括号；第二组是不使用`export default`时，对应的`import`语句需要使用大括号。

`export default`命令用于指定模块的默认输出。显然，一个模块只能有一个默认输出，因此`export default`命令只能使用一次。所以，import命令后面才不用加大括号，因为只可能唯一对应`export default`命令。

本质上，`export default`就是输出一个叫做`default`的变量或方法，然后系统允许你为它取任意名字。所以，下面的写法是有效的。

```javascript
// modules.js
function add(x, y) {
  return x * y;
}
export {add as default};
// 等同于
// export default add;

// app.js
import { default as foo } from 'modules';
// 等同于
// import foo from 'modules';
```

所以它后面不能跟变量声明语句。

```javascript
// 正确
export var a = 1;

// 正确
var a = 1;
export default a;

// 错误
export default var a = 1;
```

同样地，因为`export default`命令的本质是将后面的值，赋给`default`变量，所以可以直接将一个值写在`export default`之后。

```javascript
// 正确
export default 42;

// 报错
export 42;
```

有了`export default`命令，输入模块时就非常直观了，以输入 lodash 模块为例。

```javascript
import _ from 'lodash';
```

如果想在一条`import`语句中，同时输入默认方法和其他接口，可以写成下面这样。

```javascript
import _, { each, forEach } from 'lodash';
```

对应上面代码的`export`语句如下。

```javascript
export default function (obj) {
  // ···
}

export function each(obj, iterator, context) {
  // ···
}

export { each as forEach };
```

上面代码的最后一行的意思是，暴露出`forEach`接口，默认指向`each`接口，即`forEach`和`each`指向同一个方法。

`export default`也可以用来输出类。

```javascript
// MyClass.js
export default class { ... }

// main.js
import MyClass from 'MyClass';
let o = new MyClass();
```



#### import 命令

1.通用的导入方式

```
import * as m1 from "./src/js/m1.js";
// //引入 m2.js 模块内容
import * as m2 from "./src/js/m2.js";
// //引入 m3.js
import * as m3 from "./src/js/m3.js";
```

2.解构赋值形式

```
import {school, teach} from "./src/js/m1.js";
import {school as guigu, findJob} from "./src/js/m2.js";
import {default as m3} from "./src/js/m3.js";
```

3.简便形式  针对默认暴露

```
import m3 from "./src/js/m3.js";
```



使用`export`命令定义了模块的对外接口以后，其他 JS 文件就可以通过`import`命令加载这个模块。

```javascript
// main.js
import { firstName, lastName, year } from './profile.js';

function setName(element) {
  element.textContent = firstName + ' ' + lastName;
}
```

如果想为输入的变量重新取一个名字，`import`命令要使用`as`关键字，将输入的变量重命名。

```javascript
import { lastName as surname } from './profile.js';
```

`import`命令输入的变量都是只读的，因为它的本质是输入接口。也就是说，不允许在加载模块的脚本里面，改写接口。

```javascript
import {a} from './xxx.js'

a = {}; // Syntax Error : 'a' is read-only;
```

上面代码中，脚本加载了变量`a`，对其重新赋值就会报错，因为`a`是一个只读的接口。但是，如果`a`是一个对象，改写`a`的属性是允许的。

```javascript
import {a} from './xxx.js'

a.foo = 'hello'; // 合法操作
```

上面代码中，`a`的属性可以成功改写，并且其他模块也可以读到改写后的值。不过，这种写法很难查错，建议凡是输入的变量，都当作完全只读，不要轻易改变它的属性。

**注意**，`import`命令具有提升效果，会提升到整个模块的头部，首先执行。

```javascript
foo();

import { foo } from 'my_module';
```

上面的代码不会报错，因为`import`的执行早于`foo`的调用。这种行为的本质是，`import`命令是编译阶段执行的，在代码运行之前。

由于`import`是静态执行，所以不能使用表达式和变量，这些只有在运行时才能得到结果的语法结构。

```javascript
// 报错
import { 'f' + 'oo' } from 'my_module';

// 报错
let module = 'my_module';
import { foo } from module;

// 报错
if (x === 1) {
  import { foo } from 'module1';
} else {
  import { foo } from 'module2';
}
```

最后，`import`语句会执行所加载的模块，因此可以有下面的写法。

```javascript
import 'lodash';
```

上面代码仅仅执行`lodash`模块，但是不输入任何值。

如果多次重复执行同一句`import`语句，那么只会执行一次，而不会执行多次。

```javascript
import 'lodash';
import 'lodash';
```

上面代码加载了两次`lodash`，但是只会执行一次。

```javascript
import { foo } from 'my_module';
import { bar } from 'my_module';

// 等同于
import { foo, bar } from 'my_module';
```

上面代码中，虽然`foo`和`bar`在两个语句中加载，但是它们对应的是同一个`my_module`模块。也就是说，`import`语句是 Singleton 模式。

目前阶段，通过 Babel 转码，CommonJS 模块的`require`命令和 ES6 模块的`import`命令，可以写在同一个模块里面，但是最好不要这样做。因为`import`在静态解析阶段执行，所以它是一个模块之中最早执行的。下面的代码可能不会得到预期结果。

```javascript
require('core-js/modules/es6.symbol');
require('core-js/modules/es6.promise');
import React from 'React';
```

#### export 与 import 的复合写法

如果在一个模块之中，先输入后输出同一个模块，`import`语句可以与`export`语句写在一起。

```javascript
export { foo, bar } from 'my_module';

// 可以简单理解为
import { foo, bar } from 'my_module';
export { foo, bar };
```

上面代码中，`export`和`import`语句可以结合在一起，写成一行。但需要注意的是，写成一行以后，`foo`和`bar`实际上并没有被导入当前模块，只是相当于对外转发了这两个接口，导致当前模块不能直接使用`foo`和`bar`。

模块的接口改名和整体输出，也可以采用这种写法。

```javascript
// 接口改名
export { foo as myFoo } from 'my_module';

// 整体输出
export * from 'my_module';
```

默认接口的写法如下。

```javascript
export { default } from 'foo';
```

具名接口改为默认接口的写法如下。

```javascript
export { es6 as default } from './someModule';

// 等同于
import { es6 } from './someModule';
export default es6;
```

同样地，默认接口也可以改名为具名接口。

```javascript
export { default as es6 } from './someModule';
```

ES2020 之前，有一种`import`语句，没有对应的复合写法。

```javascript
import * as someIdentifier from "someModule";
```

[ES2020](https://github.com/tc39/proposal-export-ns-from)补上了这个写法。

```javascript
export * as ns from "mod";

// 等同于
import * as ns from "mod";
export {ns};
```

#### 模块的继承

模块之间也可以继承。

假设有一个`circleplus`模块，继承了`circle`模块。

```javascript
// circleplus.js

export * from 'circle';
export var e = 2.71828182846;
export default function(x) {
  return Math.exp(x);
}
```

上面代码中的`export *`，表示再输出`circle`模块的所有属性和方法。注意，`export *`命令会忽略`circle`模块的`default`方法。然后，上面代码又输出了自定义的`e`变量和默认方法。

这时，也可以将`circle`的属性或方法，改名后再输出。

```javascript
// circleplus.js

export { area as circleArea } from 'circle';
```

上面代码表示，只输出`circle`模块的`area`方法，且将其改名为`circleArea`。

加载上面模块的写法如下。

```javascript
// main.js

import * as math from 'circleplus';
import exp from 'circleplus';
console.log(exp(math.e));
```

#### 跨模块常量

`const`声明的常量只在当前代码块有效。如果想设置跨模块的常量（即跨多个文件），或者说一个值要被多个模块共享，可以采用下面的写法。

```javascript
// constants.js 模块
export const A = 1;
export const B = 3;
export const C = 4;

// test1.js 模块
import * as constants from './constants';
console.log(constants.A); // 1
console.log(constants.B); // 3

// test2.js 模块
import {A, B} from './constants';
console.log(A); // 1
console.log(B); // 3
```

如果要使用的常量非常多，可以建一个专门的`constants`目录，将各种常量写在不同的文件里面，保存在该目录下。

```javascript
// constants/db.js
export const db = {
  url: 'http://my.couchdbserver.local:5984',
  admin_username: 'admin',
  admin_password: 'admin password'
};

// constants/user.js
export const users = ['root', 'admin', 'staff', 'ceo', 'chief', 'moderator'];
```

然后，将这些文件输出的常量，合并在`index.js`里面。

```javascript
// constants/index.js
export {db} from './db';
export {users} from './users';
```

使用的时候，直接加载`index.js`就可以了。

```javascript
// script.js
import {db, users} from './constants/index';
```

#### import()

`import`命令会被 JavaScript 引擎静态分析，先于模块内的其他语句执行（`import`命令叫做“连接” binding 其实更合适）。所以，下面的代码会报错。

```javascript
// 报错
if (x === 2) {
  import MyModual from './myModual';
}
```

由于引擎处理`import`语句是在编译时，这时不会去分析或执行`if`语句。也就是说，`import`和`export`命令只能在模块的顶层，不能在代码块之中。

[ES2020提案](https://github.com/tc39/proposal-dynamic-import) 引入`import()`函数，支持动态加载模块。

```javascript
import(specifier)
```

上面代码中，`import`函数的参数`specifier`，指定所要加载的模块的位置。`import`命令能够接受什么参数，`import()`函数就能接受什么参数，两者区别主要是后者为动态加载。

`import()`返回一个 Promise 对象。

```javascript
const main = document.querySelector('main');

import(`./section-modules/${someVariable}.js`)
  .then(module => {
    module.loadPageInto(main);
  })
  .catch(err => {
    main.textContent = err.message;
  });
```

`import()`函数可以用在任何地方，不仅仅是模块，非模块的脚本也可以使用。它是运行时执行，也就是说，什么时候运行到这一句，就会加载指定的模块。另外，`import()`函数与所加载的模块没有静态连接关系，这点也是与`import`语句不相同。`import()`类似于 Node 的`require`方法，区别主要是前者是异步加载，后者是同步加载。

**适用场合：**

（1）按需加载。

`import()`可以在需要的时候，再加载某个模块。

```javascript
button.addEventListener('click', event => {
  import('./dialogBox.js')
  .then(dialogBox => {
    dialogBox.open();
  })
  .catch(error => {
    /* Error handling */
  })
});
```

上面代码中，`import()`方法放在`click`事件的监听函数之中，只有用户点击了按钮，才会加载这个模块。

（2）条件加载

`import()`可以放在`if`代码块，根据不同的情况，加载不同的模块。

```javascript
if (condition) {
  import('moduleA').then(...);
} else {
  import('moduleB').then(...);
}
```

上面代码中，如果满足条件，就加载模块 A，否则加载模块 B。

（3）动态的模块路径

`import()`允许模块路径动态生成。

```javascript
import(f())
.then(...);
```

上面代码中，根据函数`f`的返回结果，加载不同的模块。

`import()`加载模块成功以后，这个模块会作为一个对象，当作`then`方法的参数。因此，可以使用对象解构赋值的语法，获取输出接口。

```javascript
import('./myModule.js')
.then(({export1, export2}) => {
  // ...·
});
```

上面代码中，`export1`和`export2`都是`myModule.js`的输出接口，可以解构获得。

如果模块有`default`输出接口，可以用参数直接获得。

```javascript
import('./myModule.js')
.then(myModule => {
  console.log(myModule.default);
});
```

上面的代码也可以使用具名输入的形式。

```javascript
import('./myModule.js')
.then(({default: theDefault}) => {
  console.log(theDefault);
});
```

如果想同时加载多个模块，可以采用下面的写法。

```javascript
Promise.all([
  import('./module1.js'),
  import('./module2.js'),
  import('./module3.js'),
])
.then(([module1, module2, module3]) => {
   ···
});
```

`import()`也可以用在 async 函数之中。

```javascript
async function main() {
  const myModule = await import('./myModule.js');
  const {export1, export2} = await import('./myModule.js');
  const [module1, module2, module3] =
    await Promise.all([
      import('./module1.js'),
      import('./module2.js'),
      import('./module3.js'),
    ]);
}
main();
```

## 三、ES7

### 1.Array.prototype.includes

Includes 方法用来检测数组中是否包含某个元素，返回布尔类型值

```
const mingzhu = ['西游记','红楼梦','三国演义','水浒传'];

//判断
console.log(mingzhu.includes('西游记')); //true
console.log(mingzhu.includes('金瓶梅')); //false
```

### 2.指数操作符

在 ES7 中引入指数运算符「**」，用来实现幂运算，功能与 Math.pow 结果相同

```
console.log(2 ** 10); //1024
console.log(Math.pow(2, 10)); //1024
```

## 四、ES8

### 1.async 和 await

ES2017 标准引入了 async 函数，使得异步操作变得更加方便。

async 函数，就是 Generator 函数的语法糖。

```javascript
const fs = require('fs');

const readFile = function (fileName) {
  return new Promise(function (resolve, reject) {
    fs.readFile(fileName, function(error, data) {
      if (error) return reject(error);
      resolve(data);
    });
  });
};

const gen = function* () {
  const f1 = yield readFile('/etc/fstab');
  const f2 = yield readFile('/etc/shells');
  console.log(f1.toString());
  console.log(f2.toString());
};
```

上面代码的函数`gen`可以写成`async`函数，就是下面这样。

```javascript
const asyncReadFile = async function () {
  const f1 = await readFile('/etc/fstab');
  const f2 = await readFile('/etc/shells');
  console.log(f1.toString());
  console.log(f2.toString());
};
```

一比较就会发现，`async`函数就是将 Generator 函数的星号（`*`）替换成`async`，将`yield`替换成`await`，仅此而已。

`async`函数对 Generator 函数的改进，体现在以下四点。

（1）内置执行器。

Generator 函数的执行必须靠执行器，所以才有了`co`模块，而`async`函数自带执行器。也就是说，`async`函数的执行，与普通函数一模一样，只要一行。

```javascript
asyncReadFile();
```

上面的代码调用了`asyncReadFile`函数，然后它就会自动执行，输出最后结果。这完全不像 Generator 函数，需要调用`next`方法，或者用`co`模块，才能真正执行，得到最后结果。

（2）更好的语义。

`async`和`await`，比起星号和`yield`，语义更清楚了。`async`表示函数里有异步操作，`await`表示紧跟在后面的表达式需要等待结果。

（3）更广的适用性。

`co`模块约定，`yield`命令后面只能是 Thunk 函数或 Promise 对象，而`async`函数的`await`命令后面，可以是 Promise 对象和原始类型的值（数值、字符串和布尔值，但这时会自动转成立即 resolved 的 Promise 对象）。

（4）返回值是 Promise。

`async`函数的返回值是 Promise 对象，这比 Generator 函数的返回值是 Iterator 对象方便多了。你可以用`then`方法指定下一步的操作。

进一步说，`async`函数完全可以看作多个异步操作，包装成的一个 Promise 对象，而`await`命令就是内部`then`命令的语法糖。

#### 基本用法

`async`函数返回一个 Promise 对象，可以使用`then`方法添加回调函数。当函数执行的时候，一旦遇到`await`就会先返回，等到异步操作完成，再接着执行函数体内后面的语句。

```javascript
async function getStockPriceByName(name) {
  const symbol = await getStockSymbol(name);
  const stockPrice = await getStockPrice(symbol);
  return stockPrice;
}

getStockPriceByName('goog').then(function (result) {
  console.log(result);
});
```

#### 语法

`async`函数的语法规则总体上比较简单，难点是错误处理机制。

##### 返回 Promise 对象

`async`函数内部`return`语句返回的值，会成为`then`方法回调函数的参数。

```javascript
async function f() {
  return 'hello world';
}

f().then(v => console.log(v))
// "hello world"
```

`async`函数内部抛出错误，会导致返回的 Promise 对象变为`reject`状态。抛出的错误对象会被`catch`方法回调函数接收到。

```javascript
async function f() {
  throw new Error('出错了');
}

f().then(
  v => console.log('resolve', v),
  e => console.log('reject', e)
)
//reject Error: 出错了
```

##### Promise 对象的状态变化

`async`函数返回的 Promise 对象，必须等到内部所有`await`命令后面的 Promise 对象执行完，才会发生状态改变，除非遇到`return`语句或者抛出错误。也就是说，只有`async`函数内部的异步操作执行完，才会执行`then`方法指定的回调函数。

```javascript
async function getTitle(url) {
  let response = await fetch(url);
  let html = await response.text();
  return html.match(/<title>([\s\S]+)<\/title>/i)[1];
}
getTitle('https://tc39.github.io/ecma262/').then(console.log)
// "ECMAScript 2017 Language Specification"
```

上面代码中，函数`getTitle`内部有三个操作：抓取网页、取出文本、匹配页面标题。只有这三个操作全部完成，才会执行`then`方法里面的`console.log`。

##### await 命令

正常情况下，`await`命令后面是一个 Promise 对象，返回该对象的结果。如果不是 Promise 对象，就直接返回对应的值。

```javascript
async function f() {
  // 等同于
  // return 123;
  return await 123;
}

f().then(v => console.log(v))
// 123
```

另一种情况是，`await`命令后面是一个`thenable`对象（即定义了`then`方法的对象），那么`await`会将其等同于 Promise 对象。

```javascript
class Sleep {
  constructor(timeout) {
    this.timeout = timeout;
  }
  then(resolve, reject) {
    const startTime = Date.now();
    setTimeout(
      () => resolve(Date.now() - startTime),
      this.timeout
    );
  }
}

(async () => {
  const sleepTime = await new Sleep(1000);
  console.log(sleepTime);
})();
// 1000
```

```javascript
class Sleep {
  constructor(timeout) {
    this.timeout = timeout;
  }
  then(resolve, reject) {
    const startTime = Date.now();
    setTimeout(
      () => resolve(Date.now() - startTime),
      this.timeout
    );
  }
}

(async () => {
  const sleepTime = await new Sleep(1000);
  console.log(sleepTime);
})();
// 1000
```

上面代码中，`await`命令后面是一个`Sleep`对象的实例。这个实例不是 Promise 对象，但是因为定义了`then`方法，`await`会将其视为`Promise`处理。

这个例子还演示了如何实现休眠效果。JavaScript 一直没有休眠的语法，但是借助`await`命令就可以让程序停顿指定的时间。下面给出了一个简化的`sleep`实现。

```javascript
function sleep(interval) {
  return new Promise(resolve => {
    setTimeout(resolve, interval);
  })
}

// 用法
async function one2FiveInAsync() {
  for(let i = 1; i <= 5; i++) {
    console.log(i);
    await sleep(1000);
  }
}

one2FiveInAsync();
```

`await`命令后面的 Promise 对象如果变为`reject`状态，则`reject`的参数会被`catch`方法的回调函数接收到。

```javascript
async function f() {
  await Promise.reject('出错了');
}

f()
.then(v => console.log(v))
.catch(e => console.log(e))
// 出错了
```

注意，上面代码中，`await`语句前面没有`return`，但是`reject`方法的参数依然传入了`catch`方法的回调函数。这里如果在`await`前面加上`return`，效果是一样的。

任何一个`await`语句后面的 Promise 对象变为`reject`状态，那么整个`async`函数都会中断执行。

```javascript
async function f() {
  await Promise.reject('出错了');
  await Promise.resolve('hello world'); // 不会执行
}
```

上面代码中，第二个`await`语句是不会执行的，因为第一个`await`语句状态变成了`reject`。

有时，我们希望即使前一个异步操作失败，也不要中断后面的异步操作。这时可以将第一个`await`放在`try...catch`结构里面，这样不管这个异步操作是否成功，第二个`await`都会执行。

```javascript
async function f() {
  try {
    await Promise.reject('出错了');
  } catch(e) {
  }
  return await Promise.resolve('hello world');
}

f()
.then(v => console.log(v))
// hello world
```

另一种方法是`await`后面的 Promise 对象再跟一个`catch`方法，处理前面可能出现的错误。

```javascript
async function f() {
  await Promise.reject('出错了')
    .catch(e => console.log(e));
  return await Promise.resolve('hello world');
}

f()
.then(v => console.log(v))
// 出错了
// hello world
```

##### 错误处理

如果`await`后面的异步操作出错，那么等同于`async`函数返回的 Promise 对象被`reject`。

```javascript
async function f() {
  await new Promise(function (resolve, reject) {
    throw new Error('出错了');
  });
}

f()
.then(v => console.log(v))
.catch(e => console.log(e))
// Error：出错了
```

上面代码中，`async`函数`f`执行后，`await`后面的 Promise 对象会抛出一个错误对象，导致`catch`方法的回调函数被调用，它的参数就是抛出的错误对象。具体的执行机制，可以参考后文的“async 函数的实现原理”。

防止出错的方法，也是将其放在`try...catch`代码块之中。

```javascript
async function f() {
  try {
    await new Promise(function (resolve, reject) {
      throw new Error('出错了');
    });
  } catch(e) {
  }
  return await('hello world');
}
```

如果有多个`await`命令，可以统一放在`try...catch`结构中。

```javascript
async function main() {
  try {
    const val1 = await firstStep();
    const val2 = await secondStep(val1);
    const val3 = await thirdStep(val1, val2);

    console.log('Final: ', val3);
  }
  catch (err) {
    console.error(err);
  }
}
```

下面的例子使用`try...catch`结构，实现多次重复尝试。

```javascript
const superagent = require('superagent');
const NUM_RETRIES = 3;

async function test() {
  let i;
  for (i = 0; i < NUM_RETRIES; ++i) {
    try {
      await superagent.get('http://google.com/this-throws-an-error');
      break;
    } catch(err) {}
  }
  console.log(i); // 3
}

test();
```

上面代码中，如果`await`操作成功，就会使用`break`语句退出循环；如果失败，会被`catch`语句捕捉，然后进入下一轮循环。

##### 使用注意点

第一点，前面已经说过，`await`命令后面的`Promise`对象，运行结果可能是`rejected`，所以最好把`await`命令放在`try...catch`代码块中。

```javascript
async function myFunction() {
  try {
    await somethingThatReturnsAPromise();
  } catch (err) {
    console.log(err);
  }
}

// 另一种写法

async function myFunction() {
  await somethingThatReturnsAPromise()
  .catch(function (err) {
    console.log(err);
  });
}
```

第二点，多个`await`命令后面的异步操作，如果不存在继发关系，最好让它们同时触发。

```javascript
let foo = await getFoo();
let bar = await getBar();
```

上面代码中，`getFoo`和`getBar`是两个独立的异步操作（即互不依赖），被写成继发关系。这样比较耗时，因为只有`getFoo`完成以后，才会执行`getBar`，完全可以让它们同时触发。

```javascript
// 写法一
let [foo, bar] = await Promise.all([getFoo(), getBar()]);

// 写法二
let fooPromise = getFoo();
let barPromise = getBar();
let foo = await fooPromise;
let bar = await barPromise;
```

上面两种写法，`getFoo`和`getBar`都是同时触发，这样就会缩短程序的执行时间。

第三点，`await`命令只能用在`async`函数之中，如果用在普通函数，就会报错。

```javascript
async function dbFuc(db) {
  let docs = [{}, {}, {}];

  // 报错
  docs.forEach(function (doc) {
    await db.post(doc);
  });
}
```

上面代码会报错，因为`await`用在普通函数之中了。但是，如果将`forEach`方法的参数改成`async`函数，也有问题。

```javascript
function dbFuc(db) { //这里不需要 async
  let docs = [{}, {}, {}];

  // 可能得到错误结果
  docs.forEach(async function (doc) {
    await db.post(doc);
  });
}
```

上面代码可能不会正常工作，原因是这时三个`db.post()`操作将是并发执行，也就是同时执行，而不是继发执行。正确的写法是采用`for`循环。

```javascript
async function dbFuc(db) {
  let docs = [{}, {}, {}];

  for (let doc of docs) {
    await db.post(doc);
  }
}
```

另一种方法是使用数组的`reduce()`方法。

```javascript
async function dbFuc(db) {
  let docs = [{}, {}, {}];

  await docs.reduce(async (_, doc) => {
    await _;
    await db.post(doc);
  }, undefined);
}
```

上面例子中，`reduce()`方法的第一个参数是`async`函数，导致该函数的第一个参数是前一步操作返回的 Promise 对象，所以必须使用`await`等待它操作结束。另外，`reduce()`方法返回的是`docs`数组最后一个成员的`async`函数的执行结果，也是一个 Promise 对象，导致在它前面也必须加上`await`。

上面的`reduce()`的参数函数里面没有`return`语句，原因是这个函数的主要目的是`db.post()`操作，不是返回值。而且`async`函数不管有没有`return`语句，总是返回一个 Promise 对象，所以这里的`return`是不必要的。

如果确实希望多个请求并发执行，可以使用`Promise.all`方法。当三个请求都会`resolved`时，下面两种写法效果相同。

```javascript
async function dbFuc(db) {
  let docs = [{}, {}, {}];
  let promises = docs.map((doc) => db.post(doc));

  let results = await Promise.all(promises);
  console.log(results);
}

// 或者使用下面的写法

async function dbFuc(db) {
  let docs = [{}, {}, {}];
  let promises = docs.map((doc) => db.post(doc));

  let results = [];
  for (let promise of promises) {
    results.push(await promise);
  }
  console.log(results);
}
```

第四点，async 函数可以保留运行堆栈。

```javascript
const a = () => {
  b().then(() => c());
};
```

上面代码中，函数`a`内部运行了一个异步任务`b()`。当`b()`运行的时候，函数`a()`不会中断，而是继续执行。等到`b()`运行结束，可能`a()`早就运行结束了，`b()`所在的上下文环境已经消失了。如果`b()`或`c()`报错，错误堆栈将不包括`a()`。

现在将这个例子改成`async`函数。

```javascript
const a = async () => {
  await b();
  c();
};
```

上面代码中，`b()`运行的时候，`a()`是暂停执行，上下文环境都保存着。一旦`b()`或`c()`报错，错误堆栈将包括`a()`。

#### async 函数的实现原理

async 函数的实现原理，就是将 Generator 函数和自动执行器，包装在一个函数里。

```javascript
async function fn(args) {
  // ...
}

// 等同于

function fn(args) {
  return spawn(function* () {
    // ...
  });
}
```

所有的`async`函数都可以写成上面的第二种形式，其中的`spawn`函数就是自动执行器。

#### 与其他异步处理方法的比较

async 函数与 Promise、Generator 函数的比较：

首先是 Promise 的写法。

```javascript
function chainAnimationsPromise(elem, animations) {

  // 变量ret用来保存上一个动画的返回值
  let ret = null;

  // 新建一个空的Promise
  let p = Promise.resolve();

  // 使用then方法，添加所有动画
  for(let anim of animations) {
    p = p.then(function(val) {
      ret = val;
      return anim(elem);
    });
  }

  // 返回一个部署了错误捕捉机制的Promise
  return p.catch(function(e) {
    /* 忽略错误，继续执行 */
  }).then(function() {
    return ret;
  });

}
```

虽然 Promise 的写法比回调函数的写法大大改进，但是一眼看上去，代码完全都是 Promise 的 API（`then`、`catch`等等），操作本身的语义反而不容易看出来。

接着是 Generator 函数的写法。

```javascript
function chainAnimationsGenerator(elem, animations) {

  return spawn(function*() {
    let ret = null;
    try {
      for(let anim of animations) {
        ret = yield anim(elem);
      }
    } catch(e) {
      /* 忽略错误，继续执行 */
    }
    return ret;
  });

}
```

上面代码使用 Generator 函数遍历了每个动画，语义比 Promise 写法更清晰，用户定义的操作全部都出现在`spawn`函数的内部。这个写法的问题在于，必须有一个任务运行器，自动执行 Generator 函数，上面代码的`spawn`函数就是自动执行器，它返回一个 Promise 对象，而且必须保证`yield`语句后面的表达式，必须返回一个 Promise。

最后是 async 函数的写法。

```javascript
async function chainAnimationsAsync(elem, animations) {
  let ret = null;
  try {
    for(let anim of animations) {
      ret = await anim(elem);
    }
  } catch(e) {
    /* 忽略错误，继续执行 */
  }
  return ret;
}
```

可以看到 Async 函数的实现最简洁，最符合语义，几乎没有语义不相关的代码。它将 Generator 写法中的自动执行器，改在语言层面提供，不暴露给用户，因此代码量最少。如果使用 Generator 写法，自动执行器需要用户自己提供。

### 2.Object.values和 Object.entries

Object.values()方法返回一个给定对象的所有可枚举属性值的数组

Object.entries()方法返回一个给定对象自身可遍历属性 [key,value] 的数组

```
//声明对象
const school = {
    name:"guigu",
    cities:['北京','上海','深圳'],
    xueke: ['前端','Java','大数据','运维']
};
```

```
//获取对象所有的键
console.log(Object.keys(school)); // ['name', 'cities', 'xueke']
//获取对象所有的值
console.log(Object.values(school)); //['guigu', Array(3), Array(4)]
//entries
console.log(Object.entries(school)); //[['name', 'guigu'], ['cities', Array(3)], ['xueke', Array(4)]]
```

```
//创建 Map
const m = new Map(Object.entries(school));
```

### 3.Object.getOwnPropertyDescriptors

该方法返回指定对象所有自身属性的描述对象

```
console.log(Object.getOwnPropertyDescriptors(school));
```

![自身属性的描述对象](https://raw.githubusercontent.com/weixiaoyun/Images/ES6/%E8%87%AA%E8%BA%AB%E5%B1%9E%E6%80%A7%E7%9A%84%E6%8F%8F%E8%BF%B0%E5%AF%B9%E8%B1%A1.png)

```
const obj = Object.create(null, {
    name: {
        //设置值
        value: '尚硅谷',
        //属性特性
        writable: true,
        configurable: true,
        enumerable: true
    }
});
```

## 五、ES9

### 1.Rest/Spread 属性

Rest 参数与 spread 扩展运算符在 ES6 中已经引入，不过 ES6 中只针对于数组，

在 ES9 中为对象提供了像数组一样的 rest 参数和扩展运算符

```
function connect({host, port, ...user}){
    console.log(host); //127.0.0.1
    console.log(port); //3306
    console.log(user); //{username: 'root', password: 'root', type: 'master'}
}

connect({
    host: '127.0.0.1',
    port: 3306,
    username: 'root',
    password: 'root',
    type: 'master'
});


//对象合并
const skillOne = {
    q: '天音波'
}

const skillTwo = {
    w: '金钟罩'
}

const skillThree = {
    e: '天雷破'
}
const skillFour = {
    r: '猛龙摆尾'
}

const mangseng = {...skillOne, ...skillTwo, ...skillThree, ...skillFour};

console.log(mangseng) //{q: '天音波', w: '金钟罩', e: '天雷破', r: '猛龙摆尾'}
```

### 2.正则表达式命名捕获组

ES9 允许命名捕获组使用符号『?<name>』,这样获取捕获结果可读性更强

```
let str = '<a href="http://www.baidu.com">百度</a>';
//分组命名
const reg = /<a href="(?<url>.*)">(?<text>.*)<\/a>/;

const result = reg.exec(str);

console.log(result.groups.url); //http://www.baidu.com

console.log(result.groups.text); //百度
```

### 3.正则表达式反向断言

ES9 支持反向断言，通过对匹配结果前面的内容进行判断，对匹配进行筛选。

“先行断言”指的是，`x`只有在`y`前面才匹配，必须写成`/x(?=y)/`。比如，只匹配百分号之前的数字，要写成`/\d+(?=%)/`。“先行否定断言”指的是，`x`只有不在`y`前面才匹配，必须写成`/x(?!y)/`。比如，只匹配不在百分号之前的数字，要写成`/\d+(?!%)/`。

```javascript
/\d+(?=%)/.exec('100% of US presidents have been male')  // ["100"]
/\d+(?!%)/.exec('that’s all 44 of them')                 // ["44"]
```

上面两个字符串，如果互换正则表达式，就不会得到相同结果。另外，还可以看到，“先行断言”括号之中的部分（`(?=%)`），是不计入返回结果的。

“后行断言”正好与“先行断言”相反，`x`只有在`y`后面才匹配，必须写成`/(?<=y)x/`。比如，只匹配美元符号之后的数字，要写成`/(?<=\$)\d+/`。“后行否定断言”则与“先行否定断言”相反，`x`只有不在`y`后面才匹配，必须写成`/(?<!y)x/`。比如，只匹配不在美元符号后面的数字，要写成`/(?<!\$)\d+/`。

```javascript
/(?<=\$)\d+/.exec('Benjamin Franklin is on the $100 bill')  // ["100"]
/(?<!\$)\d+/.exec('it’s is worth about €90')                // ["90"]
```

上面的例子中，“后行断言”的括号之中的部分（`(?<=\$)`），也是不计入返回结果。

### 4.正则表达式 dotAll 模式

正则表达式中，点（`.`）是一个特殊字符，代表任意的单个字符，但是有两个例外。一个是四个字节的 UTF-16 字符，这个可以用`u`修饰符解决；另一个是行终止符（line terminator character）。

所谓行终止符，就是该字符表示一行的终结。以下四个字符属于“行终止符”。

- U+000A 换行符（`\n`）
- U+000D 回车符（`\r`）
- U+2028 行分隔符（line separator）
- U+2029 段分隔符（paragraph separator）

```javascript
/foo.bar/.test('foo\nbar')
// false
```

上面代码中，因为`.`不匹配`\n`，所以正则表达式返回`false`。

但是，很多时候我们希望匹配的是任意单个字符，这时有一种变通的写法。

```javascript
/foo[^]bar/.test('foo\nbar')
// true
```

这种解决方案毕竟不太符合直觉，ES2018 [引入](https://github.com/tc39/proposal-regexp-dotall-flag)`s`修饰符，使得`.`可以匹配任意单个字符。

```javascript
/foo.bar/s.test('foo\nbar') // true
```

这被称为`dotAll`模式，即点（dot）代表一切字符。所以，正则表达式还引入了一个`dotAll`属性，返回一个布尔值，表示该正则表达式是否处在`dotAll`模式。

```javascript
const re = /foo.bar/s;
// 另一种写法
// const re = new RegExp('foo.bar', 's');

re.test('foo\nbar') // true
re.dotAll // true
re.flags // 's'
```

`/s`修饰符和多行修饰符`/m`不冲突，两者一起使用的情况下，`.`匹配所有字符，而`^`和`$`匹配每一行的行首和行尾。

## 六、ES10

### 1.Object.fromEntries

```
//二维数组
const result = Object.fromEntries([
    ['name','school'],
    ['xueke', 'Java,大数据,前端,云计算']
]);
console.log(result) //{name: 'school', xueke: 'Java,大数据,前端,云计算'}
```

```
//Object.entries ES8
const arr = Object.entries({
    name: "school"
})
console.log(arr); //[['name', 'school']]
```

```
//Map
const m = new Map();
m.set('name','school');
const result = Object.fromEntries(m);
console.log(result) //{name: 'school'}
```

### 2.trimStart 和 trimEnd

```
// trim
let str = '   iloveyou   ';

console.log(str); //   iloveyou
console.log(str.trimStart()); //iloveyou
console.log(str.trimEnd()); //   iloveyou
```

### 3.Array.prototype.flat 与 flatMap

```
//flat 平
//将多维数组转化为低位数组
// const arr = [1,2,3,4,[5,6]];
// const arr = [1,2,3,4,[5,6,[7,8,9]]];
//参数为深度 是一个数字
// console.log(arr.flat(2));  

//flatMap
const arr = [1,2,3,4];
const result = arr.flatMap(item => [item * 10]);
console.log(result); //[10, 20, 30, 40]
```

### 4.Symbol.prototype.description

```
let s = Symbol('wxy');

console.log(s.description); //wxy
```

## 七、ES11

### 1.String.prototype.matchAll

如果一个正则表达式在字符串里面有多个匹配，现在一般使用`g`修饰符或`y`修饰符，在循环里面逐一取出。

```javascript
var regex = /t(e)(st(\d?))/g;
var string = 'test1test2test3';

var matches = [];
var match;
while (match = regex.exec(string)) {
  matches.push(match);
}

matches
// [
//   ["test1", "e", "st1", "1", index: 0, input: "test1test2test3"],
//   ["test2", "e", "st2", "2", index: 5, input: "test1test2test3"],
//   ["test3", "e", "st3", "3", index: 10, input: "test1test2test3"]
// ]
```

[ES2020](https://github.com/tc39/proposal-string-matchall) 增加了`String.prototype.matchAll()`方法，可以一次性取出所有匹配。不过，它返回的是一个遍历器（Iterator），而不是数组。

```javascript
const string = 'test1test2test3';
const regex = /t(e)(st(\d?))/g;

for (const match of string.matchAll(regex)) {
  console.log(match);
}
// ["test1", "e", "st1", "1", index: 0, input: "test1test2test3"]
// ["test2", "e", "st2", "2", index: 5, input: "test1test2test3"]
// ["test3", "e", "st3", "3", index: 10, input: "test1test2test3"]
```

上面代码中，由于`string.matchAll(regex)`返回的是遍历器，所以可以用`for...of`循环取出。相对于返回数组，返回遍历器的好处在于，如果匹配结果是一个很大的数组，那么遍历器比较节省资源。

遍历器转为数组是非常简单的，使用`...`运算符和`Array.from()`方法就可以了。

```javascript
// 转为数组的方法一
[...string.matchAll(regex)]

// 转为数组的方法二
Array.from(string.matchAll(regex))
```

### 2.类的私有属性

```
class Person{
    //公有属性
    name;
    //私有属性
    #age;
    #weight;
    //构造方法
    constructor(name, age, weight){
        this.name = name;
        this.#age = age;
        this.#weight = weight;
    }

    intro(){
        console.log(this.name);
        console.log(this.#age);
        console.log(this.#weight);
    }
}

//实例化
const girl = new Person('晓红', 18, '45kg');

console.log(girl.name); //晓红
// console.log(girl.#age);//Uncaught SyntaxError: Private field '#age' must be declared in an enclosing class
// console.log(girl.#weight);

girl.intro();
```

### 3.Promise.allSettled

有时候，我们希望等到一组异步操作都结束了，不管每一个操作是成功还是失败，再进行下一步操作。但是，现有的 Promise 方法很难实现这个要求。

`Promise.all()`方法只适合所有异步操作都成功的情况，如果有一个操作失败，就无法满足要求。

```javascript
const urls = [url_1, url_2, url_3];
const requests = urls.map(x => fetch(x));

try {
  await Promise.all(requests);
  console.log('所有请求都成功。');
} catch {
  console.log('至少一个请求失败，其他请求可能还没结束。');
}
```

上面示例中，`Promise.all()`可以确定所有请求都成功了，但是只要有一个请求失败，它就会报错，而不管另外的请求是否结束。

为了解决这个问题，[ES2020](https://github.com/tc39/proposal-promise-allSettled) 引入了`Promise.allSettled()`方法，用来确定一组异步操作是否都结束了（不管成功或失败）。所以，它的名字叫做”Settled“，包含了”fulfilled“和”rejected“两种情况。

`Promise.allSettled()`方法接受一个数组作为参数，数组的每个成员都是一个 Promise 对象，并返回一个新的 Promise 对象。只有等到参数数组的所有 Promise 对象都发生状态变更（不管是`fulfilled`还是`rejected`），返回的 Promise 对象才会发生状态变更。

```javascript
const resolved = Promise.resolve(42);
const rejected = Promise.reject(-1);

const allSettledPromise = Promise.allSettled([resolved, rejected]);

allSettledPromise.then(function (results) {
  console.log(results);
});
// [
//    { status: 'fulfilled', value: 42 },
//    { status: 'rejected', reason: -1 }
// ]
```

### 4.可选链操作符

```
// ?.
function main(config){
    // const dbHost = config && config.db && config.db.host;
    const dbHost = config?.db?.host;

    console.log(dbHost); //192.168.1.100
}

main({
    db: {
        host:'192.168.1.100',
        username: 'root'
    },
    cache: {
        host: '192.168.1.200',
        username:'admin'
    }
})
```

### 5.动态 import 导入

```
//获取元素
const btn = document.getElementById('btn');

btn.onclick = function(){
    import('./hello.js').then(module => {
        module.hello();
    });
}
```

### 6.globalThis 对象

```
console.log(globalThis); //Window {window: Window, self: Window, document: document, name: '', location: Location, …}
```

### 7.BigInt

```
//大整形
let n = 521n;
console.log(n, typeof(n)); //521n 'bigint'
```

```
let n = 123;
console.log(BigInt(n)); //123n
console.log(BigInt(1.2)); //报错 Uncaught RangeError: The number 1.2 cannot be converted to a BigInt because it is not an integer
```

```
//大数值运算
let max = Number.MAX_SAFE_INTEGER;
console.log(max); //9007199254740991
console.log(max + 1); //9007199254740992
console.log(max + 2); //9007199254740992

console.log(BigInt(max)) //9007199254740991n
console.log(BigInt(max) + BigInt(1)) //9007199254740992n
console.log(BigInt(max) + BigInt(2)) //9007199254740993n
```