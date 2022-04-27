# ES6~ES11

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