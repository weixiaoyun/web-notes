# JavaScript基础

## 一、JS的HelloWorld

### 1.alert

控制浏览器弹出一个警告框：

```
alert("哥，你真帅啊！！");
```

### 2.document.write

让计算机在页面中输出一个内容：

```
document.write("看我出不出来~~~");
```

### 3.console.log

向控制台输出一个内容：

```
console.log("你猜我在哪出来呢？");
```

### 4.prompt()

prompt()可以弹出一个提示框，该提示框中会带有一个文本框；用户可以在文本框中输入一段内容，（该函数需要一个字符串作为参数，该字符串将会作为提示框的提示文字）

用户输入的内容将会作为函数的返回值返回，可以定义一个变量来接收该内容

```
var score = prompt("请输入小明的期末成绩(0-100):");
```

### 5.console.time()

console.time("计时器的名字")可以用来开启一个计时器;它需要一个字符串作为参数，这个字符串将会作为计时器的标识:

```
console.time("test");
```

console.timeEnd()用来停止一个计时器，需要一个计时器的名字作为参数:

```
console.timeEnd("test");
```

输出这两行代码之间程序的执行时间

## 二、js编写的位置

### 1.外部js文件

可以将js代码编写到外部js文件中，然后通过script标签引入；写到外部文件中可以在不同的页面中同时引用，也可以利用到浏览器的缓存机制（推荐使用的方式）

<script type="text/javascript" src="js/script.js"></script>



script标签一旦用于引入外部文件了，就不能在编写代码了，即使编写了浏览器也会忽略；如果需要则可以在创建一个新的script标签用于编写内部代码。



外部js文件js/script.js

![外部js](../../Typora图片/Images/JavaScript基础/外部js.png)

### 2.script标签

可以将js代码编写到script标签：

```
<script type="text/javascript">
   alert("我是内部的JS代码");
</script>
```



### 3.HTML标签的属性中

可以将js代码编写到标签的onclick属性中，当我们点击按钮时，js代码才会执行：（虽然可以写在标签的属性中，但是他们属于结构与行为耦合，不方便维护，不推荐使用）

```
<button onclick="alert('讨厌，你点我干嘛~~');">点我一下</button>
```



可以将js代码写在超链接的href属性中，这样当点击超链接时，会执行js代码：

```
<a href="javascript:alert('让你点你就点！！');">你也点我一下</a>
```

## 三、基本语法

- JS中严格区分大小写

- JS中每一条语句以分号(;)结尾

  如果不写分号，浏览器会自动添加，但是会消耗一些系统资源，而且有些时候，浏览器会加错分号，所以在开发中分号必须写

- JS中会忽略多个空格和换行，所以我们可以利用空格和换行对代码进行格式化

### 1.注释

注释中的内容不会被执行，但是可以在源代码中查看

#### 多行注释

```
/*
   多行注释
   JS注释
   多行注释，注释中的内容不会被执行，但是可以在源代码中查看
      要养成良好的编写注释的习惯，也可以通过注释来对代码进行一些简单的调试
 */
```

#### 单行注释

```
//单行注释
//alert("hello");
```

### 2.字面量和变量

字面量，都是一些不可改变的值

- 比如 ：1 2 3 4 5 
- 字面量都可以直接使用，但是我们一般都不会直接使用字面量

变量，变量可以用来保存字面量，而且变量的值是可以任意改变的

- 变量更加方便我们使用，所以在开发中都是通过变量去保存一个字面量，
- 很少直接使用字面量，可以通过变量对字面量进行描述

```
//声明变量
//在js中使用var关键字来声明一个变量
var a;

//为变量赋值
a = 123;
a = 456;
a = 123124223423424;

//声明和赋值同时进行
var b = 789;
var c = 0;

var age = 80;

console.log(age);
```

### 3.标识符

- 在JS中所有的可以由我们自主命名的都可以称为是标识符

- 例如：变量名、函数名、属性名都属于标识符

- 命名一个标识符时需要遵守如下的规则：

   - 标识符中可以含有字母、数字、_、$

   - 标识符不能以数字开头

   - 标识符不能是ES中的关键字或保留字

   - 标识符一般都采用驼峰命名法

      首字母小写，每个单词的开头字母大写，其余字母小写
      helloWorld xxxYyyZzz

- JS底层保存标识符时实际上是采用的Unicode编码，
   所以理论上讲，所有的utf-8中含有的内容都可以作为标识符

```
//千万不要这么用
var 锄禾日当午 = 789;
console.log(锄禾日当午);
```

## 四、数据类型

数据类型指的就是字面量的类型，在JS中一共有六种数据类型：

- Undefined 未定义
- String 字符串
- Object 对象
- Number 数值
- Null 空值
- Boolean 布尔值     

其中String Number Boolean Null Undefined属于基本数据类型，而Object属于引用数据类型

### 1.String

- 在JS中字符串需要使用引号引起来
- 使用双引号或单引号都可以，但是不要混着用
- 引号不能嵌套，双引号不能放双引号，单引号不能放单引号

```
var str = 'hello';
```

在字符串中我们可以使用\作为转义字符，当表示一些特殊符号时可以使用\进行转义

- \" 表示 "
- \' 表示 '
- \n 表示换行
- \t 制表符
- \\ 表示\

```
str = "我说:\"今天\t天气真不错！\"";//我说:"今天  天气真不错！"
console.log(str);

str = "\\\\\\";
console.log(str);//\\\
```

### 2.Number

- 在JS中所有的数值都是Number类型，包括整数和浮点数（小数）

- JS中可以表示的数字的最大值

  - Number.MAX_VALUE = 1.7976931348623157e+308

  - Number.MIN_VALUE 大于0的最小值 = 5e-324

- 如果使用Number表示的数字超过了最大值，则会返回一个
  - Infinity 表示正无穷
  -  -Infinity 表示负无穷
  - 使用typeof检查Infinity也会返回number
- NaN 是一个特殊的数字，表示Not A Number；使用typeof检查一个NaN也会返回number

```
//数字123
var a = 123;
//字符串123
var b = "123";
```

可以使用一个运算符 typeof，来检查一个变量的类型

语法：typeof 变量

- 检查字符串时，会返回string
- 检查数值时，会返回number

```
a = -Number.MAX_VALUE * Number.MAX_VALUE;//-Infinity
console.log(typeof a); //number
a = "abc" * "bcd";//NaN
console.log(typeof a); //number
a = NaN;//NaN
console.log(typeof a); //number

a = Number.MIN_VALUE; //5e-324

console.log(a);
```

**注意**：在JS中整数的运算基本可以保证精确；如果使用JS进行浮点运算，可能得到一个不精确的结果，所以千万不要使用JS进行对精确度要求比较高的运算

```
var c = 0.1 + 0.2;//0.30000000000000004

console.log(c);
```

### 3.Boolean

Boolean 布尔值；布尔值只有两个，主要用来做逻辑判断

- true：表示真
- false：表示假

使用typeof检查一个布尔值时，会返回boolean

```
var bool = false;

console.log(typeof bool);//boolean
console.log(bool);//false
```

### 4.Null和Undefined

Null（空值）类型的值只有一个，就是null

- null这个值专门用来表示一个为空的对象
- 使用typeof检查一个null值时，会返回object

Undefined（未定义）类型的值只有一个，就undefind

- 当声明一个变量，但是并不给变量赋值时，它的值就是undefined
- 使用typeof检查一个undefined时也会返回undefined

```
var a = null;

var b = undefined;
console.log(typeof a);//object
console.log(typeof b);//undefined
```

### 5.强制类型转换

- 指将一个数据类型强制转换为其他的数据类型
- 类型转换主要指，将其他的数据类型，转换为
   String Number Boolean

#### 将其他的数据类型转换为String

   方式一：

- 调用被转换数据类型的toString()方法

- 该方法不会影响到原变量，它会将转换的结果返回

- 但是注意：null和undefined这两个值没有toString()方法，
  如果调用他们的方法，会报错
  
  对于Number调用toString()时可以在方法中传递一个整数作为参数,此时它将会把数字转换为指定的进制,如果不指定则默认转换为10进制:
  
  ```
  var a = 255;
  a = a.toString(2);
  
  console.log(a); //11111111
  console.log(typeof a); //string
  ```

 方式二：
   - 调用String()函数，并将被转换的数据作为参数传递给函数

   - 使用String()函数做强制类型转换时，

        对于Number和Boolean实际上就是调用的toString()方法

        但是对于null和undefined，就不会调用toString()方法。它会将 null 直接转换为 "null"；将 undefined 直接转换为 "undefined"

```
var a = 123;

//调用a的toString()方法
//调用xxx的yyy()方法，就是xxx.yyy()
a = a.toString(); //'123'

a = true;
a = a.toString(); //'true'


a = null;
//a = a.toString(); //报错

a = undefined;
//a = a.toString(); //报错
```

```
a = 123;

//调用String()函数，来将a转换为字符串
a = String(a); //123

a = null;
a = String(a);//null

a = undefined;
a = String(a);

console.log(typeof a); //string
console.log(a); //undefined
```

#### 将其他的数据类型转换为Number

- 转换方式一：使用Number()函数

  - 字符串 --> 数字
       1.如果是纯数字的字符串，则直接将其转换为数字
       2.如果字符串中有非数字的内容，则转换为NaN
       3.如果字符串是一个空串或者是一个全是空格的字符串，则转换为0

  - 布尔 --> 数字
    true 转成 1
    false 转成 0

  - null --> 数字   0
  
  
    - undefined --> 数字 NaN
  


- 转换方式二：

  这种方式专门用来对付字符串：

  - parseInt() 把一个字符串转换为一个整数，可以将一个字符串中的有效的整数内容去出来，然后转换为Number

  - parseFloat() 把一个字符串转换为一个浮点数，作用和parseInt()类似，不同的是它可以获得有效的小数
  - 如果对非String使用parseInt()或parseFloat()，它会先将其转换为String然后在操作

```
var a = "123";

//调用Number()函数来将a转换为Number类型
a = Number(a); //123

a = false;
a = Number(a); //0


a = null;
a = Number(a); //0


a = undefined;
a = Number(a); //NaN
```

```
a = "123567a567px";
//调用parseInt()函数将a转换为Number
/*
  parseInt()可以将一个字符串中的有效的整数内容去出来，
   然后转换为Number
 */
a = parseInt(a); //123567

/*
 * parseFloat()作用和parseInt()类似，不同的是它可以获得有效的小数
 */
a = "123.456.789px";
a = parseFloat(a);//123.456

/*
  如果对非String使用parseInt()或parseFloat()
   它会先将其转换为String然后在操作
 */
a = true;
a = parseInt(a); //NaN

a = 198.23;
a = parseInt(a);//198

console.log(typeof a); //number
```

#### 将其他的数据类型转换为Boolean

使用Boolean()函数
- 数字 ---> 布尔
  
   除了0和NaN，其余的都是true
   
- 字符串 ---> 布尔
  
   除了空串，其余的都是true
   
- null和undefined都会转换为false

- 对象也会转换为true

```
var a = 123; //true
a = -123; //true
a = 0; //false
a = Infinity; //true
a = NaN; //false
```

```
a = " ";

a = Boolean(a);//true

a = null; //false
a = Boolean(a);

a = undefined; //false
a = Boolean(a);

console.log(typeof a); //boolean
console.log(a);
```





### 6.其他进制的数字

在js中：

- 如果需要表示16进制的数字，则需要以0x开头
- 如果需要表示8进制的数字，则需要以0开头
- 如果要要表示2进制的数字，则需要以0b开头

但是不是所有的浏览器都支持

```
//十六进制
a = 0x10;
a = 0xff;
a = 0xCafe;

//八进制数字
a = 070;

//二进制数字
a = 0b10;

//向"070"这种字符串，有些浏览器会当成8进制解析，有些会当成10进制解析
a = "070";

//可以在parseInt()中传递一个第二个参数，来指定数字的进制
a = parseInt(a,10);

console.log(typeof a); //number
console.log(a); //70
```

## 五、运算符

运算符也叫操作符，通过运算符可以对一个或多个值进行运算,并获取运算结果

比如：typeof就是运算符，可以来获得一个值的类型，它会将该值的类型以字符串的形式返回：number string boolean undefined object

```
var a = 123;

var result = typeof a;

console.log(result) //number
console.log(typeof result); //string
```

### 1.算数运算符

- 当对非Number类型的值（String类型的+除外）进行运算时，会将这些值转换为Number然后在运算
- 任何值和NaN做运算都得NaN

#### +

- +可以对两个值进行加法运算，并将结果返回
- 如果对两个字符串进行加法运算，则会做拼串（会将两个字符串拼接为一个字符串，并返回）

- 任何的值和字符串做加法运算，都会先转换为字符串，然后再和字符串做拼串的操作，我们可以利用这一特点，来将一个任意的数据类型转换为String：

  我们只需要为任意的数据类型 + 一个 "" 即可将其转换为String，这是一种**隐式的类型转换**，由浏览器自动完成，实际上它也是调用String()函数

  ```
  result = a + 1; //124
  
  result = 456 + 789; //1245
  
  result = true + 1; //2
  
  result = true + false; //1
  
  result = 2 + null; //2
  
  result = 2 + NaN; //NaN
  
  result = "你好" + "大帅哥"; //你好大帅哥
  
  var str = "锄禾日当午，" +
          "汗滴禾下土，" +
          "谁知盘中餐，" +
          "粒粒皆辛苦";
  console.log(str) //锄禾日当午，汗滴禾下土，谁知盘中餐，粒粒皆辛苦
  
  result = 123 + "1"; //1231
  
  result = true + "hello"; //truehello
  ```

  ```
  var c = 123;
  
  c = c + ""; //'123'
  
  c = null;
  
  c = c + "";
  
  console.log(c) //'null'
  console.log(typeof c); //string
  console.log("c = "+c); //c = null
  ```

  ```
  result = 1 + 2 + "3"; //33
  
  result = "1" + 2 + 3; //123
  ```

#### -

可以对两个值进行减法运算，并将结果返回

#### *

可以对两个值进行乘法运算

#### / 

可以对两个值进行除法运算

任何值做-  *  /运算时都会自动转换为Number

我们可以利用这一特点做**隐式的类型转换**：可以通过为一个值 -0    *1    /1来将其转换为Number，原理和Number()函数一样，使用起来更加简单

```
result = 100 - 5; //95

result = 100 - true; //99

result = 100 - "1"; //99

result = 2 * 2; //4

result = 2 * "8"; //16

result = 2 * undefined; //NaN

result = 2 * null; //0

result = 4 / 2; //2

result = 3 / 2; //1.5
```

```
var d = "123";

d = d - 0;

console.log(typeof d); //number
console.log(d); //123

result = 9 % 5;

console.log("result = "+result); //result = 4
```



#### %

取模运算（取余数）

### 2.一元运算符

一元运算符，只需要一个操作数
   + 正号：正号不会对数字产生任何影响
   - 负号：负号可以对数字进行负号的取反

   - 对于非Number类型的值，

      它会将先转换为Number，然后在运算

      可以对一个其他的数据类型使用+,来将其转换为number

      它的原理和Number()函数一样

```
a = "18";

a = +a;

console.log("a = "+a); //a = 18
console.log(typeof a); //number

var result = 1 + +"2" + 3;

console.log("result = "+result); //result = 6
```

### 3.自增和自减

#### 自增 ++

- 通过自增可以使变量在自身的基础上增加1
- 对于一个变量自增以后，原变量的值会立即自增1
- 自增分成两种：后++(a++) 和 前++(++a)  
  无论是a++ 还是 ++a，都会立即使原变量的值自增1
  不同的是a++ 和 ++a的值不同
  a++的值等于原变量的值（自增前的值）
  ++a的值等于新值 （自增后的值）

#### 自减 --

   - 通过自减可以使变量在自身的基础上减1
   - 自减分成两种：后--(a--) 和 前--(--a)
      无论是a-- 还是 --a 都会立即使原变量的值自减1
      不同的是a-- 和 --a的值不同
      a-- 是变量的原值 （自减前的值）
      --a 是变量的新值 （自减以后的值）

```
var num = 10;

console.log(num--);//10
console.log(--num);//8

console.log("num = "+num);//num = 8
```

```
var a = 1;

// 使a自增1
a++;
++a;

console.log(a++); //3

console.log("++a = " + ++a); //++a = 5
console.log("a++ = " + a++); //a++ = 5

console.log("a = "+a); //a = 6
```

```
var d = 20;

// 20 + 22 + 22
var result = d++ + ++d + d ;
console.log('result = ' + result)//result = 64
```

```
d = 20
d = d++;

var e = d++;
d = e;

console.log("d = "+d); //d = 20
```

### 4.逻辑运算符

JS中为我们提供了三种逻辑运算符

#### ! 非

   - !可以用来对一个值进行非运算
   - 所谓非运算就是值对一个布尔值进行取反操作，
      true变false，false变true
   - 如果对一个值进行两次取反，它不会变化
   - 如果对非布尔值进行元素，则会将其转换为布尔值，然后再取反
      所以我们可以利用该特点，来将一个其他的数据类型转换为布尔值
      可以为一个任意数据类型取两次反，来将其转换为布尔值，
      原理和Boolean()函数一样

```
var a = false;

//对a进行非运算
a = !a; //a = true


var b = 10;
b = !!b;

console.log("b = "+b); //b = true
console.log(typeof b); //boolean
```

#### && 与

   - &&可以对符号两侧的值进行与运算并返回结果
   - 运算规则
      - 两个值中只要有一个值为false就返回false，
         只有两个值都为true时，才会返回true
      - JS中的“与”属于短路的与，
         如果第一个值为false，则不会看第二个值

```
var result = true && true;  //result = true

//只要有一个false，就返回false
result = true && false;  //result = false

result = false && true;  //result = false

result = false && false; //result = false
```

```
true && alert("看我出不出来！！");

//第一个值为false，不会检查第二个值
false && alert("看我出不出来！！");
```



#### || 或

   - ||可以对符号两侧的值进行或运算并返回结果
   - 运算规则：
      - 两个值中只要有一个true，就返回true
         如果两个值都为false，才返回false
      - JS中的“或”属于短路的或
            如果第一个值为true，则不会检查第二个值

```
//两个都是false，则返回false
result = false || false;  //result = false

//只有有一个true，就返回true
result = true || false;  //result = true

result = false || true ;  //result = true

result = true || true ; //result = true
```

```
//第一个值为false，则会检查第二个值
false || alert("123");

//第一个值为true，则不再检查第二个值
true || alert("123");
```

#### && || 非布尔值的情况

   - 对于非布尔值进行与或运算时，
      会先将其转换为布尔值，然后再运算，并且返回原值
   - 与运算：
      - 如果第一个值为true，则必然返回第二个值
      - 如果第一个值为false，则直接返回第一个值

   - 或运算
      - 如果第一个值为true，则直接返回第一个值
      - 如果第一个值为false，则返回第二个值

```
//与运算：如果两个值都为true，则返回后边的
var result = 5 && 6; //result = 6


//与运算：如果两个值中有false，则返回靠前的false
//false && true
result = 0 && 2; //result = 0

result = 2 && 0; //result = 0

//false &&　false
result = NaN && 0; //result = NaN

result = 0 && NaN; //result = 0
```

```
//如果第一个值为true，则直接返回第一个值
result = 2 || 1; //result = 2

result = 2 || NaN; //result = 2

result = 2 || 0; //result = 2


//如果第一个值为false，则直接返回第二个值
result = NaN || 1; //result = 1

result = NaN || 0; //result = 0

result = "" || "hello"; //result = hello

result = -1 || "你好"; //result = -1
```

### 5.赋值运算符

- =：可以将符号右侧的值赋值给符号左侧的变量
- +=：a += 5 等价于 a = a + 5
- -=：a -= 5 等价于 a = a - 5
- *=：a *= 5 等价于 a = a * 5
- /=：a /= 5 等价于 a = a / 5
- %=：a %= 5 等价于 a = a % 5

```
var a = 10;

a = a + 5; //15

a += 5; //20

a -= 5;  //15

a *= 5; //75

a = a%3; //0

a %= 3; //0
```

### 6.关系运算符

通过关系运算符可以比较两个值之间的大小关系，如果关系成立它会返回true，如果关系不成立则返回false

- ''>' 大于号

  - 判断符号左侧的值是否大于右侧的值
  - 如果关系成立，返回true，如果关系不成立则返回false

- '>=' 大于等于

  判断符号左侧的值是否大于或等于右侧的值

- '<' 小于号

- '<=' 小于等于

**非数值的情况:**

   - 对于非数值进行比较时，会将其转换为数字然后在比较
   - 如果符号两侧的值都是字符串时，不会将其转换为数字进行比较。而会分别比较字符串中字符的Unicode编码 (如果比较的两个字符串型的数字，可能会得到不可预期的结果。注意：在比较两个字符串型的数字时，一定一定一定要转型)
   - 任何值和NaN做任何比较都是false

```
var result = 5 > 10;//false

result = 5 > 4; //true

result = 5 > 5; //false

result = 5 >= 5; //true

result = 5 >= 4; //true

result = 5 < 4; //false

result = 4 <= 4; //true
```

```
console.log(1 > true); //false
console.log(1 >= true); //true
console.log(1 > "0"); //true
console.log(10 > null); //true
```

```
//任何值和NaN做任何比较都是false
console.log(10 <= "hello"); //false
console.log(true > false); //true
```

```
//比较两个字符串时，比较的是字符串的字符编码
console.log("1" < "5"); //true
console.log("11" < "5"); //true


console.log("a" < "b");//true
//比较字符编码时是一位一位进行比较
//如果两位一样，则比较下一位，所以借用它来对英文进行排序
console.log("abc" < "bcd");//true
//比较中文时没有意义
console.log("戒" > "我"); //true
```

```
//如果比较的两个字符串型的数字，可能会得到不可预期的结果
//注意：在比较两个字符串型的数字时，一定一定一定要转型
console.log("11123123123123123123" < +"5"); //false
```

#### 编码

在字符串中使用转义字符输入Unicode编码：

```
  //    \u四位编码
console.log("\u2620"); //☠
```

在网页中使用Unicode编码：&#编码; 这里的编码需要的是10进制

```
<h1 style="font-size: 200px;">&#9760;</h1>
<h1 style="font-size: 200px;">&#9856;</h1>
```

### 7.相等运算符

#### 相等运算符 ==

用来比较两个值是否相等，如果相等会返回true，否则返回false

- 使用 == 来做相等运算
- 当使用==来比较两个值时，如果值的类型不同，则会自动进行类型转换，将其转换为相同的类型，然后再比较

#### 不相等运算符 !=

不相等用来判断两个值是否不相等，如果不相等返回true，否则返回false

   - 使用 != 来做不相等运算
   - 不相等也会对变量进行自动的类型转换，如果转换后相等它也会返回false

#### 全等 ===

用来判断两个值是否全等，它和相等类似，不同的是它不会做自动的类型转换
如果两个值的类型不同，直接返回false

#### 不全等 !==

用来判断两个值是否不全等，和不等类似，不同的是它不会做自动的类型转换
如果两个值的类型不同，直接返回true

```
console.log(1 == 1); //true

var a = 10;

console.log(a == 4); //false

console.log("1" == 1); //true

console.log(true == "1"); //true

console.log(null == 0); //false

/*
 * undefined 衍生自 null
 *     所以这两个值做相等判断时，会返回true
 */
console.log(undefined == null); //true

/*
 * NaN不和任何值相等，包括他本身
 */
console.log(NaN == NaN); //false

var b = NaN;

//判断b的值是否是NaN
console.log(b == NaN); //false
/*
 * 可以通过isNaN()函数来判断一个值是否是NaN
 *     如果该值是NaN则返回true，否则返回false
 */
console.log(isNaN(b)); //true

console.log(10 != 5); //true
console.log(10 != 10); //false
console.log("abcd" != "abcd"); //false
console.log("1" != 1);//false

console.log("123" === 123);//false
console.log(null === undefined);//false

console.log(1 !== "1"); //true
```

### 8.条件运算符

条件运算符也叫三元运算符

- 语法：条件表达式?语句1:语句2;

   - 执行的流程：

      - 条件运算符在执行时，首先对条件表达式进行求值，

           如果该值为true，则执行语句1，并返回执行结果

           如果该值为false，则执行语句2，并返回执行结果

      - 如果条件的表达式的求值结果是一个非布尔值，会将其转换为布尔值然后在运算

```
//获取a和b中的最大值
//var max = a > b ? a : b;
//获取a b c 中的大值
//max = max > c ? max : c;
```

```
"hello"?alert("语句1"):alert("语句2");
```

![条件运算符](https://raw.githubusercontent.com/weixiaoyun/Images/JavaScript/%E6%9D%A1%E4%BB%B6%E8%BF%90%E7%AE%97%E7%AC%A6.png)

### 9.‘，’运算符

使用,可以分割多个语句，一般可以在声明多个变量时使用

```
//使用,运算符同时声明多个变量
var a , b , c;

//可以同时声明多个变量并赋值
var a=1 , b=2 , c=3;
```

### 10.运算符的优先级

就和数学中一样，在JS中运算符也有优先级，比如：先乘除 后加减

下表按从最高到最低的优先级列出JavaScript运算符。具有相同优先级的运算符按从左至右的顺序求值：

| 运算符                             | 描述                                         |
| ---------------------------------- | -------------------------------------------- |
| . [] ()                            | 字段访问、数组下标、函数调用以及表达式分组   |
| ++ -- - ~ ! delete new typeof void | 一元运算符、返回数据类型、对象创建、未定义值 |
| * / %                              | 乘法、除法、取模                             |
| + - +                              | 加法、减法、字符串连接                       |
| << >> >>>                          | 移位                                         |
| < <= > >= instanceof               | 小于、小于等于、大于、大于等于、instanceof   |
| == != === !==                      | 等于、不等于、严格相等、非严格相等           |
| &                                  | 按位与                                       |
| ^                                  | 按位异或                                     |
| \|                                 | 按位或                                       |
| &&                                 | 逻辑与                                       |
| \|\|                               | 逻辑或                                       |
| ?:                                 | 条件                                         |
| = oP=                              | 赋值、运算赋值                               |
| ,                                  | 多重求值                                     |

也可以使用()来改变优先级

```
var result = 1 || 2 && 3; //与的优先级高，返回1

console.log("result = "+result); //result = 1
```

## 六、代码块

- 我们的程序是由一条一条语句构成的，语句是按照自上向下的顺序一条一条执行的，在JS中可以使用{}来为语句进行分组
- 同一个{}中的语句我们称为是一组语句，它们要么都执行，要么都不执行，
- 一个{}中的语句我们也称为叫一个代码块，在代码块的后边就不用再编写;了
- JS中的代码块，只具有分组的的作用，没有其他的用途，代码块内容的内容，在外部是完全可见的

## 七、流程控制语句

   - JS中的程序是从上到下一行一行执行的
   - 通过流程控制语句可以控制程序执行流程，使程序可以根据一定的条件来选择执行
 - 语句的分类：
      1.条件判断语句
      2.条件分支语句
      3.循环语句

### 1.条件判断语句

使用条件判断语句可以在执行某个语句之前进行判断，如果条件成立才会执行语句，条件不成立则语句不执行。

条件判断语句也叫if语句

**语法一**：

```
if(条件表达式){
   语句...
}
```

- if语句在执行时，会先对条件表达式进行求值判断。如果条件表达式的值为true，则执行if后的语句；如果条件表达式的值为false，则不会执行if后的语句。
- if语句只能控制紧随其后的那个语句,如果希望if语句可以控制多条语句，可以将这些语句统一放到代码块中。
- if语句后的代码块不是必须的，但是在开发中尽量写上代码块，即使if后只有一条语句。

```
var a = 25;

if(a > 10 && a <= 20){
   alert("a大于10，并且 a小于等于20");
}
```

**语法二**:

```
if(条件表达式){
   语句...
}else{
   语句...
}
```

if...else...语句。当该语句执行时，会先对if后的条件表达式进行求值判断，

- 如果该值为true，则执行if后的语句
- 如果该值为false，则执行else后的语句

**语法三**：

```
if(条件表达式){
   语句...
}else if(条件表达式){
   语句...
}else if(条件表达式){
   语句...
}else{
   语句...
}
```

if...else if...else

- 当该语句执行时，会从上到下依次对条件表达式进行求值判断
- 如果值为true，则执行当前语句。
- 如果值为false，则继续向下判断。
- 如果所有的条件都不满足，则执行最后一个else后的语句
- 该语句中，只会有一个代码块被执行，一旦代码块执行了，则直接结束语句

```
var age = 50;

if(age >= 60){
   alert("你已经退休了~~");
}else{
   alert("你还没退休~~~");
}

age = 200;

if(age > 100){
   alert("活着挺没意思的~~");
}else if(age > 80){
   alert("你也老大不小的了~~");
}else if(age > 60){
   alert("你也退休了~~");
}else if(age > 30){
   alert("你已经中年了~~");
}else if(age > 17){
   alert("你已经成年了");
}else{
   alert("你还是个小孩子~~");
}

age = 90;

if(age > 17 && age <= 30){
   alert("你已经成年了");
}else if(age > 30 && age <= 60){
   alert("你已经中年了");
}else if(age > 60 && age <= 80){
   alert("你已经退休了");
}else{
   alert("你岁数挺大的了~~");
}
```

### 2.条件分支语句

条件分支语句也叫switch语句

语法：

```
switch(条件表达式){
   case 表达式:
      语句...
      break;
   case 表达式:
      语句...
      break;
   default:
      语句...
      break;
}
```

switch...case..语句执行流程：

在执行时会依次将case后的表达式的值和switch后的条件表达式的值进行全等比较，

- 如果比较结果为true，则从当前case处开始执行代码。

  当前case后的所有的代码都会执行，我们可以在case的后边跟着一个break关键字，这样可以确保只会执行当前case后的语句，而不会执行其他的case

- 如果比较结果为false，则继续向下比较

- 如果所有的比较结果都为false，则只执行default后的语句

switch语句和if语句的功能实际上有重复的，使用switch可以实现if的功能，同样使用if也可以实现switch的功能，所以我们使用时，可以根据自己的习惯选择。

```
/*if(num == 1){
   console.log("壹");
}else if(num == 2){
   console.log("贰");
}else if(num == 3){
   console.log("叁");
}*/

num = "hello";

switch(num){
   case 1:
      console.log("壹");
      //使用break可以来退出switch语句
      break;
   case 2:
      console.log("贰");
      break;
   case 3:
      console.log("叁");
      break;
   default:
      console.log("非法数字~~");
      break;
}
```

### 3.循环语句

通过循环语句可以反复的执行一段代码多次：

#### while循环

- 语法：

   ```
   while(条件表达式){
      语句...
   }
   ```

- while语句在执行时，先对条件表达式进行求值判断：
  
   - 如果值为true，则执行循环体；循环体执行完毕以后，继续对表达式进行判断；如果为true，则继续执行循环体，以此类推
   - 如果值为false，则终止循环

#### do...while循环

- 语法：
  
   ```
   do{
      语句...
   }while(条件表达式)
   ```
   
- 执行流程：
  
   - do...while语句在执行时，会先执行循环体，
      循环体执行完毕以后，在对while后的条件表达式进行判断，
      如果结果为true，则继续执行循环体，执行完毕继续判断以此类推
      如果结果为false，则终止循环
   
   - 实际上这两个语句功能类似，不同的是while是先判断后执行，而do...while会先执行后判断，
   - do...while可以保证循环体至少执行一次，而while不能

**死循环**

向这种将条件表达式写死为true的循环，叫做死循环；该循环不会停止，除非浏览器关闭，死循环在开发中慎用；可以使用break，来终止循环

```
while(true){
   alert(n++);

   //判断n是否是10
   if(n == 10){
      //退出循环
      break;
   }

}
```

创建一个循环，往往需要三个步骤：

1. 创初始化一个变量
2. 在循环中设置一个条件表达式
3. 定义一个更新表达式，每次更新初始化变量

```
//1.创初始化一个变量
var i = 11;



//2.在循环中设置一个条件表达式
while(i <= 10){
   //3.定义一个更新表达式，每次更新初始化变量
   document.write(i++ +"<br />")

}

do{
   document.write(i++ +"<br />");
}while(i <= 10);
```

#### for循环

for语句，也是一个循环语句，也称为for循环；在for循环中，为我们提供了专门的位置用来放三个表达式：

1. 初始化表达式
2. 条件表达式
3. 更新表达式

 for循环的语法：

```
for(①初始化表达式;②条件表达式;④更新表达式){
③语句...
}
```

for循环的执行流程：

- ①执行初始化表达式，初始化变量（初始化表达式只会执行一次）
- ②执行条件表达式，判断是否执行循环。
  - 如果为true，则执行循环③
  - 如果为false，终止循环
- ④执行更新表达式，更新表达式执行完毕继续重复②

```
for(var i = 0 ; i < 10 ; i++ ){
   alert(i);
}
```

```
for(var i = 0 ; i < 10 ; i++ ){
   console.log(i); //0,1,2,3,4,5,6,7,8,9
}
```

for循环中的三个部分都可以省略，也可以写在外部：

```
var i = 0;

for(; i < 10 ;){
   alert(i++ );
}
```

如果在for循环中不写任何的表达式，只写两个;此时循环是一个死循环，会一直执行下去：

```
for(;;){
   alert("hello");
}
```

#### break和continue

break关键字可以用来退出switch或循环语句，break关键字，会立即终止离他最近的那个循环语句

在if语句中使用break和continue会对离他最近的循环生效：

```
for(var i=0 ; i<5 ; i++){
   console.log(i);

   if(i == 2){
      break;
   }

}//0
//1
//2
```

可以为循环语句创建一个label，来标识当前的循环：

*label:循环语句*

使用break语句时，可以在break后跟着一个label，这样break将会结束指定的循环，而不是最近的：

```
outer:
for(var i=0 ; i<5 ; i++){
   console.log("@外层循环"+i)
   for(var j=0 ; j<5; j++){
      break outer;
      console.log("内层循环:"+j);
   }
}//@外层循环0
```

continue关键字可以用来跳过当次循环，同样continue也是默认只会对离他最近的循环循环起作用：

```
for(var i=0 ; i<5 ; i++){

   if(i==2){
      continue;
   }

   console.log(i);
}//0
//1
//3
//4
```

## 八、对象

JS中数据类型：
- String 字符串

- Number 数值

- Boolean 布尔值

- Null 空值

- Undefined 未定义

   以上这五种类型属于基本数据类型，以后我们看到的值
   只要不是上边的5种，全都是对象

- Object 对象

基本数据类型都是单一的值"hello" 123 true，值和值之间没有任何的联系。

在JS中来表示一个人的信息（name gender age）：

```
var name = "孙悟空";
var gender = "男";
var age = 18;
```

如果使用基本数据类型的数据，我们所创建的变量都是独立，不能成为一个整体。

对象属于一种复合的数据类型，在对象中可以保存多个不同数据类型的属性。

**对象的分类**：

1. 内建对象：由ES标准中定义的对象，在任何的ES的实现中都可以使用
   比如：Math String Number Boolean Function Object....
2. 宿主对象：由JS的运行环境提供的对象，目前来讲主要指由浏览器提供的对象
   比如 BOM DOM
3. 自定义对象：由开发人员自己创建的对象

### 1.创建对象

使用new关键字调用的函数，是构造函数constructor；构造函数是专门用来创建对象的函数；使用typeof检查一个对象时，会返回object：

```
var obj = new Object();
```

在对象中保存的值称为属性，**向对象添加属性**：

*语法：对象.属性名 = 属性值;*

```
//向obj中添加一个name属性
obj.name = "孙悟空";
//向obj中添加一个gender属性
obj.gender = "男";
//向obj中添加一个age属性
obj.age = 18;
```

**读取对象中的属性**：

*语法：对象.属性名*

如果读取对象中没有的属性，不会报错而是会返回undefined

```
console.log(obj.gender); //男
console.log(obj.hello);  //undefined
```

**修改对象的属性值**：

*语法：对象.属性名 = 新值*

```
obj.name = "tom";
```

**删除对象的属性**：

*语法：delete 对象.属性名*

```
delete obj.name;
```

### 2.属性名和属性值

#### 属性名

   - 对象的属性名不强制要求遵守标识符的规范
   - 但是我们使用是还是尽量按照标识符的规范去做

```
obj.name = "孙悟空";
```

如果要使用特殊的属性名，不能采用.的方式来操作，需要使用另一种方式：

*语法：对象["属性名"] = 属性值*

读取时也需要采用这种方式。

使用[]这种形式去操作属性，更加的灵活，在[]中可以直接传递一个变量，这样变量值是多少就会读取那个属性

```
obj["123"] = 789;
obj["nihao"] = "你好";
var n = "nihao";
console.log(obj["123"]);  //789
```

#### 属性值

JS对象的属性值，可以是任意的数据类型，甚至也可以是一个对象

```
var obj2 = new Object();
obj2.name = "猪八戒";

//将obj2设置为obj的属性
obj.test = obj2;

console.log(obj.test.name); //猪八戒
```

#### in 运算符

通过该运算符可以检查一个对象中是否含有指定的属性：
如果有则返回true，没有则返回false

语法：*"属性名" in 对象*

```
console.log("name" in obj); //true
```

### 3.基本和引用数据类型

基本数据类型：

*String Number Boolean Null Undefined*

引用数据类型：

*Object*



JS中的变量都是保存到栈内存中的

- 基本数据类型的值直接在栈内存中存储，
- 值与值之间是独立存在，修改一个变量不会影响其他的变量

对象是保存到堆内存中的，每创建一个新的对象，就会在堆内存中开辟出一个新的空间

- 变量保存的是对象的内存地址（对象的引用），如果两个变量保存的是同一个对象引用，
- 当一个通过一个变量修改属性时，另一个也会受到影响



当比较两个基本数据类型的值时，就是比较值。而比较两个引用数据类型时，它是比较的对象的内存地址，如果两个对象是一摸一样的，但是地址不同，它也会返回false



```
var a = 123;
var b = a;
a++;

console.log("a = "+a); //a = 124
console.log("b = "+b); //b = 123
```

![栈内存](https://raw.githubusercontent.com/weixiaoyun/Images/JavaScript/%E6%A0%88%E5%86%85%E5%AD%98.png)



```
var obj = new Object();
obj.name = "孙悟空";

var obj2 = obj;

//修改obj的name属性
obj.name = "猪八戒";



console.log(obj.name); //猪八戒
console.log(obj2.name); //猪八戒
```

![堆内存1](https://raw.githubusercontent.com/weixiaoyun/Images/JavaScript/%E5%A0%86%E5%86%85%E5%AD%981.png)



```
obj2 = null;

console.log(obj); //{name: '猪八戒'}
console.log(obj2); //null
```

![堆内存2](https://raw.githubusercontent.com/weixiaoyun/Images/JavaScript/%E5%A0%86%E5%86%85%E5%AD%982.png)



```
var obj3 = new Object();
var obj4 = new Object();
obj3.name = "沙和尚";
obj4.name = "沙和尚";

console.log(obj3 == obj4); //false
```

![堆内存3](https://raw.githubusercontent.com/weixiaoyun/Images/JavaScript/%E5%A0%86%E5%86%85%E5%AD%983.png)

### 4.对象字面量

使用对象字面量来创建一个对象：

```
var obj = {};

console.log(typeof obj); //object

obj.name = "孙悟空";

console.log(obj.name);  //孙悟空
```

使用对象字面量，可以在创建对象时，直接指定对象中的属性

*语法：{属性名:属性值,属性名:属性值....}*

- 对象字面量的属性名可以加引号也可以不加，建议不加,
- 如果要使用一些特殊的名字，则必须加引号

属性名和属性值是一组一组的名值对结构，

- 名和值之间使用:连接，多个名值对之间使用,隔开
- 如果一个属性之后没有其他的属性了，就不要写,

```
var obj2 = {

   name:"猪八戒",
   age:13,
   gender:"男",
   test:{name:"沙僧"}

};
```

## 九、函数

函数 function
   - 函数也是一个对象
   - 函数中可以封装一些功能（代码），在需要时可以执行这些功能（代码）
   - 函数中可以保存一些代码在需要的时候调用
   - 使用typeof检查一个函数对象时，会返回function

### 1.创建函数

#### 创建函数对象

我们在实际开发中很少使用构造函数来创建一个函数对象，可以将要封装的代码以字符串的形式传递给构造函数

```
// 创建一个函数对象
var fun = new Function("console.log('Hello 这是我的第一个函数');");
```

封装到函数中的代码不会立即执行，函数中的代码会在函数调用的时候执行

调用：*函数对象()*

当调用函数时，函数中封装的代码会按照顺序执行

```
fun();
```

#### 函数声明

使用 函数声明 来创建一个函数：

```
function 函数名([形参1,形参2...形参N]){
   语句...
}
```

```
function fun2(){
   console.log("这是我的第二个函数~~~");
   alert("哈哈哈哈哈");
   document.write("~~~~(>_<)~~~~");
}
```

调用：

```
fun2();
```

#### 函数表达式

使用 函数表达式 来创建一个函数：

```
var 函数名  = function([形参1,形参2...形参N]){
    语句....
 }
```

```
var fun3 = function(){
   console.log("我是匿名函数中封装的代码");
};
```

调用：

```
fun3();
```

### 2.函数的参数

- 可以在函数的()中来指定一个或多个形参（形式参数）
- 多个形参之间使用,隔开，声明形参就相当于在函数内部声明了对应的变量，但是并不赋值

```
//定义一个用来求两个数和的函数
function sum(a,b){
   console.log("a = "+a);
   console.log("b = "+b);
   console.log(a+b);
}
```

在调用函数时，可以在()中指定实参（实际参数），实参将会赋值给函数中对应的形参

```
sum(1,2);  //3
sum(123,456);  //579
```

- 调用函数时解析器不会检查实参的类型,所以要注意，是否有可能会接收到非法的参数，如果有可能则需要对参数进行类型的检查
- 函数的实参可以是任意的数据类型

```
sum(123,"hello"); //123hello
sum(true , false); //1
```

- 调用函数时，解析器也不会检查实参的数量，多余实参不会被赋值
- 如果实参的数量少于形参的数量，则没有对应实参的形参将是undefined

```
//a = 123
//b = 456
sum(123,456,"hello",true,null); //579
//a = 123
//b = undefined
sum(123); //NaN
```

### 3.函数的返回值

可以使用 return 来设置函数的返回值
语法：*return 值*

return后的值将会会作为函数的执行结果返回；可以定义一个变量，来接收该结果

在函数中return后的语句都不会执行

- 如果return语句后不跟任何值就相当于返回一个undefined，
- 如果函数中不写return，则也会返回undefined

- return后可以跟任意类型的值；可以是一个对象，也可以是一个函数

```
function sum(a , b , c){

   var d = a + b + c;

   return d;

}
```

```
function fun2(){

   //返回一个对象
   return {name:"沙和尚"};
}

var a = fun2();

console.log("a = "+a); //a = [object Object]

function fun3(){
   //在函数内部再声明一个函数
   function fun4(){
      return '我是fun4'
   }

   //将fun4函数对象作为返回值返回
   return fun4;
}

a = fun3();
console.log(a);/*ƒ fun4(){
   return '我是fun4'
}*/
console.log(a());  //我是fun4
console.log(fun3()());  //我是fun4
```

调用函数

```
var result = sum(4,7,8);

console.log("result = "+result); //result = 19
```

- 函数名()：调用函数，相当于使用的函数的返回值

- 函数名：函数对象，相当于直接使用函数对象

break，continue，return的区别：

- 使用break可以退出当前的循环
- continue用于跳过当次循环
- 使用return可以结束整个函数

### 4.立即执行函数

函数定义完，立即被调用，这种函数叫做立即执行函数（立即执行函数往往只会执行一次）

```
(function(a,b){
   console.log("a = "+a);
   console.log("b = "+b);
})(123,456); /*a = 123
          b = 456*/
```

### 5.方法

函数也可以作为对象的属性，如果一个函数作为一个对象的属性保存，那么我们称这个函数是这个对象的方法。
调用这个函数就说调用对象的方法（method）

（但是它只是名称上的区别没有其他的区别）

```
var obj = new Object();

//向对象中添加属性
obj.name = "孙悟空";
obj.age = 18;

//对象的属性值可以是任何的数据类型，也可以是个函数
obj.sayName = function(){
   console.log(obj.name);
};
```

```
//调方法
obj.sayName();
```

### 6.枚举对象中的属性

使用for ... in 语句

语法：

```
for(var 变量 in 对象){

}
```

for...in语句 对象中有几个属性，循环体就会执行几次，每次执行时，会将对象中的一个属性的名字赋值给变量

```
var obj = {
         name:"孙悟空",
         age:18,
         gender:"男",
         address:"花果山"
       };

//枚举对象中的属性

for(var n in obj){
   console.log("属性名:"+n);

   console.log("属性值:"+obj[n]);
}
/*属性名:name
属性值:孙悟空
属性名:age
属性值:18
属性名:gender
属性值:男
属性名:address
属性值:花果山*/
```

### 7.作用域

作用域指一个变量的作用的范围，在JS中一共有两种作用域：

#### 全局作用域

   - 直接编写在script标签中的JS代码，都在全局作用域
   - 全局作用域在页面打开时创建，在页面关闭时销毁
   - 在全局作用域中有一个全局对象window，
      它代表的是一个浏览器的窗口，它由浏览器创建我们可以直接使用
   - 在全局作用域中：
      创建的变量都会作为window对象的属性保存
      创建的函数都会作为window对象的方法保存
   - 全局作用域中的变量都是全局变量，
      在页面的任意的部分都可以访问的到

```
var a = 10;
var b = 20;
var c = "hello";

console.log(window.c); //hello

function fun(){
   console.log("我是fun函数");
}

window.fun(); //我是fun函数
```

变量的声明提前
   - 使用var关键字声明的变量，会在所有的代码执行之前被声明（但是不会赋值），
      但是如果声明变量时不使用var关键字，则变量不会被声明提前

函数的声明提前
   - 使用函数声明形式创建的函数 function 函数(){}
      它会在所有的代码执行之前就被创建，所以我们可以在函数声明前来调用函数
   - 使用函数表达式创建的函数，不会被声明提前，所以不能在声明前调用

```
console.log("a = "+a); //a = undefined

var a = 123;
```

```
fun();//我是一个fun函数

//函数声明，会被提前创建
function fun(){
   console.log("我是一个fun函数");
}

fun2();//Uncaught TypeError: fun2 is not a function

//函数表达式，不会被提前创建
var fun2 = function(){
   console.log("我是fun2函数");
};
```

#### 函数作用域

- 调用函数时创建函数作用域，函数执行完毕以后，函数作用域销毁
- 每调用一次函数就会创建一个新的函数作用域，他们之间是互相独立的
- 在函数作用域中可以访问到全局作用域的变量
   在全局作用域中无法访问到函数作用域的变量
- 当在函数作用域操作一个变量时，它会先在自身作用域中寻找，如果有就直接使用
   如果没有则向上一级作用域中寻找，直到找到全局作用域，
   如果全局作用域中依然没有找到，则会报错ReferenceError
- 在函数中要访问全局变量可以使用window对象

```
var a = 10;

function fun(){

   var a = "我是fun函数中的变量a";
   var b = 20;

   function fun2(){
      console.log("a = "+a);  //a = 我是fun函数中的变量a
      console.log("a = "+window.a);  //a = 10
   }

   fun2();

}

fun();
console.log("b = "+b);  //Uncaught ReferenceError: b is not defined
```

在函数作用域也有声明提前的特性：

- 使用var关键字声明的变量，会在函数中所有的代码执行之前被声明
- 函数声明也会在函数中所有的代码执行之前执行
- 在函数中，不使用var声明的变量都会成为全局变量
- 定义形参就相当于在函数作用域中声明了变量

```
function fun3(){

   fun4();  //I'm fun4

   console.log(a); //undefined

   var a = 35;

   function fun4(){
      console.log("I'm fun4");
   }

}

fun3();
```

```
var c = 33;

function fun5(){
   console.log("c = "+c); //c = undefined

   var c = 10;
}

fun5();
```

该处由于没有使用var，那么也不会提前声明，console处的c需要到上一级作用域寻找，所以输出33

```
var c = 33;

function fun5(){
   console.log("c = "+c); //c = 33

   c = 10;
}
```

在函数中，不使用var声明的变量都会成为全局变量：

```
var c = 33;
function fun5(){
   console.log("c = "+c); //c = 33
   c = 10;
}
console.log("c = "+c) //c = 33
fun5();
console.log("c = "+c) //c = 10
```

```
function fun5(){
   //d没有使用var关键字，则会设置为全局变量
   d = 100;
}
fun5();
//在全局输出d
console.log("d = "+d); //d = 100
```

定义形参就相当于在函数作用域中声明了变量：

```
var e = 23;

function fun6(){
   alert(e);  //23
}

fun6();
```

```
var e = 23;

function fun6(e){
   alert(e);  //undefined
}

fun6();
```

### 8.this

解析器在调用函数每次都会向函数内部传递进一个隐含的参数；这个隐含的参数就是this，this指向的是一个对象。

这个对象我们称为函数执行的 上下文对象

根据函数的调用方式的不同，this会指向不同的对象

1. 以函数的形式调用时，this永远都是window
2. 以方法的形式调用时，this就是调用方法的那个对象



其中，直接以函数形式调用，会输出  ‘全局的name属性’，this相当于windows；

但是刚打开页面时，‘全局的name属性’ 不会打印出来，因为先调用的fun函数，后定义的全局name，但是刷新页面就会打印出，因为name属性赋值给了全局变量window，除非销毁页面，那样定义的全局作用域变量才会失效。

以方法的形式调用，this是调用方法的对象。

```
function fun(){
   console.log(this.name);
}

//以函数形式调用，this是window
fun(); //全局的name属性

//创建一个对象
var obj = {
   name:"孙悟空",
   sayName:fun
};

console.log(obj.sayName == fun); //true
var name = "全局的name属性";

//以方法的形式调用，this是调用方法的对象
obj.sayName(); //孙悟空
```

#### 使用工厂法创建对象

可以通过该方法可以大批量的创建对象

使用工厂方法创建的对象，使用的构造函数都是Object，所以创建的对象都是Object这个类型，就导致我们无法区分出多种不同类型的对象

```
function createPerson(name , age ,gender){
   //创建一个新的对象
   var obj = new Object();
   //向对象中添加属性
   obj.name = name;
   obj.age = age;
   obj.gender = gender;
   obj.sayName = function(){
      alert(this.name);
   };
   //将新的对象返回
   return obj;
}

/*
 * 用来创建狗的对象
 */
function createDog(name , age){
   var obj = new Object();
   obj.name = name;
   obj.age = age;
   obj.sayHello = function(){
      alert("汪汪~~");
   };

   return obj;
}

var obj2 = createPerson("猪八戒",28,"男");
var obj3 = createPerson("白骨精",16,"女");
var obj4 = createPerson("蜘蛛精",18,"女");

//创建一个狗的对象
var dog = createDog("旺财",3);

console.log(dog); //{name: '旺财', age: 3, sayHello: ƒ}
console.log(obj4);  //{name: '蜘蛛精', age: 18, gender: '女', sayName: ƒ}
```

### 9.构造函数

可以创建一个构造函数，专门用来创建Person对象

- 构造函数就是一个普通的函数，创建方式和普通函数没有区别，不同的是构造函数习惯上首字母大写
- 构造函数和普通函数的区别就是调用方式的不同；普通函数是直接调用，而构造函数需要使用new关键字来调用


**构造函数的执行流程**：

1. 立刻创建一个新的对象
2. 将新建的对象设置为函数中this,在构造函数中可以使用this来引用新建的对象
3. 逐行执行函数中的代码
4. 将新建的对象作为返回值返回

使用同一个构造函数创建的对象，我们称为一类对象，也将一个构造函数称为一个类。
我们将通过一个构造函数创建的对象，称为是该类的实例（也就是说通过构造函数创建的对象可以知道它是哪一个类，而不用像工厂法创建的对象一样全是object）

**this的情况**：

1. 当以函数的形式调用时，this是window
2. 当以方法的形式调用时，谁调用方法this就是谁
3. 当以构造函数的形式调用时，this就是新创建的那个对象

```
function Person(name , age , gender){
   this.name = name;
   this.age = age;
   this.gender = gender;
   this.sayName = function(){
      alert(this.name);
   };
}

function Dog(){

}

var per = new Person("孙悟空",18,"男");
var per2 = new Person("玉兔精",16,"女");
var per3 = new Person("奔波霸",38,"男");

var dog = new Dog();

console.log(per); //Person {name: '孙悟空', age: 18, gender: '男', sayName: ƒ}
console.log(dog); //Dog {}
```

使用instanceof可以检查一个对象是否是一个类的实例，语法：

*对象 instanceof 构造函数*

如果是，则返回true，否则返回false

```
console.log(per instanceof Person); //true
console.log(dog instanceof Person); //false

/*
 * 所有的对象都是Object的后代，
 *     所以任何对象和Object左instanceof检查时都会返回true
 */
console.log(dog instanceof Object); //true
```

在Person构造函数中，为每一个对象都添加了一个sayName方法。

目前我们的方法是在构造函数内部创建的，也就是构造函数每执行一次就会创建一个新的sayName方法。

但是所有实例的sayName都是唯一的。这样就导致了构造函数执行一次就会创建一个新的方法，执行10000次就会创建10000个新的方法，而10000个方法都是一摸一样的，这是完全没有必要，完全可以使所有的对象共享同一个方法。

将函数定义在全局作用域，污染了全局作用域的命名空间，而且定义在全局作用域中也很不安全：

```
function Person(name , age , gender){
   this.name = name;
   this.age = age;
   this.gender = gender;
   //向对象中添加一个方法
   this.sayName = fun;
}
```

```
function fun(){
   alert("Hello大家好，我是:"+this.name);
};
```

所以可以向原型中添加sayName方法：

```
//向原型中添加sayName方法
Person.prototype.sayName = function(){
   alert("Hello大家好，我是:"+this.name);
};
```

```
var per = new Person("孙悟空",18,"男");
var per2 = new Person("猪八戒",28,"男");
per.sayName();
per2.sayName();

console.log(per.sayName == per2.sayName); //true
```

### 10.原型

- 我们所创建的每一个函数，解析器都会向函数中添加一个属性prototype，这个属性对应着一个对象，这个对象就是我们所谓的原型对象
- 如果函数作为普通函数调用prototype没有任何作用
- 当函数以构造函数的形式调用时，它所创建的对象中都会有一个隐含的属性，指向该构造函数的原型对象，我们可以通过__proto__来访问该属性
- 原型对象就相当于一个公共的区域，所有同一个类的实例都可以访问到这个原型对象，
  我们可以将对象中共有的内容，统一设置到原型对象中
- 当我们访问对象的一个属性或方法时，它会先在对象自身中寻找，如果有则直接使用，
  如果没有则会去原型对象中寻找，如果找到则直接使用
- 以后我们创建构造函数时，可以将这些对象共有的属性和方法，统一添加到构造函数的原型对象中
- 这样不用分别为每一个对象添加，也不会影响到全局作用域，就可以使每个对象都具有这些属性和方法了

![原型](https://raw.githubusercontent.com/weixiaoyun/Images/JavaScript/%E5%8E%9F%E5%9E%8B.png)

```
function MyClass(){

}

//向MyClass的原型中添加属性a
MyClass.prototype.a = 123;

//向MyClass的原型中添加一个方法
MyClass.prototype.sayHello = function(){
   alert("hello");
};

var mc = new MyClass();

var mc2 = new MyClass();

console.log(MyClass.prototype);  //{a: 123, sayHello: ƒ, constructor: ƒ}
console.log(mc2.__proto__ == MyClass.prototype); //true

//向mc中添加a属性
mc.a = "我是mc中的a";

console.log(mc.a); //我是mc中的a
console.log(mc2.a); //123
```

原型对象也是对象，所以它也有原型，当我们使用一个对象的属性或方法时，会现在自身中寻找：

- 自身中如果有，则直接使用
- 如果没有则去原型对象中寻找，如果原型对象中有，则使用
- 如果没有则去原型的原型中寻找,直到找到Object对象的原型
- Object对象的原型没有原型，如果在Object原型中依然没有找到，则返回undefined

```
function MyClass(){

}

//向MyClass的原型中添加一个name属性
MyClass.prototype.name = "我是原型中的名字";

var mc = new MyClass();
mc.age = 18;

console.log(mc.name); //我是原型中的名字
```

- 使用in检查对象中是否含有某个属性时，如果对象中没有但是原型中有，也会返回true
- 可以使用对象的hasOwnProperty()来检查对象自身中是否含有该属性，使用该方法只有当对象自身中含有属性时，才会返回true

```
//使用in检查对象中是否含有某个属性时，如果对象中没有但是原型中有，也会返回true
console.log("name" in mc); //true

/*可以使用对象的hasOwnProperty()来检查对象自身中是否含有该属性
使用该方法只有当对象自身中含有属性时，才会返回true*/
console.log(mc.hasOwnProperty("age")); //true
console.log(mc.hasOwnProperty("name")); //false
console.log(mc.hasOwnProperty("hasOwnProperty")); //false
```

```
console.log(mc.__proto__.hasOwnProperty("hasOwnProperty")); //false

console.log(mc.__proto__.__proto__.hasOwnProperty("hasOwnProperty")); //true

console.log(mc.hello); //undefined

//Object对象
console.log(mc.__proto__); //{name: '我是原型中的名字', constructor: ƒ}

//Object对象的原型
console.log(mc.__proto__.__proto__); //{constructor: ƒ, __defineGetter__: ƒ, __defineSetter__: ƒ, hasOwnProperty: ƒ, __lookupGetter__: ƒ, …}

console.log(mc.__proto__.__proto__.__proto__) //null
```

### 11.toString

当我们直接在页面中打印一个对象时，事件上是输出的对象的toString()方法的返回值

如果我们希望在输出对象时不输出[object Object]，可以为对象添加一个toString()方法

```
function Person(name , age , gender){
   this.name = name;
   this.age = age;
   this.gender = gender;
}

//修改Person原型的toString
Person.prototype.toString = function(){
   return "Person[name="+this.name+",age="+this.age+",gender="+this.gender+"]";
};

//创建一个Person实例
var per = new Person("孙悟空",18,"男");
```

```
var result = per.toString();
console.log("result = " + result); //result = Person[name=孙悟空,age=18,gender=男]
console.log(per.__proto__.hasOwnProperty("toString")) //true
console.log(per.__proto__.__proto__.hasOwnProperty("toString")); //true
```

### 12.垃圾回收（GC）

就像人生活的时间长了会产生垃圾一样，程序运行过程中也会产生垃圾；这些垃圾积攒过多以后，会导致程序运行的速度过慢；所以我们需要一个垃圾回收的机制，来处理程序运行过程中产生垃圾：

- 当一个对象没有任何的变量或属性对它进行引用，此时我们将永远无法操作该对象，此时这种对象就是一个垃圾，这种对象过多会占用大量的内存空间，导致程序运行变慢，所以这种垃圾必须进行清理
- 在JS中拥有自动的垃圾回收机制，会自动将这些垃圾对象从内存中销毁，
   我们不需要也不能进行垃圾回收的操作
- 我们需要做的只是要将不再使用的对象设置null即可

```
var obj = new Object();

//对对象进行各种操作。。。。

obj = null;
```

### 13.函数的方法

call()和apply()
   - 这两个方法都是函数对象的方法，需要通过函数对象来调用
   - 当对函数调用call()和apply()都会调用函数执行
   - 在调用call()和apply()可以将一个对象指定为第一个参数
      此时这个对象将会成为函数执行时的this
   - call()方法可以将实参在对象之后依次传递
   - apply()方法需要将实参封装到一个数组中统一传递

   - this的情况：
      1.以函数形式调用时，this永远都是window
      2.以方法的形式调用时，this是调用方法的对象
      3.以构造函数的形式调用时，this是新创建的那个对象
      4.使用call和apply调用时，this是指定的那个对象

```
function fun(a,b) {
   console.log("a = "+a);
   console.log("b = "+b);
}

var obj = {
   name: "obj",
   sayName:function(){
      alert(this.name);
   }
};


fun.call(obj,2,3); //a = 2 ;b = 3
fun.apply(obj,[2,3]); //a = 2 ;b = 3

var obj2 = {
   name: "obj2"
};

fun.apply();
fun.call();
fun();

fun.call(obj); //a = undefined;b = undefined
fun.apply(obj); //a = undefined;b = undefined

fun();

obj.sayName.apply(obj2); //alert 'obj2'
```

### 14.arguments

在调用函数时，浏览器每次都会传递进两个隐含的参数：

- 函数的上下文对象 this
- 封装实参的对象 arguments

arguments是一个类数组对象,它也可以通过索引来操作数据，也可以获取长度；在调用函数时，我们所传递的实参都会在arguments中保存

   - arguments.length可以用来获取实参的长度
      - 我们即使不定义形参，也可以通过arguments来使用实参，只不过比较麻烦
            - arguments[0] 表示第一个实参
        arguments[1] 表示第二个实参 。。。

   - 里边有一个属性callee，
         这个属性对应一个函数对象，就是当前正在指向的函数的对象

```
function fun(a,b){
   console.log(arguments instanceof Array); //false
   console.log(Array.isArray(arguments)); //false
   console.log(arguments[1]); //true
   console.log(arguments.length); //2
   console.log(arguments.callee == fun); //true
}

fun("hello",true);
```

## 十、数组（Array）

   - 数组也是一个对象
   - 它和我们普通对象功能类似，也是用来存储一些值的
   - 不同的是普通对象是使用字符串作为属性名的，而数组时使用数字来作为索引操作元素
   - 索引：从0开始的整数就是索引
   - 数组的存储性能比普通对象要好，在开发中我们经常使用数组来存储一些数据

```
var arr = new Array();

console.log(typeof arr); //object
```

向数组中添加元素，语法：*数组[索引] = 值*

```
arr[0] = 10;
arr[1] = 33;
arr[2] = 22;
arr[3] = 44;
```

读取数组中的元素，语法：*数组[索引]*

如果读取不存在的索引，他不会报错而是返回undefined

```
console.log(arr[3]); //44
```

获取数组的长度，可以使用length属性来获取数组的长度(元素的个数)
语法：*数组.length*

- 对于连续的数组，使用length可以获取到数组的长度（元素的个数）
- 对于非连续的数组，使用length会获取到数组的最大的索引+1，尽量不要创建非连续的数组

```
console.log(arr.length); //4
console.log(arr); // [10, 33, 22, 44]
```

修改length

- 如果修改的length大于原长度，则多出部分会空出来
- 如果修改的length小于原长度，则多出的元素会被删除

```
arr.length = 10;
console.log(arr.length); //10
console.log(arr); //[10, 33, 22, 44, 空属性 × 6]

arr.length = 2;

console.log(arr.length); //2
console.log(arr); //[10, 33]
```

向数组的最后一个位置添加元素；

语法：*数组[数组.length] = 值;*

```
arr[4] = 50;
arr[5] = 60;

arr[arr.length] = 70;
arr[arr.length] = 80;
arr[arr.length] = 90;

console.log(arr); // [10, 33, 22, 44, 50, 60, 70, 80, 90]
```

### 1.创建数组

#### 使用字面量来创建数组

语法: *[]*

```
var arr = [];

console.log(typeof arr); //object

//使用字面量创建数组时，可以在创建时就指定数组中的元素
var arr = [1,2,3,4,5,10];

console.log(arr[3]); //4
```

#### 使用构造函数创建数组

使用构造函数创建数组时，也可以同时添加元素，将要添加的元素作文构造函数的参数传递。元素之间使用,隔开

```
var arr2 = new Array(10,20,30); 
console.log(arr2);  //[10, 20, 30]
```

```
//创建一个数组数组中只有一个元素10
arr = [10];
console.log(arr.length) //1

//创建一个长度为10的数组
arr2 = new Array(10);

console.log(arr2.length);  //10
```

数组中的元素可以是任意的数据类型：

```
arr = ["hello",1,true,null,undefined];

//也可以是对象
var obj = {name:"孙悟空"};
arr[arr.length] = obj;
arr = [{name:"孙悟空"},{name:"沙和尚"},{name:"猪八戒"}];

//也可以是一个函数
arr = [function(){alert(1)},function(){alert(2)}];

console.log(arr); //[ƒ, ƒ]
arr[0]();
```

数组中也可以放数组，如下这种数组我们称为二维数组：

```
arr = [[1,2,3],[3,4,5],[5,6,7]];
console.log(arr[1]); // [3, 4, 5]
```

### 2.数组的方法

#### push()

- 该方法可以向数组的末尾添加一个或多个元素，并返回数组的新的长度
- 可以将要添加的元素作为方法的参数传递，这样这些元素将会自动添加到数组的末尾
- 该方法会将数组新的长度作为返回值返回

```
//创建一个数组
var arr = ["孙悟空","猪八戒","沙和尚"];

var result = arr.push("唐僧","蜘蛛精","白骨精","玉兔精");

console.log(arr);  //['孙悟空', '猪八戒', '沙和尚', '唐僧', '蜘蛛精', '白骨精', '玉兔精']
console.log("result = "+result);  //result = 7
```

#### pop()

该方法可以删除数组的最后一个元素,并将被删除的元素作为返回值返回

```
result = arr.pop();
console.log(arr); //['孙悟空', '猪八戒', '沙和尚', '唐僧', '蜘蛛精', '白骨精']
console.log("result = "+result); //result = 玉兔精
```

#### unshift()

   - 向数组开头添加一个或多个元素，并返回新的数组长度
   - 向前边插入元素以后，其他的元素索引会依次调整

```
arr.unshift("牛魔王","二郎神"); 

console.log(arr); //['牛魔王', '二郎神', '孙悟空', '猪八戒', '沙和尚', '唐僧', '蜘蛛精', '白骨精']
```

#### shift()

可以删除数组的第一个元素，并将被删除的元素作为返回值返回

```
result = arr.shift();

console.log(arr); //['二郎神', '孙悟空', '猪八戒', '沙和尚', '唐僧', '蜘蛛精', '白骨精']
console.log("result = "+result); //result = 牛魔王
```

#### forEach()

一般我们都是使用for循环去遍历数组，JS中还为我们提供了一个方法forEach()，用来遍历数组

这个方法只支持IE8以上的浏览器,IE8及以下的浏览器均不支持该方法，所以如果需要兼容IE8，则不要使用forEach,还是使用for循环来遍历

forEach()方法需要一个函数作为参数
   - 像这种函数，由我们创建但是不由我们调用的，我们称为回调函数
   - 数组中有几个元素函数就会执行几次，每次执行时，浏览器会将遍历到的元素
      以实参的形式传递进来，我们可以来定义形参，来读取这些内容
   - 浏览器会在回调函数中传递三个参数：
      - 第一个参数，就是当前正在遍历的元素
      - 第二个参数，就是当前正在遍历的元素的索引
      - 第三个参数，就是正在遍历的数组

```
var arr = ["孙悟空","猪八戒","沙和尚","唐僧","白骨精"];

arr.forEach(function(value , index , obj){
   console.log(value);
   console.log(index);
   console.log(obj);
});
```

#### slice()

- 可以用来从数组提取指定元素

- 该方法不会改变元素数组，而是将截取到的元素封装到一个新数组中返回

- 参数：

  截取开始的位置的索引,包含开始索引

  截取结束的位置的索引,不包含结束索引

     - 第二个参数可以省略不写,此时会截取从开始索引往后的所有元素
   - 索引可以传递一个负值，如果传递一个负值，则从后往前计算
      -1 倒数第一个
      -2 倒数第二个

```
var arr = ["孙悟空","猪八戒","沙和尚","唐僧","白骨精"];

var result = arr.slice(1,4);
console.log(result); // ['猪八戒', '沙和尚', '唐僧']
result = arr.slice(3);
console.log(result); //['唐僧', '白骨精']
result = arr.slice(1,-2); 
console.log(result); //['猪八戒', '沙和尚']
```

#### splice()

splice()
   - 可以用于删除数组中的指定元素
   - 使用splice()会影响到原数组，会将指定元素从原数组中删除,并将被删除的元素作为返回值返回
   - 参数：
      第一个，表示开始位置的索引
      第二个，表示删除的数量
      第三个及以后，可以传递一些新的元素，这些元素将会自动插入到开始位置索引前边

```
arr = ["孙悟空","猪八戒","沙和尚","唐僧","白骨精"];
var result = arr.splice(3,0,"牛魔王","铁扇公主","红孩儿");

console.log(arr); //['孙悟空', '猪八戒', '沙和尚', '牛魔王', '铁扇公主', '红孩儿', '唐僧', '白骨精']
console.log(result); //[]
```

#### concat()

concat()可以连接两个或多个数组，并将新的数组返回（该方法不会对原数组产生影响）

```
var arr = ["孙悟空","猪八戒","沙和尚"];
var arr2 = ["白骨精","玉兔精","蜘蛛精"];
var arr3 = ["二郎神","太上老君","玉皇大帝"];

var result = arr.concat(arr2,arr3,"牛魔王","铁扇公主");
console.log(result) //['孙悟空', '猪八戒', '沙和尚', '白骨精', '玉兔精', '蜘蛛精', '二郎神', '太上老君', '玉皇大帝', '牛魔王', '铁扇公主']
```

#### join()

- 该方法可以将数组转换为一个字符串
- 该方法不会对原数组产生影响，而是将转换后的字符串作为结果返回
- 在join()中可以指定一个字符串作为参数，这个字符串将会成为数组中元素的连接符
   如果不指定连接符，则默认使用,作为连接符

```
arr = ["孙悟空","猪八戒","沙和尚","唐僧"];

result = arr.join("@-@"); 
console.log(result) //孙悟空@-@猪八戒@-@沙和尚@-@唐僧
```

#### reverse()

- 该方法用来反转数组（前边的去后边，后边的去前边）
- 该方法会直接修改原数组

```
arr.reverse();

console.log(arr); // ['唐僧', '沙和尚', '猪八戒', '孙悟空']
```

#### sort()

- 可以用来对数组中的元素进行排序
- 也会影响原数组，默认会按照Unicode编码进行排序

```
arr = ["b","d","e","a","c"];

console.log(arr.sort())  //['a', 'b', 'c', 'd', 'e']
```

即使对于纯数字的数组，使用sort()排序时，也会按照Unicode编码来排序，所以对数字进排序时，可能会得到错误的结果。

我们可以自己来指定排序的规则,在sort()添加一个回调函数，来指定排序规则，

回调函数中需要定义两个形参，浏览器将会分别使用数组中的元素作为实参去调用回调函数；使用哪个元素调用不确定，但是肯定的是在数组中a一定在b前边

   - 浏览器会根据回调函数的返回值来决定元素的顺序，

      如果返回一个大于0的值，则元素会交换位置

      如果返回一个小于0的值，则元素位置不变

      如果返回一个0，则认为两个元素相等，也不交换位置

- 如果需要升序排列，则返回 a-b
  如果需要降序排列，则返回b-a

```
arr = [5,4,2,1,3,6,8,7];

arr.sort(function(a,b){

   //前边的大
   /*if(a > b){
      return -1;
   }else if(a < b){
      return 1;
   }else{
      return 0;
   }*/

   //升序排列
   //return a - b;

   //降序排列
   return b - a;

});

console.log(arr); //[8, 7, 6, 5, 4, 3, 2, 1]
```

### 3.数组的遍历

所谓的遍历数组，就是将数组中所有的元素都取出来

```
//创建一个数组
var arr = ["孙悟空","猪八戒","沙和尚","唐僧","白骨精"];

for(var i=0 ; i<arr.length ; i++){
   console.log(arr[i]);
}                       /*孙悟空
                  猪八戒
                  沙和尚
                  唐僧
                  白骨精*/
```

### 4.字符串的相关方法

在底层字符串是以字符数组的形式保存的：["H","e","l"]

#### length

可以用来获取字符串的长度

```
//创建一个字符串
var str = "Hello Weixiaoyun";

console.log(str.length); //16
console.log(str[5]); //' '
```

#### charCodeAt()

获取指定位置字符的字符编码（Unicode编码）

```
result = str.charCodeAt(0); //72
```

#### String.formCharCode()

可以根据字符编码去获取字符

```
result = String.fromCharCode(0x2692); //⚒
```

#### concat()

- 可以用来连接两个或多个字符串
- 作用和+一样

```
result = str.concat("你好","再见"); //Hello Weixiaoyun你好再见
```

#### indexOf()和lastIndexOf()

indexof()：
   - 该方法可以检索一个字符串中是否含有指定内容
   - 如果字符串中含有该内容，则会返回其第一次出现的索引
      如果没有找到指定的内容，则返回-1
   - 可以指定一个第二个参数，指定开始查找的位置

lastIndexOf()：
   - 该方法的用法和indexOf()一样，不同的是indexOf是从前往后找，而lastIndexOf是从后往前找
   - 也可以指定开始查找的位置

```
str = "hello hweixiaoyun";

result = str.indexOf("h",1); //6

result = str.lastIndexOf("h",5); //0
```

#### slice()

- 可以从字符串中截取指定的内容
- 不会影响原字符串，而是将截取到内容返回
- 参数：
   第一个，开始位置的索引（包括开始位置）
   第二个，结束位置的索引（不包括结束位置）
      - 如果省略第二个参数，则会截取到后边所有的
   - 也可以传递一个负数作为参数，负数的话将会从后边计算

```
str = "abcdefghijk";

result = str.slice(1,-1);
console.log(result) //bcdefghij
```

#### substring()

- 可以用来截取一个字符串，可以slice()类似
- 参数：
   - 第一个：开始截取位置的索引（包括开始位置）
   - 第二个：结束位置的索引（不包括结束位置）
   - 不同的是这个方法不能接受负值作为参数，
      如果传递了一个负值，则默认使用0
   - 而且他还自动调整参数的位置，如果第二个参数小于第一个，则自动交换

```
result = str.substring(0,1); //a
```

#### substr()

- 用来截取字符串
- 参数：
   - 截取开始位置的索引
   - 截取的长度

```
str = "abcdefg";

result = str.substr(3,2);
console.log(result) //de
```

#### split()

- 可以将一个字符串拆分为一个数组
- 参数：需要一个字符串作为参数，将会根据该字符串去拆分数组

```
str = "abcbcdefghij";

result = str.split("d");
console.log(result) //['abcbc', 'efghij']

/*
 * 如果传递一个空串作为参数，则会将每个字符都拆分为数组中的一个元素
 */
result = str.split("");

console.log(result); //['a', 'b', 'c', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j']
```

#### toUpperCase()

将一个字符串转换为大写并返回:

```
str = "abcdefg";

result = str.toUpperCase();
console.log(result); //ABCDEFG
```

#### toLowerCase()

将一个字符串转换为小写并返回:

```
str = "ABCDEFG";

result = str.toLowerCase();
console.log(result); //abcdefg
```

## 十一、Date

在JS中使用Date对象来表示一个时间

### 1.创建Date对象

如果直接使用构造函数创建一个Date对象，则会封装为当前代码执行的时间：

```
var d = new Date();
```

创建一个指定的时间对象：需要在构造函数中传递一个表示时间的字符串作为参数

日期的格式：  *月份/日/年 时:分:秒*

```
var d2 = new Date("2/18/2011 11:10:30");
```

### 2.获取日期对象的时间

#### getDate()

获取当前日期对象是几日

```
var date = d2.getDate(); //date = 18
```

#### getDay()

获取当前日期对象时周几

会返回一个0-6的值

- 0 表示周日
- 1表示周一。。。

```
var day = d2.getDay(); //day = 5
```

#### getMonth()

获取当前时间对象的月份

会返回一个0-11的值

- 0 表示1月
- 1 表示2月
- 11 表示12月

```
var month = d2.getMonth(); //month = 1
```

#### getFullYear()

获取当前日期对象的年份

```
var year = d2.getFullYear(); //2011
```

#### getTime()

获取当前日期对象的时间戳

   - 时间戳，指的是从格林威治标准时间的1970年1月1日，0时0分0秒
      到当前日期所花费的毫秒数（1秒 = 1000毫秒）
   - 计算机底层在保存时间时使用都是时间戳

```
var time = d2.getTime();

console.log(time/1000/60/60/24/365);  //41.15926655251142
```

```
//利用时间戳来测试代码的执行的性能
//获取当前的时间戳
var start = Date.now();

for(var i=0 ; i<100 ; i++){
   console.log(i);
}

var end = Date.now();
console.log(start);  //1649944828051
console.log(end);  //1649944828053

console.log("执行了："+(end - start)+"毫秒"); //执行了：2毫秒
```

## 十二、Math

- Math和其他的对象不同，它不是一个构造函数，
   它属于一个工具类，不用创建对象，它里边封装了数学运算相关的属性和方法
- 比如：Math.PI 表示的圆周率

```
console.log(Math.PI); //3.141592653589793
```

### 1.Math.abs()

可以用来计算一个数的绝对值

```
console.log(Math.abs(-1)); //1
```

### 2.Math.ceil()、Math.floor()、Math.round()

Math.ceil()：可以对一个数进行向上取整，小数位只有有值就自动进1

Math.floor()：可以对一个数进行向下取整，小数部分会被舍掉

Math.round()：可以对一个数进行四舍五入取整

```
console.log(Math.ceil(1.1)); //2
console.log(Math.floor(1.99)); //1
console.log(Math.round(1.4)); //1
```

### 3.Math.random()

- 可以用来生成一个0-1之间的随机数
- 生成一个0-x之间的随机数
   Math.round(Math.random()*x)
- 生成一个x-y之间的随机数
   Math.round(Math.random()*(y-x)+x)

### 4.Math.max()、Math.min()

max() 可以获取多个数中的最大值
min() 可以获取多个数中的最小值

```
var max = Math.max(10,45,30,100); //100
var min = Math.min(10,45,30,100); //10
```

### 5.Math.pow()

Math.pow(x,y)：返回x的y次幂

```
console.log(Math.pow(12,3)); //1728
```

### 6.Math.sqrt()

用于对一个数进行开方运算

```
console.log(Math.sqrt(2)); //1.4142135623730951
```

## 十三、包装类

在JS中为我们提供了三个包装类，通过这三个包装类可以将基本数据类型的数据转换为对象

- String()：可以将基本数据类型字符串转换为String对象
- Number()：可以将基本数据类型的数字转换为Number对象
- Boolean()：可以将基本数据类型的布尔值转换为Boolean对象
- 但是注意：我们在实际应用中不会使用基本数据类型的对象，如果使用基本数据类型的对象，在做一些比较时可能会带来一些不可预期的结果

```
var num = new Number(3);
var num2 = new Number(3);
var str = new String("hello");
var str2 = new String("hello");
var bool = new Boolean(true);
var bool2 = true;
```

```
console.log(str === str2); //false

var b = new Boolean(false);

if(b){
   console.log(b) //Boolean {false}
   alert("我运行了~~~"); //弹出'我运行了~~~'
}
```

方法和属性之能添加给对象，不能添加给基本数据类型

当我们对一些基本数据类型的值去调用属性和方法时：浏览器会临时使用包装类将其转换为对象，然后在调用对象的属性和方法；调用完以后，在将其转换为基本数据类型

```
var s = 123;

s = s.toString();

s.hello = "你好";

console.log(s.hello); //undefined
console.log(typeof s); //string
```

## 十四、正则表达式

正则表达式用于定义一些字符串的规则，计算机可以根据正则表达式，来检查一个字符串是否符合规则，将字符串中符合规则的内容提取出来

### 1.创建正则表达式

语法：

```
var 变量 = new RegExp("正则表达式","匹配模式");
```

使用typeof检查正则对象，会返回object

​	var reg = new RegExp("a"); 这个正则表达式可以来检查一个字符串中是否含有a

在构造函数中可以传递一个匹配模式作为第二个参数，可以是：

-  i 忽略大小写
- g 全局匹配模式

```
var reg = new RegExp("ab","i");

var str = "a";
```

### 2.正则表达式的方法

#### test()

使用这个方法可以用来检查一个字符串是否符合正则表达式的规则，如果符合则返回true，否则返回false

```
var result = reg.test(str);
console.log(result); //false
console.log(reg.test("Ac")); //false
```

### 3.使用字面量来创建正则表达式

```
语法：var 变量 = /正则表达式/匹配模式
```

使用字面量的方式创建更加简单，使用构造函数创建更加灵活

```
var reg = /a/i;

console.log(typeof reg); //object
console.log(reg.test("abc")); //true
```

**检查一个字符串中是否有a或b**：

使用 | 表示或者的意思

```
reg = /a|b|c/;
```



**创建一个正则表达式检查一个字符串中是否有字母**：

[]里的内容也是或的关系

- [ab] == a|b
- [a-z] 任意小写字母
- [A-Z] 任意大写字母
- [A-z] 任意字母
- [0-9] 任意数字

```
reg = /[A-z]/;
```

```
//检查一个字符串中是否含有 abc 或 adc 或 aec
reg = /a[bde]c/;
```

**[^ ] 除了**：

```
reg1 = /[^ab]/;

reg2 = /[^0-9]/;

console.log(reg1.test("ab")); //false
console.log(reg1.test("abc")); //true
console.log(reg2.test("12a3456")); //true
```

### 4.字符串和正则结合的方法

#### split()

- 可以将一个字符串拆分为一个数组
- 方法中可以传递一个正则表达式作为参数，这样方法将会根据正则表达式去拆分字符串
- 这个方法即使不指定全局匹配，也会全都插分

```
var str = "1a2b3c4d5e6f7";

var result = str.split(/[A-z]/); 

console.log(result); // ['1', '2', '3', '4', '5', '6', '7']
```

#### search()

- 可以搜索字符串中是否含有指定内容
- 如果搜索到指定内容，则会返回第一次出现的索引，如果没有搜索到返回-1
- 它可以接受一个正则表达式作为参数，然后会根据正则表达式去检索字符串
- serach()只会查找第一个，即使设置全局匹配也没用

```
str = "hello abc hello aec afc";
/*
 * 搜索字符串中是否含有abc 或 aec 或 afc
 */
result = str.search(/a[bef]c/);

console.log(result); //6
```

#### match()

- 可以根据正则表达式，从一个字符串中将符合条件的内容提取出来
- 默认情况下我们的match只会找到第一个符合要求的内容，找到以后就停止检索
   我们可以设置正则表达式为全局匹配模式，这样就会匹配到所有的内容
   可以为一个正则表达式设置多个匹配模式，且顺序无所谓
- match()会将匹配到的内容封装到一个数组中返回，即使只查询到一个结果

```
str = "1a2a3a4a5e6f7A8B9C";

result = str.match(/[a-z]/ig); 
console.log(result); //['a', 'a', 'a', 'a', 'e', 'f', 'A', 'B', 'C']
console.log(result[2]); //a
```

#### replace()

- 可以将字符串中指定内容替换为新的内容

- 参数：

   1.被替换的内容，可以接受一个正则表达式作为参数
   2.新的内容

- 默认只会替换第一个

```
result = str.replace(/[a-z]/gi , "");

console.log(result); //123456789
```

### 5.量词

- 通过量词可以设置一个内容出现的次数
- 量词只对它前边的一个内容起作用
- {n} 正好出现n次
- {m,n} 出现m-n次
- {m,} m次以上
- +： 至少一个，相当于{1,}
- *： 0个或多个，相当于{0,}
- ? ：0个或1个，相当于{0,1}

```
//创建一个正则表达式检查一个字符串中是否含有aaa
var reg = /a{3}/;
//ababab
reg = /(ab){3}/;

reg = /b{3}/;

reg = /ab{1,3}c/;

reg = /ab{3,}c/;

reg = /ab+c/;

reg = /ab*c/;

reg = /ab?c/;

console.log(reg.test("abbc")); //false
```

### 6.检测开头或结尾

- ^ 表示开头
- $ 表示结尾

```
reg = /^a/; //匹配开头的a

reg = /a$/; //匹配结尾的a
```

如果在正则表达式中同时使用^ $则要求字符串必须完全符合正则表达式：

```
reg = /^a$/;

console.log(reg.test("abbca")); //false
```

```
/*
 * 创建一个正则表达式，用来检查一个字符串是否是一个合法手机号
 *
 * 手机号的规则：
 *     1 3 567890123 （11位）
 *
 *     1. 以1开头
 *  2. 第二位3-9任意数字
 *     3. 三位以后任意数字9个
 *
 *  ^1   [3-9]  [0-9]{9}$
 *
 */

var phoneStr = "13067890123";

var phoneReg = /^1[3-9][0-9]{9}$/;

console.log(phoneReg.test(phoneStr)); //true
```

### 7.转义字符

. 表示任意字符

在正则表达式中使用\作为转义字符：

- \. 来表示.
- \\  表示\

注意：使用构造函数时，由于它的参数是一个字符串，而\是字符串中转义字符，
   如果要使用 \ 则需要使用 \\ 来代替

```
// 检查一个字符串中是否含有 .
var reg = /\./;

// 检查一个字符串中是否含有\
reg = /\\/;
```

\w：任意字母、数字、_        [A-z0-9_]

\W：除了字母、数字、_       [ ^A-z0-9_]

\d：任意的数字  [0-9]

\D：除了数字     [ ^0-9]

\s：空格

\S：除了空格

\b：单词边界

\B：除了单词边界



```
/*
 * 创建一个正则表达式检查一个字符串中是否含有单词child
 */

reg = /\bchild\b/;

console.log(reg.test("hello child ")); //true
```

去除字符串中的空格：

```
var str = "              he      llo                ";

//去除掉字符串中的空格
//去除空格就是使用""来替换空格

str = str.replace(/\s/g , "");
console.log(str); //hello
```

去除开头的空格：

```
str = str.replace(/^\s*/, "");
console.log(str)  //he      llo   
```

去除结尾的空格：

```
str = str.replace(/\s*$/, ""); 
console.log(str) //              he      llo
```

去除开头和结尾的空格：

```
str = str.replace(/^\s*|\s*$/g,"");

console.log(str); //he      llo
```

### 8.邮件的正则

```
/*
 * 电子邮件
 *     hello  .nihao          @     abc  .com.cn
 * 
 * 任意字母数字下划线    .任意字母数字下划线  @   任意字母数字     .任意字母（2-5位）   .任意字母（2-5位）
 * 
 * \w{3,}  (\.\w+)*  @  [A-z0-9]+  (\.[A-z]{2,5}){1,2}
 */

var emailReg = /^\w{3,}(\.\w+)*@[A-z0-9]+(\.[A-z]{2,5}){1,2}$/;

var email = "abc.hello@163.com";

console.log(emailReg.test(email)); //true
```

## 十五、DOM

DOM，全称Document Object Model（文档对象模型）

- JS中通过DOM来对HTML文档进行操作。只要理解了DOM就可以随心所欲的操作WEB页面。
- 文档：文档表示的就是整个的HTML网页文档
- 对象：对象表示将网页中的每一个部分都转换为了一个对象。
- 模型：使用模型来表示对象之间的关系，这样方便我们获取对象。

![模型](https://raw.githubusercontent.com/weixiaoyun/Images/JavaScript/%E6%A8%A1%E5%9E%8B.png)

### 1.节点

- 节点Node，是构成我们网页的最基本的组成部分，网页中的每一个部分都可以称为是一个节点。

  比如：html标签、属性、文本、注释、整个文档等都是一个节点。

- 虽然都是节点，但是实际上他们的具体类型是不同的。

  比如：标签我们称为元素节点、属性称为属性节点、文本称为文本节点、文档称为文档节点。

- 节点的类型不同，属性和方法也都不尽相同。

**节点**：Node——构成HTML文档最基本的单元。常用节点分为四类：

- 文档节点：整个HTML文档
- 元素节点：HTML文档中的HTML标签
- 属性节点：元素的属性
- 文本节点：HTML标签中的文本内容

![节点](https://raw.githubusercontent.com/weixiaoyun/Images/JavaScript/%E8%8A%82%E7%82%B9.png)

**节点的属性：**

![节点的属性](https://raw.githubusercontent.com/weixiaoyun/Images/JavaScript/%E8%8A%82%E7%82%B9%E7%9A%84%E5%B1%9E%E6%80%A7.png)

#### 文档节点

- 文档节点document，代表的是整个HTML文档，网页中的所有节点都是它的子节点。
- document对象作为window对象的属性存在的，我们不用获取可以直接使用。
- 通过该对象我们可以在整个文档访问内查找节点对象，并可以通过该对象创建各种节点对象。

#### 元素节点（Element）

- HTML中的各种标签都是元素节点，这也是我们最常用的一个节点。
- 浏览器会将页面中所有的标签都转换为一个元素节点，我们可以通过document的方法来获取元素节点。
- 比如：
  - document.getElementById()
  - 根据id属性值获取一个元素节点对象。

1.获取元素节点：通过document对象调用

- getElementById()：通过**id**属性获取**一个**元素节点对象

- getElementsByTagName()：通过**标签名**获取**一组**元素节点对象

- getElementsByName()：通过**name**属性获取**一组**元素节点对象

  ```
  var btn02 = document.getElementById("btn02");
  ```

  ```
  var lis = document.getElementsByTagName("li");
  ```

  ```
  var inputs = document.getElementsByName("gender");
  ```

2.获取元素节点的子节点：通过具体的元素节点调用

- getElementsByTagName()：方法，返回当前节点的指定标签名后代节点
- childNodes：属性，表示当前节点的所有子节点
- firstChild：属性，表示当前节点的第一个子节点
- lastChild：属性，表示当前节点的最后一个子节点

3.获取父节点和兄弟节点，通过具体的节点调用

- parentNode：属性，表示当前节点的父节点
- previousSibling：属性，表示当前节点的前一个兄弟节点
- nextSibling：属性，表示当前节点的后一个兄弟节点

4.元素节点的属性

- 获取，元素对象.属性名

  例：element.value

  element.id

  element.className

- 设置，元素对象.属性名=新的值

  例：element.value = “hello”

  element.id = “id01”

  element.className = “newClass”

#### 文本节点（Text）

- 文本节点表示的是HTML标签以外的文本内容，任意非HTML的文本都是文本节点。
- 它包括可以字面解释的纯文本内容。
- 文本节点一般是作为元素节点的子节点存在的。
- 获取文本节点时，一般先要获取元素节点。在通过元素节点获取文本节点。
- 例如：
  - 元素节点.firstChild;
  - 获取元素节点的第一个子节点，一般为文本节点

#### 属性节点（Attr）

- 属性节点表示的是标签中的一个一个的属性，这里要注意的是属性节点并非是元素节点的子节点，而是元素节点的一部分。
- 可以通过元素节点来获取指定的属性节点。
- 例如：元素节点.getAttributeNode("属性名");
- 注意：我们一般不使用属性节点。

```
<button id="btn">我是一个按钮</button>
<script type="text/javascript">
   
   //获取到button对象
   var btn = document.getElementById("btn");
   
   //修改按钮的文字
   btn.innerHTML = "I'm Button";
   
   
</script>
```

![DOM](https://raw.githubusercontent.com/weixiaoyun/Images/JavaScript/DOM.png)

#### 其他属性

- nodeValue：文本节点可以通过nodeValue属性获取和设置文本节点的内容
- innerHTML：元素节点通过该属性获取和设置标签内部的html代码

#### 使用CSS选择器进行查询

- querySelector()
- querySelectorAll()
- 这两个方法都是用document对象来调用，两个方法使用相同，都是传递一个选择器字符串作为参数，方法会自动根据选择器字符串去网页中查找元素。
- 不同的地方是querySelector()只会返回找到的第一个元素，而querySelectorAll()会返回所有符合条件的元素。

```
<div class="box1">
   <div>我是box1中的div</div>
</div>
```

```
var div = document.querySelector(".box1 div");

var box1 = document.querySelector(".box1")
```

#### 节点的修改

这里的修改我们主要指对元素节点的操作。

- 创建节点：document.createElement(标签名) 

  它需要一个标签名作为参数，将会根据该标签名创建元素节点对象，并将创建好的对象作为返回值返回

  ```
  var li = document.createElement("li");
  ```

- 创建一个文本节点对象：需要一个文本内容作为参数，将会根据该内容创建文本节点，并将新的节点返回

  ```
  var li = document.createElement("li");
  ```

  ```
  var gzText = document.createTextNode("广州");
  ```

- 删除节点：父节点.removeChild(子节点) 

  ```
  bj.parentNode.removeChild(bj);
  ```

- 替换节点：可以使用指定的子节点替换已有的子节点：父节点.replaceChild(新节点 , 旧节点) 

  ```
  city.replaceChild(li , bj);
  ```

- 插入节点：
  
  - 向一个父节点中添加一个新的子节点：父节点.appendChild(子节点) 
  
    ```
    li.appendChild(gzText);
    ```
  
  - 也可以通过innerHTML完成DOM的增删改的相关操作
  
    ```
    //创建一个li
    var li = document.createElement("li");
    //向li中设置文本
    li.innerHTML = "广州";
    //将li添加到city中
    city.appendChild(li);
    ```
  
  - 可以在指定的子节点前插入新的子节点：父节点.insertBefore(新节点 , 旧节点)
  
    ```
    city.insertBefore(li , bj);
    ```



### 2.事件

- 事件，就是文档或浏览器窗口中发生的一些特定的交互瞬间。 
- JavaScript 与 HTML 之间的交互是通过事件实现的。 
- 对于 Web 应用来说，有下面这些代表性的事件：点击某个元素、将鼠标移动至某个元素上方、按下键盘上某个键，等等。

我们可以在事件对应的属性中设置一些js代码，这样当事件被触发时，这些代码将会执行

这种写法我们称为结构和行为耦合，不方便维护，不推荐使用

```
<button id="btn" onmousemove="alert('讨厌，你点我干嘛！');">我是一个按钮</button>
```

可以为按钮的对应事件绑定处理函数的形式来响应事件；这样当事件被触发时，其对应的函数将会被调用

```
//获取按钮对象
var btn = document.getElementById("btn");

//绑定一个单击事件
//像这种为单击事件绑定的函数，我们称为单击响应函数
btn.onclick = function(){
   alert("你还点~~~");
};
```

点击超链接以后，超链接会跳转页面，这个是超链接的默认行为，但是此时我们不希望出现默认行为，可以通过在响应函数的最后return false来取消默认行为：

```
<script type="text/javascript">

   window.onload = function(){

      /*
       * 点击超链接以后，删除一个员工的信息
       */

      //获取所有额超链接
      var allA = document.getElementsByTagName("a");

      //为每个超链接都绑定一个单击响应函数
      for(var i=0 ; i < allA.length ; i++){
         allA[i].onclick = function(){

            //点击超链接以后需要删除超链接所在的那行
            //这里我们点击那个超链接this就是谁
            //获取当前tr
            var tr = this.parentNode.parentNode;

            //获取要删除的员工的名字
            //var name = tr.getElementsByTagName("td")[0].innerHTML;
            var name = tr.children[0].innerHTML;

            //删除之前弹出一个提示框
            /*
             * confirm()用于弹出一个带有确认和取消按钮的提示框
             *     需要一个字符串作为参数，该字符串将会作为提示文字显示出来
             * 如果用户点击确认则会返回true，如果点击取消则返回false
             */
            var flag = confirm("确认删除"+name+"吗?");

            //如果用户点击确认
            if(flag){
               //删除tr
               tr.parentNode.removeChild(tr);
            }

            /*
              点击超链接以后，超链接会跳转页面，这个是超链接的默认行为，
               但是此时我们不希望出现默认行为，可以通过在响应函数的最后return false来取消默认行为
             */
            return false;
         };
      }

   };


</script>
</head>
<body>

   <table id="employeeTable">
      <tr>
         <th>Name</th>
         <th>Email</th>
         <th>Salary</th>
         <th>&nbsp;</th>
      </tr>
      <tr>
         <td>Tom</td>
         <td>tom@tom.com</td>
         <td>5000</td>
         <td><a href="javascript:;">Delete</a></td>
      </tr>
      <tr>
         <td>Jerry</td>
         <td>jerry@sohu.com</td>
         <td>8000</td>
         <td><a href="deleteEmp?id=002">Delete</a></td>
      </tr>
      <tr>
         <td>Bob</td>
         <td>bob@tom.com</td>
         <td>10000</td>
         <td><a href="deleteEmp?id=003">Delete</a></td>
      </tr>
   </table>

   <div id="formDiv">

      <h4>添加新员工</h4>

      <table>
         <tr>
            <td class="word">name: </td>
            <td class="inp">
               <input type="text" name="empName" id="empName" />
            </td>
         </tr>
         <tr>
            <td class="word">email: </td>
            <td class="inp">
               <input type="text" name="email" id="email" />
            </td>
         </tr>
         <tr>
            <td class="word">salary: </td>
            <td class="inp">
               <input type="text" name="salary" id="salary" />
            </td>
         </tr>
         <tr>
            <td colspan="2" align="center">
               <button id="addEmpButton" value="abc">
                  Submit
               </button>
            </td>
         </tr>
      </table>

   </div>

</body>
</html>
```

### 3.文档的加载

浏览器在加载一个页面时，是按照自上向下的顺序加载的，读取到一行就运行一行,如果将script标签写到页面的上边，在代码执行时，页面还没有加载，页面没有加载DOM对象也没有加载，会导致无法获取到DOM对象

onload事件会在整个页面加载完成之后才触发；为window绑定一个onload事件：

该事件对应的响应函数将会在页面加载完成之后执行，这样可以确保我们的代码执行时所有的DOM对象已经加载完毕了

```
window.onload = function(){
   //获取id为btn的按钮
   var btn = document.getElementById("btn");
   //为按钮绑定一个单击响应函数
   btn.onclick = function(){
      alert("hello");
   };
};
```

```
<script type="text/javascript">

   /*
    * 将js代码编写到页面的下部就是为了，可以在页面加载完毕以后再执行js代码
    */
   //获取id为btn的按钮
   var btn = document.getElementById("btn");
   //为按钮绑定一个单击响应函数
   btn.onclick = function(){
      alert("hello");
   };

</script>
```

### 4.使用dom操作CSS3

通过JS修改元素的样式：

语法：*元素.style.样式名 = 样式值*

**注意**：如果CSS的样式名中含有-，这种名称在JS中是不合法的比如background-color，需要将这种样式名修改为驼峰命名法，去掉-，然后将-后的字母大写

我们通过style属性设置的样式都是内联样式，而内联样式有较高的优先级，所以通过JS修改的样式往往会立即显示，所以也无法获取样式表中的样式

但是如果在样式中写了!important，则此时样式会有最高的优先级，即使通过JS也不能覆盖该样式，此时将会导致JS修改样式失效，所以尽量不要为样式添加!important

```
<style type="text/css">

   #box1{
      width: 100px;
      height: 100px;
      background-color: red;
   }

</style>
```

```
<button id="btn01">点我一下</button>
<button id="btn02">点我一下2</button>

<br /><br />

<div id="box1"></div>
```

```
window.onload = function(){

   /*
    * 点击按钮以后，修改box1的大小
    */
   //获取box1
   var box1 = document.getElementById("box1");
   //为按钮绑定单击响应函数
   var btn01 = document.getElementById("btn01");
   btn01.onclick = function(){

      //修改box1的宽度
      box1.style.width = "300px";
      box1.style.height = "300px";
      box1.style.backgroundColor = "yellow";

   };


   //点击按钮2以后，读取元素的样式
   var btn02 = document.getElementById("btn02");
   btn02.onclick = function(){
      //读取box1的样式
      /*
       *     语法：元素.style.样式名
       *
       * 通过style属性设置和读取的都是内联样式
       *     无法读取样式表中的样式
       */
      alert(box1.style.width);  //300px
   };
};
```

#### 读取元素的样式

获取元素的当前显示的样式：

```
<button id="btn01">点我一下</button>
<br /><br />
<div id="box1" ></div>
```

**IE浏览器：**

语法：*元素.currentStyle.样式名*

它可以用来读取当前元素正在显示的样式，如果当前元素没有设置该样式，则获取它的默认值

currentStyle只有IE浏览器支持，其他的浏览器都不支持

```
alert(box1.currentStyle.width);
alert(box1.currentStyle.backgroundColor);
```

**其他浏览器：**

在其他浏览器中可以使用getComputedStyle()这个方法来获取元素当前的样式，这个方法是window的方法，可以直接使用，需要两个参数：

- 第一个：要获取样式的元素
- 第二个：可以传递一个伪元素，一般都传null

 该方法会返回一个对象，对象中封装了当前元素对应的样式：

可以通过 *对象.样式名* 来读取样式，如果获取的样式没有设置，则会获取到真实的值，而不是默认值；比如：没有设置width，它不会获取到auto，而是一个长度

但是该方法不支持IE8及以下的浏览器

```
var obj = getComputedStyle(box1,null);


//正常浏览器的方式
alert(getComputedStyle(box1,null).width);
alert(getComputedStyle(box1,null).backgroundColor);

//IE8的方式
alert(box1.currentStyle.backgroundColor);
```

**注意：**通过currentStyle和getComputedStyle()读取到的样式都是只读的，不能修改，如果要修改必须通过style属性

**兼容IE8和其他浏览器的方式：**

```
/*
 * 定义一个函数，用来获取指定元素的当前的样式
 * 参数：
 *        obj 要获取样式的元素
 *        name 要获取的样式名
 */

function getStyle(obj , name){

   if(window.getComputedStyle){
      //正常浏览器的方式，具有getComputedStyle()方法
      return getComputedStyle(obj , null)[name];
   }else{
      //IE8的方式，没有getComputedStyle()方法
      return obj.currentStyle[name];
   }

   //return window.getComputedStyle?getComputedStyle(obj , null)[name]:obj.currentStyle[name];

}
```

#### 其他样式操作的属性

**clientWidth & clientHeight**：

   - 这两个属性可以获取元素的可见宽度和高度
   - 这些属性都是不带px的，返回都是一个数字，可以直接进行计算
   - 会获取元素宽度和高度，包括内容区和内边距
 - 这些属性都是只读的，不能修改

```
alert(box1.clientWidth);
alert(box1.clientHeight);
```

**offsetWidth & offsetHeight：**

获取元素的整个的宽度和高度，包括内容区、内边距和边框

```
alert(box1.offsetWidth);
```

**offsetParent：**

   - 可以用来获取当前元素的定位父元素
 - 会获取到离当前元素最近的开启了定位的祖先元素；如果所有的祖先元素都没有开启定位，则返回body

```
var op = box1.offsetParent;

alert(op.id);
```

**offsetLeft & offsetTop：**

- offsetLeft ：当前元素相对于其定位父元素的水平偏移量
- offsetTop：当前元素相对于其定位父元素的垂直偏移量

```
alert(box1.offsetLeft);
```

**scrollWidth & scrollHeight：**

可以获取元素整个滚动区域的宽度和高度

```
alert(box4.scrollWidth);
```

**scrollLeft & scrollTop：**

   - scrollLeft：可以获取水平滚动条滚动的距离
   - scrollTop：可以获取垂直滚动条滚动的距离

**注意：**

当满足scrollHeight - scrollTop == clientHeight；说明垂直滚动条滚动到底了

当满足scrollWidth - scrollLeft == clientWidth；说明水平滚动条滚动到底

```
       #info{
         width: 300px;
         height: 500px;
         background-color: #bfa;
         overflow: auto;
      }
      
   </style>
   <script type="text/javascript">
      window.onload = function(){
         
         /*
          * 当垂直滚动条滚动到底时使表单项可用
          * onscroll
          *     - 该事件会在元素的滚动条滚动时触发
          */
         
         //获取id为info的p元素
         var info = document.getElementById("info");
         //获取两个表单项
         var inputs = document.getElementsByTagName("input");
         //为info绑定一个滚动条滚动的事件
         info.onscroll = function(){
            
            //检查垂直滚动条是否滚动到底
            if(info.scrollHeight - info.scrollTop == info.clientHeight){
               //滚动条滚动到底，使表单项可用
               /*
                * disabled属性可以设置一个元素是否禁用，
                *     如果设置为true，则元素禁用
                *     如果设置为false，则元素可用
                */
               inputs[0].disabled = false;
               inputs[1].disabled = false;
            }
            
         };
         
      };
      
      
   </script>
</head>
<body>
   <h3>欢迎亲爱的用户注册</h3>
   <p id="info">
      亲爱的用户，请仔细阅读以下协议，如果你不仔细阅读你就别注册
      亲爱的用户，请仔细阅读以下协议，如果你不仔细阅读你就别注册
      亲爱的用户，请仔细阅读以下协议，如果你不仔细阅读你就别注册
      亲爱的用户，请仔细阅读以下协议，如果你不仔细阅读你就别注册
      亲爱的用户，请仔细阅读以下协议，如果你不仔细阅读你就别注册
      亲爱的用户，请仔细阅读以下协议，如果你不仔细阅读你就别注册
      亲爱的用户，请仔细阅读以下协议，如果你不仔细阅读你就别注册
      亲爱的用户，请仔细阅读以下协议，如果你不仔细阅读你就别注册
      亲爱的用户，请仔细阅读以下协议，如果你不仔细阅读你就别注册
      亲爱的用户，请仔细阅读以下协议，如果你不仔细阅读你就别注册
      亲爱的用户，请仔细阅读以下协议，如果你不仔细阅读你就别注册
      亲爱的用户，请仔细阅读以下协议，如果你不仔细阅读你就别注册
      亲爱的用户，请仔细阅读以下协议，如果你不仔细阅读你就别注册
      亲爱的用户，请仔细阅读以下协议，如果你不仔细阅读你就别注册
      亲爱的用户，请仔细阅读以下协议，如果你不仔细阅读你就别注册
      亲爱的用户，请仔细阅读以下协议，如果你不仔细阅读你就别注册
      亲爱的用户，请仔细阅读以下协议，如果你不仔细阅读你就别注册
      亲爱的用户，请仔细阅读以下协议，如果你不仔细阅读你就别注册
      亲爱的用户，请仔细阅读以下协议，如果你不仔细阅读你就别注册
      亲爱的用户，请仔细阅读以下协议，如果你不仔细阅读你就别注册
      亲爱的用户，请仔细阅读以下协议，如果你不仔细阅读你就别注册
      亲爱的用户，请仔细阅读以下协议，如果你不仔细阅读你就别注册
      亲爱的用户，请仔细阅读以下协议，如果你不仔细阅读你就别注册
      亲爱的用户，请仔细阅读以下协议，如果你不仔细阅读你就别注册
      亲爱的用户，请仔细阅读以下协议，如果你不仔细阅读你就别注册
      亲爱的用户，请仔细阅读以下协议，如果你不仔细阅读你就别注册
      亲爱的用户，请仔细阅读以下协议，如果你不仔细阅读你就别注册
      亲爱的用户，请仔细阅读以下协议，如果你不仔细阅读你就别注册
      亲爱的用户，请仔细阅读以下协议，如果你不仔细阅读你就别注册
      亲爱的用户，请仔细阅读以下协议，如果你不仔细阅读你就别注册
      亲爱的用户，请仔细阅读以下协议，如果你不仔细阅读你就别注册
      亲爱的用户，请仔细阅读以下协议，如果你不仔细阅读你就别注册
      亲爱的用户，请仔细阅读以下协议，如果你不仔细阅读你就别注册
      亲爱的用户，请仔细阅读以下协议，如果你不仔细阅读你就别注册
      亲爱的用户，请仔细阅读以下协议，如果你不仔细阅读你就别注册
      亲爱的用户，请仔细阅读以下协议，如果你不仔细阅读你就别注册
      亲爱的用户，请仔细阅读以下协议，如果你不仔细阅读你就别注册
      亲爱的用户，请仔细阅读以下协议，如果你不仔细阅读你就别注册
      亲爱的用户，请仔细阅读以下协议，如果你不仔细阅读你就别注册
      亲爱的用户，请仔细阅读以下协议，如果你不仔细阅读你就别注册
      亲爱的用户，请仔细阅读以下协议，如果你不仔细阅读你就别注册
      亲爱的用户，请仔细阅读以下协议，如果你不仔细阅读你就别注册
      亲爱的用户，请仔细阅读以下协议，如果你不仔细阅读你就别注册
      亲爱的用户，请仔细阅读以下协议，如果你不仔细阅读你就别注册
      亲爱的用户，请仔细阅读以下协议，如果你不仔细阅读你就别注册
      亲爱的用户，请仔细阅读以下协议，如果你不仔细阅读你就别注册
      亲爱的用户，请仔细阅读以下协议，如果你不仔细阅读你就别注册
      亲爱的用户，请仔细阅读以下协议，如果你不仔细阅读你就别注册
      亲爱的用户，请仔细阅读以下协议，如果你不仔细阅读你就别注册
      ...
   </p>
   <!-- 如果为表单项添加disabled="disabled" 则表单项将变成不可用的状态 -->
   <input type="checkbox" disabled="disabled" />我已仔细阅读协议，一定遵守
   <input type="submit" value="注册" disabled="disabled" />
</body>
```

### 5.事件对象

当事件的响应函数被触发时，浏览器每次都会将一个事件对象**作为实参**传递进响应函数。在事件对象中封装了当前事件相关的一切信息，比如：鼠标的坐标  键盘哪个按键被按下  鼠标滚轮滚动的方向。。。

```
<script type="text/javascript">

   window.onload = function(){
      /*
       * 当鼠标在areaDiv中移动时，在showMsg中来显示鼠标的坐标
       */
      //获取两个div
      var areaDiv = document.getElementById("areaDiv");
      var showMsg = document.getElementById("showMsg");

      /*onmousemove
       该事件将会在鼠标在元素中移动时被触发*/
      areaDiv.onmousemove = function(event){

         /*
          * 在IE8中，响应函数被处罚时，浏览器不会传递事件对象，
          *     在IE8及以下的浏览器中，是将事件对象作为window对象的属性保存的
          */
         /*if(!event){
            event = window.event;
         }*/

         //解决事件对象的兼容性问题
         event = event || window.event;

         /*
          * clientX可以获取鼠标指针的水平坐标
          * cilentY可以获取鼠标指针的垂直坐标
          */
         var x = event.clientX;
         var y = event.clientY;

         //alert("x = "+x + " , y = "+y);

         //在showMsg中显示鼠标的坐标
         showMsg.innerHTML = "x = "+x + " , y = "+y;

      };

   };

</script>
</head>
<body>

   <div id="areaDiv"></div>
   <div id="showMsg"></div>

</body>
```

![事件对象](https://raw.githubusercontent.com/weixiaoyun/Images/JavaScript/%E4%BA%8B%E4%BB%B6%E5%AF%B9%E8%B1%A1.png)

让box根据鼠标的位置移动：

```
    <style type="text/css">
      #box1{
         width: 100px;
         height: 100px;
         background-color: red;
         /*
          * 开启box1的绝对定位
          */
         position: absolute;
      }
      
   </style>
   
   <script type="text/javascript">
      window.onload = function(){
         
         /*
          * 使div可以跟随鼠标移动
          */
         
         //获取box1
         var box1 = document.getElementById("box1");
         //绑定鼠标移动事件
         document.onmousemove = function(event){
            
            //解决兼容问题
            event = event || window.event;
            
            //获取滚动条滚动的距离
            /*
             * chrome认为浏览器的滚动条是body的，可以通过body.scrollTop来获取
             * 火狐等浏览器认为浏览器的滚动条是html的，
             */
            var st = document.body.scrollTop || document.documentElement.scrollTop;
            var sl = document.body.scrollLeft || document.documentElement.scrollLeft;
            //var st = document.documentElement.scrollTop;
            
            
            //获取到鼠标的坐标
            /*
             * clientX和clientY
             *     用于获取鼠标在当前的可见窗口的坐标
             * div的偏移量，是相对于整个页面的
             * 
             * pageX和pageY可以获取鼠标相对于当前页面的坐标
             *     但是这个两个属性在IE8中不支持，所以如果需要兼容IE8，则不要使用
             */
            var left = event.clientX;
            var　top = event.clientY;
            
            //设置div的偏移量
            box1.style.left = left + sl + "px";
            box1.style.top = top + st + "px";
            
         };
         
         
      };
      
      
   </script>
</head>
<body style="height: 1000px;width: 2000px;">
   <div id="box1"></div>
</body>
```

### 6.事件的冒泡（Bubble）

- 所谓的冒泡指的就是事件的向上传导，当后代元素上的事件被触发时，其祖先元素的相同事件也会被触发
- 在开发中大部分情况冒泡都是有用的,如果不希望发生事件冒泡可以通过事件对象来取消冒泡

```
<div id="box1">
   我是box1
   <span id="s1">我是span</span>
</div>
```

可以将事件对象的cancelBubble设置为true，即可取消冒泡：

```
//为s1绑定一个单击响应函数
   var s1 = document.getElementById("s1");
   s1.onclick = function(event){
      event = event || window.event;
      alert("我是span的单击响应函数");

      //取消冒泡
      event.cancelBubble = true;
   };

   //为box1绑定一个单击响应函数
   var box1 = document.getElementById("box1");
   box1.onclick = function(event){
      event = event || window.event;
      alert("我是div的单击响应函数");

      event.cancelBubble = true;
   };

   //为body绑定一个单击响应函数
   document.body.onclick = function(){
      alert("我是body的单击响应函数");
   };


};
```

### 7.事件的委派

- 指将事件统一绑定给元素的共同的祖先元素，这样当后代元素上的事件触发时，会一直冒泡到祖先元素，从而通过祖先元素的响应函数来处理事件。
- 事件委派是利用了冒泡，通过委派可以减少事件绑定的次数，提高程序的性能

```
<body>
   <button id="btn01">添加超链接</button>

   <ul id="u1" style="background-color: #bfa;">
      <li>
         <p>我是p元素</p>
      </li>
      <li><a href="javascript:;" class="link">超链接一</a></li>
      <li><a href="javascript:;" class="link">超链接二</a></li>
      <li><a href="javascript:;" class="link">超链接三</a></li>
   </ul>

</body>
```

一个个为超链接绑定单击响应函数很麻烦：

```
var u1 = document.getElementById("u1");

//点击按钮以后添加超链接
var btn01 = document.getElementById("btn01");
btn01.onclick = function(){
   //创建一个li
   var li = document.createElement("li");
   li.innerHTML = "<a href='javascript:;' class='link'>新建的超链接</a>";

   //将li添加到ul中
   u1.appendChild(li);
};


/*
 * 为每一个超链接都绑定一个单击响应函数
 * 这里我们为每一个超链接都绑定了一个单击响应函数，这种操作比较麻烦，
 *     而且这些操作只能为已有的超链接设置事件，而新添加的超链接必须重新绑定
 */
//获取所有的a
var allA = document.getElementsByTagName("a");
//遍历
/*for(var i=0 ; i<allA.length ; i++){
   allA[i].onclick = function(){
      alert("我是a的单击响应函数！！！");
   };
}*/
```

而我们希望，只绑定一次事件，即可应用到多个的元素上，即使元素是后添加的，我们可以尝试将其绑定给元素的共同的祖先元素：

```
//为ul绑定一个单击响应函数
   u1.onclick = function(event){
      event = event || window.event;

      /*
       * target
       *     - event中的target表示的触发事件的对象
       */
      //alert(event.target);


      //如果触发事件的对象是我们期望的元素，则执行否则不执行
      if(event.target.className == "link"){
         alert("我是ul的单击响应函数");
      }

   };

};
```

### 8.事件的绑定

使用 *对象.事件 = 函数* 的形式绑定响应函数，它只能同时为一个元素的一个事件绑定一个响应函数，不能绑定多个，如果绑定了多个，则后边会覆盖掉前边的

```
//为btn01绑定一个单击响应函数
btn01.onclick = function(){
   alert(1);
};

//为btn01绑定第二个响应函数
btn01.onclick = function(){
   alert(2);
};
```

addEventListener()
   - 通过这个方法也可以为元素绑定响应函数
 - 参数：
      1.事件的字符串，不要on
      2.回调函数，当事件触发时该函数会被调用
      3.是否在捕获阶段触发事件，需要一个布尔值，一般都传false

使用addEventListener()可以同时为一个元素的相同事件同时绑定多个响应函数，这样当事件被触发时，响应函数将会按照函数的绑定顺序执行

**注意：**这个方法不支持IE8及以下的浏览器

```
btn01.addEventListener("click",function(){
   alert(1);
},false);

btn01.addEventListener("click",function(){
   alert(2);
},false);

btn01.addEventListener("click",function(){
   alert(3);
},false);
```

attachEvent()
   - 在IE8中可以使用attachEvent()来绑定事件
 - 参数：
      1.事件的字符串，要on
      2.回调函数

 - 这个方法也可以同时为一个事件绑定多个处理函数，不同的是它是后绑定先执行，执行顺序和addEventListener()相反

```
btn01.attachEvent("onclick",function(){
   alert(1);
});

btn01.attachEvent("onclick",function(){
   alert(2);
});

btn01.attachEvent("onclick",function(){
   alert(3);
});
```

兼容IE8和以上浏览器

```
/*
 * addEventListener()中的this，是绑定事件的对象
 * attachEvent()中的this，是window
 *  需要统一两个方法this
 */
/*
 * 参数：
 *     obj 要绑定事件的对象
 *     eventStr 事件的字符串(不要on)
 *  callback 回调函数
 */
function bind(obj , eventStr , callback){
   if(obj.addEventListener){
      //大部分浏览器兼容的方式
      obj.addEventListener(eventStr , callback , false);
   }else{
      /*
       * this是谁由调用方式决定
       * callback.call(obj)
       */
      //IE8及以下
      obj.attachEvent("on"+eventStr , function(){
         //在匿名函数中调用回调函数
         callback.call(obj);
      });
   }
}
```

### 9.事件的传播

- 关于事件的传播网景公司和微软公司有不同的理解

- 微软公司认为事件应该是由内向外传播，也就是当事件触发时，应该先触发当前元素上的事件，然后再向当前元素的祖先元素上传播，也就说事件应该在冒泡阶段执行。

- 网景公司认为事件应该是由外向内传播的，也就是当前事件触发时，应该先触发当前元素的最外层的祖先元素的事件，然后在向内传播给后代元素

- W3C综合了两个公司的方案，将事件传播分成了三个阶段：

   1.捕获阶段：在捕获阶段时从最外层的祖先元素，向目标元素进行事件的捕获，但是默认此时不会触发事件

   2.目标阶段：事件捕获到目标元素，捕获结束开始在目标元素上触发事件

   3.冒泡阶段

      - 事件从目标元素向他的祖先元素传递，依次触发祖先元素上的事件

   - 如果希望在捕获阶段就触发事件，可以将addEventListener()的第三个参数设置为true
      一般情况下我们不会希望在捕获阶段触发事件，所以这个参数一般都是false

- IE8及以下的浏览器中没有捕获阶段

   ![事件的传播](https://raw.githubusercontent.com/weixiaoyun/Images/JavaScript/%E4%BA%8B%E4%BB%B6%E7%9A%84%E4%BC%A0%E6%92%AD.png)

```
function bind(obj , eventStr , callback){
   if(obj.addEventListener){
      //大部分浏览器兼容的方式
      obj.addEventListener(eventStr , callback , true);
   }else{
      /*
       * this是谁由调用方式决定
       * callback.call(obj)
       */
      //IE8及以下
      obj.attachEvent("on"+eventStr , function(){
         //在匿名函数中调用回调函数
         callback.call(obj);
      });
   }
}
```

### 10.拖拽

拖拽的流程：

1. 当鼠标在被拖拽元素上按下时，开始拖拽  onmousedown
2. 当鼠标移动时被拖拽元素跟随鼠标移动 onmousemove
3. 当鼠标松开时，被拖拽元素固定在当前位置  onmouseup

```
<body>
   <div id="box1"></div>

   <div id="box2"></div>
</body>
```

```
//获取box1
var box1 = document.getElementById("box1");
//为box1绑定一个鼠标按下事件
//当鼠标在被拖拽元素上按下时，开始拖拽  onmousedown
box1.onmousedown = function(event){
   event = event || window.event;
   //div的偏移量 鼠标.clentX - 元素.offsetLeft
   //div的偏移量 鼠标.clentY - 元素.offsetTop
   var ol = event.clientX - box1.offsetLeft;
   var ot = event.clientY - box1.offsetTop;


   //为document绑定一个onmousemove事件
   document.onmousemove = function(event){
      event = event || window.event;
      //当鼠标移动时被拖拽元素跟随鼠标移动 onmousemove
      //获取鼠标的坐标
      var left = event.clientX - ol;
      var top = event.clientY - ot;

      //修改box1的位置
      box1.style.left = left+"px";
      box1.style.top = top+"px";

   };

   //为document绑定一个鼠标松开事件
   document.onmouseup = function(){
      //当鼠标松开时，被拖拽元素固定在当前位置  onmouseup
      //取消document的onmousemove事件
      document.onmousemove = null;
      //取消document的onmouseup事件
      document.onmouseup = null;
   };
```

当我们拖拽一个网页中的内容时，浏览器会默认去搜索引擎中搜索内容，此时会导致拖拽功能的异常，这个是浏览器提供的默认行为，如果不希望发生这个行为，则可以通过return false来取消默认行为，但是对IE8不起作用，所以借助setCapture()解决：

当调用一个元素的setCapture()方法以后，这个元素将会把下一次所有的鼠标按下相关的事件捕获到自身上（只有IE支持，但是在火狐中调用时不会报错，而如果使用chrome调用，会报错）：

```
btn01.onclick = function(){
   alert(1);
};
```

```
//设置btn01对鼠标按下相关的事件进行捕获
btn01.setCapture();
```

对于IE8:

```
//获取box1
var box1 = document.getElementById("box1");
var box2 = document.getElementById("box2");
//为box1绑定一个鼠标按下事件
//当鼠标在被拖拽元素上按下时，开始拖拽  onmousedown
box1.onmousedown = function(event){

   //设置box1捕获所有鼠标按下的事件
   /*
    * setCapture()
      - 只有IE支持，但是在火狐中调用时不会报错，
         而如果使用chrome调用，会报错
    */
   /*if(box1.setCapture){
      box1.setCapture();
   }*/
   box1.setCapture && box1.setCapture();


   event = event || window.event;
   //div的偏移量 鼠标.clentX - 元素.offsetLeft
   //div的偏移量 鼠标.clentY - 元素.offsetTop
   var ol = event.clientX - box1.offsetLeft;
   var ot = event.clientY - box1.offsetTop;


   //为document绑定一个onmousemove事件
   document.onmousemove = function(event){
      event = event || window.event;
      //当鼠标移动时被拖拽元素跟随鼠标移动 onmousemove
      //获取鼠标的坐标
      var left = event.clientX - ol;
      var top = event.clientY - ot;

      //修改box1的位置
      box1.style.left = left+"px";
      box1.style.top = top+"px";

   };

   //为document绑定一个鼠标松开事件
   document.onmouseup = function(){
      //当鼠标松开时，被拖拽元素固定在当前位置  onmouseup
      //取消document的onmousemove事件
      document.onmousemove = null;
      //取消document的onmouseup事件
      document.onmouseup = null;
      //当鼠标松开时，取消对事件的捕获
      box1.releaseCapture && box1.releaseCapture();
   };

   /*
    * 当我们拖拽一个网页中的内容时，浏览器会默认去搜索引擎中搜索内容，
    *     此时会导致拖拽功能的异常，这个是浏览器提供的默认行为，
    *     如果不希望发生这个行为，则可以通过return false来取消默认行为
    *
    * 但是对IE8不起作用
    */
   return false;

};
```

提取一个专门用来设置拖拽的函数drag

参数：开启拖拽的元素

```
function drag(obj){
   //当鼠标在被拖拽元素上按下时，开始拖拽  onmousedown
   obj.onmousedown = function(event){

      //设置box1捕获所有鼠标按下的事件
      /*
       * setCapture()
       *     - 只有IE支持，但是在火狐中调用时不会报错，
       *        而如果使用chrome调用，会报错
       */
      /*if(box1.setCapture){
         box1.setCapture();
      }*/
      obj.setCapture && obj.setCapture();


      event = event || window.event;
      //div的偏移量 鼠标.clentX - 元素.offsetLeft
      //div的偏移量 鼠标.clentY - 元素.offsetTop
      var ol = event.clientX - obj.offsetLeft;
      var ot = event.clientY - obj.offsetTop;


      //为document绑定一个onmousemove事件
      document.onmousemove = function(event){
         event = event || window.event;
         //当鼠标移动时被拖拽元素跟随鼠标移动 onmousemove
         //获取鼠标的坐标
         var left = event.clientX - ol;
         var top = event.clientY - ot;

         //修改box1的位置
         obj.style.left = left+"px";
         obj.style.top = top+"px";

      };

      //为document绑定一个鼠标松开事件
      document.onmouseup = function(){
         //当鼠标松开时，被拖拽元素固定在当前位置  onmouseup
         //取消document的onmousemove事件
         document.onmousemove = null;
         //取消document的onmouseup事件
         document.onmouseup = null;
         //当鼠标松开时，取消对事件的捕获
         obj.releaseCapture && obj.releaseCapture();
      };

      /*
       * 当我们拖拽一个网页中的内容时，浏览器会默认去搜索引擎中搜索内容，
       *     此时会导致拖拽功能的异常，这个是浏览器提供的默认行为，
       *     如果不希望发生这个行为，则可以通过return false来取消默认行为
       *
       * 但是对IE8不起作用
       */
      return false;

   };
```

### 11.滚轮事件

- onmousewheel：鼠标滚轮滚动的事件，会在滚轮滚动时触发，但是火狐不支持该属性
- 在火狐中需要使用 DOMMouseScroll 来绑定滚动事件，注意该事件需要通addEventListener()函数来绑定

**注意：**使用addEventListener()方法绑定响应函数，取消默认行为时不能使用return false，需要使用event来取消默认行为event.preventDefault();

```
var box1 = document.getElementById("box1");

//为box1绑定一个鼠标滚轮滚动的事件

box1.onmousewheel = function(event){

   event = event || window.event;


   //event.wheelDelta 可以获取鼠标滚轮滚动的方向
   //向上滚 120   向下滚 -120
   //wheelDelta这个值我们不看大小，只看正负

   //alert(event.wheelDelta);

   //wheelDelta这个属性火狐中不支持
   //在火狐中使用event.detail来获取滚动的方向
   //向上滚 -3  向下滚 3
   //alert(event.detail);


   /*
    * 当鼠标滚轮向下滚动时，box1变长
    *     当滚轮向上滚动时，box1变短
    */
   //判断鼠标滚轮滚动的方向
   if(event.wheelDelta > 0 || event.detail < 0){
      //向上滚，box1变短
      box1.style.height = box1.clientHeight - 10 + "px";

   }else{
      //向下滚，box1变长
      box1.style.height = box1.clientHeight + 10 + "px";
   }

   /*
     使用addEventListener()方法绑定响应函数，取消默认行为时不能使用return false
     需要使用event来取消默认行为event.preventDefault();
     但是IE8不支持event.preventDefault();这个玩意，如果直接调用会报错
    */
   event.preventDefault && event.preventDefault();


   /*
    * 当滚轮滚动时，如果浏览器有滚动条，滚动条会随之滚动，
    * 这是浏览器的默认行为，如果不希望发生，则可以取消默认行为
    */
   return false;


	//为火狐绑定滚轮事件
	bind(box1,"DOMMouseScroll",box1.onmousewheel);

};
```

```
function bind(obj , eventStr , callback){
   if(obj.addEventListener){
      //大部分浏览器兼容的方式
      obj.addEventListener(eventStr , callback , false);
   }else{
      /*
       * this是谁由调用方式决定
       * callback.call(obj)
       */
      //IE8及以下
      obj.attachEvent("on"+eventStr , function(){
         //在匿名函数中调用回调函数
         callback.call(obj);
      });
   }
}
```

### 12.键盘事件

**onkeydown：**

   - 按键被按下
   - 对于onkeydown来说如果一直按着某个按键不松手，则事件会一直触发
   - 当onkeydown连续触发时，第一次和第二次之间会间隔稍微长一点，其他的会非常的快
      这种设计是为了防止误操作的发生。

**onkeyup：**

按键被松开

键盘事件一般都会绑定给一些可以获取到焦点的对象或者是document



可以通过keyCode来获取按键的编码，通过它可以判断哪个按键被按下

除了keyCode，事件对象中还提供了几个属性：altKey、ctrlKey、shiftKey

这个三个用来判断alt ctrl 和 shift是否被按下，如果按下则返回true，否则返回false

```
//判断y和ctrl是否同时被按下
if(event.keyCode === 89 && event.ctrlKey){
   console.log("ctrl和y都被按下了");
}
```

```
//获取input
var input = document.getElementsByTagName("input")[0];

input.onkeydown = function(event){

   event = event || window.event;

   //console.log(event.keyCode);
   //数字 48 - 57
   //使文本框中不能输入数字
   if(event.keyCode >= 48 && event.keyCode <= 57){
      //在文本框中输入内容，属于onkeydown的默认行为
      //如果在onkeydown中取消了默认行为，则输入的内容，不会出现在文本框中
      return false;
   }
```

## 十六、BOM

浏览器对象模型：BOM可以使我们通过JS来操作浏览器；在BOM中为我们提供了一组对象，用来完成对浏览器的操作，这些功能与任何网页内容无关。

BOM对象：

- Window：代表的是整个浏览器的窗口，同时window也是网页中的全局对象
- Navigator：代表的当前浏览器的信息，通过该对象可以来识别不同的浏览器
- Location：代表当前浏览器的地址栏信息，通过Location可以获取地址栏信息，或者操作浏览器跳转页面
- History：代表浏览器的历史记录，可以通过该对象来操作浏览器的历史记录；由于隐私原因，该对象不能获取到具体的历史记录，只能操作浏览器向前或向后翻页；而且该操作只在当次访问时有效
- Screen：代表用户的屏幕的信息，通过该对象可以获取到用户的显示器的相关的信息

这些BOM对象在浏览器中都是作为window对象的属性保存的，可以通过window对象来使用，也可以直接使用

### 1.window对象

- window对象是BOM的核心，它表示一个浏览器的实例。
- 在浏览器中我们可以通过window对象来访问操作浏览器，同时window也是作为全局对象存在的。
- 全局作用域：window对象是浏览器中的全局对象，因此所有在全局作用域中声明的变量、对象、函数都会变成window对象的属性和方法。

#### 窗口大小

浏览器中提供了四个属性用来确定窗口的大小：

- 网页窗口的大小

  innerWidth

  innerHeight

- 浏览器本身的尺寸

  outerWidth

  outerHeight

#### 打开窗口

使用 window.open() 方法既可以导航到一个特定的 URL，也可以打开一个新的浏览器窗口。 

这个方法需要四个参数：

- 需要加载的url地址
- 窗口的目标
-  一个特性的字符串
- 是否创建新的历史记录

#### 超时调用/延时调用

- 延时调用一个函数不马上执行，而是隔一段时间以后在执行，而且只会执行一次

- 延时调用和定时调用的区别，定时调用会执行多次，而延时调用只会执行一次

- 延时调用和定时调用实际上是可以互相代替的，在开发中可以根据自己需要去选择

setTimeout()

- 超过一定时间以后执行指定函数
- 需要2个参数：要执行的内容、超过的时间

取消超时调用：clearTimeout()

超时调用都是在全局作用域中执行的。

```
var timer = setTimeout(function(){
   console.log(num++);
},3000);

//使用clearTimeout()来关闭一个延时调用
clearTimeout(timer);
```

#### 间歇调用/定时调用

可以将一个函数，每隔一段时间执行一次

- setInterval()：每隔一段时间执行指定代码

- clearInterval()：取消间隔调用

- 参数：

  - 回调函数，该函数会每隔一段时间被调用一次
  - 每次调用间隔的时间，单位是毫秒

- 返回值：返回一个Number类型的数据，这个数字用来作为定时器的唯一标识

  ```
  var num = 1;
  
  var timer = setInterval(function(){
  
     count.innerHTML = num++;
  
     if(num == 11){
        //关闭定时器
        clearInterval(timer);
     }
  
  },1000);
  
  console.log(timer); //1
  ```

#### 系统对话框

- 浏览器通过 alert() 、 confirm() 和 prompt() 方法可以调用系统对话框向用户显示消息。 
- 它们的外观由操作系统及（或）浏览器设置决定，而不是由 CSS 决定。 
- 显示系统对话框时会导致程序终止，当关闭对话框程序会恢复执行。

1.alert

alert()接收一个字符串并显示给用户。调用alert()方法会向用户显示一个包含一个确认按钮的对话框。例如：alert("Hello World");

![alert](https://raw.githubusercontent.com/weixiaoyun/Images/JavaScript/alert.png)

2.confirm

confirm和alert类似，只不过confirm弹出的对话框有一个确认和取消按钮。用户可以通过按钮来确认是否执行操作。

例如：confirm('你确定吗？');

这个函数的执行会返回一个布尔值，如果选择确定则返回true，如果点击取消则返回false。

![confirm](https://raw.githubusercontent.com/weixiaoyun/Images/JavaScript/confirm.png)

3.prompt

prompt会弹出一个带输入框的提示框，并可以将用户输入的内容返回。

它需要两个值作为参数：

- 显示的提示文字
- 文本框中的默认值

例子：prompt('你的年龄是？','18');

![prompt](https://raw.githubusercontent.com/weixiaoyun/Images/JavaScript/prompt.png)

### 2.navigator对象

- 代表的当前浏览器的信息，通过该对象可以来识别不同的浏览器。navigator 对象包含了浏览器的版本、浏览器所支持的插件、浏览器所使用的语言等各种与浏览器相关的信息。

- 由于历史原因，Navigator对象中的大部分属性都已经不能帮助我们识别浏览器了

- 一般我们只会使用userAgent来判断浏览器的信息，userAgent是一个字符串，这个字符串中包含有用来描述浏览器信息的内容，不同的浏览器会有不同的userAgent：

   - 火狐的userAgent
     Mozilla/5.0 (Windows NT 6.1; WOW64; rv:50.0) Gecko/20100101 Firefox/50.0

   - Chrome的userAgent
     Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/52.0.2743.82 Safari/537.36

   - IE8
     Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.1; WOW64; Trident/7.0; SLCC2; .NET CLR 2.0.50727; .NET CLR 3.5.30729; .NET CLR 3.0.30729; Media Center PC 6.0; .NET4.0C; .NET4.0E)

   - IE9
     Mozilla/5.0 (compatible; MSIE 9.0; Windows NT 6.1; WOW64; Trident/7.0; SLCC2; .NET CLR 2.0.50727; .NET CLR 3.5.30729; .NET CLR 3.0.30729; Media Center PC 6.0; .NET4.0C; .NET4.0E)

   - IE10
     Mozilla/5.0 (compatible; MSIE 10.0; Windows NT 6.1; WOW64; Trident/7.0; SLCC2; .NET CLR 2.0.50727; .NET CLR 3.5.30729; .NET CLR 3.0.30729; Media Center PC 6.0; .NET4.0C; .NET4.0E)

   - IE11
     Mozilla/5.0 (Windows NT 6.1; WOW64; Trident/7.0; SLCC2; .NET CLR 2.0.50727; .NET CLR 3.5.30729; .NET CLR 3.0.30729; Media Center PC 6.0; .NET4.0C; .NET4.0E; rv:11.0) like Gecko

```
var ua = navigator.userAgent;

console.log(ua);

if(/firefox/i.test(ua)){
   alert("你是火狐！！！");
}else if(/chrome/i.test(ua)){
   alert("你是Chrome");
}else if(/msie/i.test(ua)){
   alert("你是IE浏览器~~~");
}else if("ActiveXObject" in window){
   alert("你是IE11");
}
```

在IE11中已经将微软和IE相关的标识都已经去除了，所以我们基本已经不能通过UserAgent来识别一个浏览器是否是IE了

如果通过UserAgent不能判断，还可以通过一些浏览器中特有的对象，来判断浏览器的信息；比如：ActiveXObject

```
if("ActiveXObject" in window){
   alert("你是IE，我已经抓住你了~~~");
}else{
   alert("你不是IE~~~");
}
```

### 3.history对象

history 对象保存着用户上网的历史记录，从窗口被打开的那一刻算起。可以用来操作浏览器向前或向后翻页

**go()：**使用 go() 方法可以在用户的历史记录中任意跳转，可以向后也可以向前。

- 可以用来跳转到指定的页面
- 它需要一个整数作为参数
   1:表示向前跳转一个页面 相当于forward()
   2:表示向前跳转两个页面
   -1:表示向后跳转一个页面
   -2:表示向后跳转两个页面

```
history.go(-2);
```

**back()：**向后跳转；可以用来回退到上一个页面，作用和浏览器的回退按钮一样

```
history.back();
```

**forward()：**向前跳转；可以跳转下一个页面，作用和浏览器的前进按钮一样

```
history.forward();
```

### 4.Location对象

location对象中封装了浏览器的地址栏的信息，提供了与当前窗口中加载的文档有关的信息，还提供了一些导航功能。 

- href属性：href属性可以获取或修改当前页面的完整的URL地址，使浏览器跳转到指定页面
- assign() 方法：所用和href一样，使浏览器跳转页面，新地址错误参数传递到assign ()方法中
- replace()方法：功能一样，只不过使用replace方法跳转地址不会体现到历史记录中
- reload() 方法：用于强制刷新当前页面

如果直接打印location，则可以获取到地址栏的信息（当前页面的完整路径）：

```
alert(location);
```

如果直接将location属性修改为一个完整的路径，或相对路径，则我们页面会自动跳转到该路径，并且会生成相应的历史记录

```
location = "http://www.baidu.com";
location = "01.BOM.html";
```

assign()：用来跳转到其他的页面，作用和直接修改location一样

```
location.assign("http://www.baidu.com");
```

reload()：
   - 用于重新加载当前页面，作用和刷新按钮一样
   - 如果在方法中传递一个true，作为参数，则会强制清空缓存刷新页面

```
location.reload(true);
```

replace()：可以使用一个新的页面替换当前页面，调用完毕也会跳转页面，不会生成历史记录，不能使用回退按钮回退

```
location.replace("01.BOM.html");
```

### 5.screen对象

screen 对象基本上只用来表明客户端的能力，其中包括浏览器窗口外部的显示器的信息，如像素宽度和高度等。 该对象作用不大，我们一般不太使用。

### 6.document

document对象也是window的一个属性，这个对象代表的是整个网页的文档对象。我们对网页的大部分操作都需要以document对象作为起点。