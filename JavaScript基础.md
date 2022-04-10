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

#### if语句

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