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

#### 参数的默认值

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

### 7.rest 参数

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



### 8.spread 扩展运算符

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

### 9.Symbol

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

### 10.迭代器（遍历器）

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

### 11.生成器（Generator）

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