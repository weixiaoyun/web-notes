# JS常用API

## 一、Array

### new Set()

数组去重

```
const arr = [3,4,4,5,4,6,5,7];
console.log(new Set(arr)); // {3,4,5,6,7}
const a = Array.from(new Set(arr)) // [3, 4, 5, 6, 7]
//或者
const a = [...new Set(arr)]//推荐
```

### new Array()

创建一个定长数组

```
var arr1 = new Array(5);//[空属性 * 5]
var arr2 = new Array(5).fill('')//['','','','','']
var arr3 = new Array(2)
for (let i = 0; i < 2; i++){
    arr3[i] = new Array(2)
}//创建二维数组
console.log(arr3)//[[空属性*2]， [空属性*2]]
```

或者传递多个参数作为数组中每个item的值：

```
var arr2 = new Array(10,20,30);
console.log(arr2);  //[10, 20, 30]

var arr3 = new  Array([1,2,3],[4,5,6])
console.log(arr3); //[[1,2,3], [4,5,6]]
```

### from()

用于通过拥有 length 属性的对象或可迭代的对象来返回一个数组。

如果对象是数组返回 true，否则返回 false

```
Array.from(object, mapFunction, thisValue)
```

| 参数          | 描述                                        |
| ------------- | ------------------------------------------- |
| *object*      | 必需，要转换为数组的对象。                  |
| *mapFunction* | 可选，数组中每个元素要调用的函数。          |
| *thisValue*   | 可选，映射函数(mapFunction)中的 this 对象。 |

```
var setObj = new Set(["a", "b", "c"]);
var objArr = Array.from(setObj);
console.log(objArr[1] == "b");  // true
var arr = Array.from([1, 2, 3], x => x * 10);
console.log(arr)
// arr[0] == 10;
// arr[1] == 20;
// arr[2] == 30;
```

Array.from() 可以将一个伪数组转换为数组，如下所示：

```
let obj = {
    '0': 1,//'0':1中的'0'将转换为下标0,下面的key同理
    '1': 2,
    '2':3,
    'length': 4,//length规定了转换的数组有多长
}
let newObj= Array.from(obj, item => {return item})
console.log(newObj); //输出:[ 1, 2, 3, undefined ]
```

```
let obj = {
    'a': 1,
    'b': 2,
    'c':3,
    'length': 4,
}
let newObj= Array.from(obj, item => {return item})
console.log(newObj); //key值不按常理出牌所以无效，但规定了 length 所以输出: 四个 undefined
```

```
let obj = {
    '0': 1,
    '3': 2,
    'length': 4,
}
let newObj= Array.from(obj, item => {return item})
console.log(newObj); // 输出:[ 1, undefined, undefined, 2 ]
```

### isArray()

isArray() 方法用于判断一个对象是否为数组。

如果对象是数组返回 true，否则返回 false。

语法：*Array.isArray(obj)*

| 参数  | 描述                 |
| ----- | -------------------- |
| *obj* | 必需，要判断的对象。 |

```
var fruits = ["Banana", "Orange", "Apple", "Mango"];
console.log(Array.isArray(fruits)) //true
```

```
const arr = [3,4,4,5,4,6,5,7];
console.log(Array.isArray(arr)) // true
```



### sort()

对数组元素进行排序（改变原数组）

```
const arr = [1,2,3,4,5,6];
console.log(arr.sort((a,b)=>a-b)) // [1,2,3,4,5,6] 大小正序
cosole.log(arr.sort((a,b)=>b-a))// [6,5,4,3,2,1] 大小倒序
//不可以进行运算的则比较编码大小  'b' > 'a' => true
```

sort() 方法用于对数组的元素进行排序。

排序顺序可以是字母或数字，并按升序或降序。

默认排序顺序为按字母升序。

**语法：**    *array*.sort(*sortfunction*)

| 参数           | 描述                             |
| :------------- | :------------------------------- |
| *sortfunction* | 可选。规定排序顺序。必须是函数。 |

```
var str = ['ranko', 'kotori', 'ruby', 'rank']
var fruits = ["Banana", "Orange", "Apple", "Mango"]
fruits.sort();//['Apple', 'Banana', 'Mango', 'Orange']
str.sort((a, b)=> {
    var i = 0;
    while (a.charCodeAt(i) || b.charCodeAt(i)){
        if(!a.charCodeAt(i)){
            return -1
        } else if(!b.charCodeAt(i)){
            return 1
        } else  if(a.charCodeAt(i)!==b.charCodeAt(i)){
            return a.charCodeAt(i) - b.charCodeAt(i)
        } else {
            i++
        }
    }//模拟字典升序
}); //['kotori', 'rank', 'ranko', 'ruby']
```

### reverse()

反转数组中的元素（改变原数组）

```
const arr = [3,4,4,5,4,6,5,7];
console.log(arr.reverse());  // [7, 6, 5, 5, 4, 4, 4, 3]
```

### delete

删除一个数组成员，会形成空位，并不会影响length属性（改变原数组），同样适用于对象

```
//数组
const arr = [0,1,2];
delete arr[1];
console.log(arr); // [0, empty, 2]

//对象
const obj = {name: '谢大脚',age: '18',sex: '女'};
delete obj.sex;
console.log(obj); // {name: "谢大脚", age: "18"}
```

### shift()

把数组中的第一个元素从其中删除，并返回第一个元素的值（改变原数组）

```
const arr = [0,1,2];
const a = arr.shift(); // 0
console.log(arr); // [1, 2]
```

### unshift()

向数组的起始处添加一个或多个元素，并返回新的长度（改变原数组）

```
const arr = [3,4,4,5,4,6,5,7];
const a = arr.unshift(8);
console.log(a); // 9(a为返回的数组的新长度)
console.log(arr); // [8, 3, 4, 4, 5, 4, 6, 5, 7]
```

### push()

在数组的末端添加一个或多个元素，并返回添加新元素后的数组长度（改变原数组）

```
const arr = [3,4,4,5,4,6,5,7];
const a = arr.push(8,9);
console.log(a); // 10(a为返回的数组的新长度)
console.log(arr); // [3, 4, 4, 5, 4, 6, 5, 7, 8, 9]
```

### pop()

删除数组的最后一个元素并返回删除的元素（改变原数组）

```
const arr = [3,4,4,5,4,6,5,7];
const a = arr.pop();
console.log(a); //7(a为返回的数组的新长度)
console.log(arr)//[3, 4, 4, 5, 4, 6, 5]
```

### fill()

fill() 方法用于将一个固定值替换数组的元素。语法：array.fill(value, start, end)

```
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.fill("Runoob", 2, 4);
console.log(fruits)  //["Banana", "Orange", "Runoob", "Runoob"]
```

### toString()

可把值转换为字符串

```
const arr = [3,4,4,5,4,6,5,7];
var num = 15
//number.toString(radix)，radix：可选。规定表示数字的基数，是 2 ~ 36 之间的整数
console.log(arr.toString()); // 3,4,4,5,4,6,5,7
console.log(num.toString()); //15
console.log(num.toString(2)); //1111
console.log(num.toString(8)); //17
console.log(num.toString(16)); //f
```

### concat()

在原始数据尾部添加另外数据组成新数据（字符串也适用）。

不考虑 ie 的话 直接用扩展运算…即可

```
//数组
const a = [1,2,3];
const b = [4,5];
const c = a.concat(b); // [1, 2, 3, 4, 5]
console.log(c)
//字符串
const x = 'abc';
const y = 'def';
const z = x.concat(y); // abcdef
console.log(z)
```

### join()

以参数作为分隔符，将所有参数组成一个字符串返回（默认逗号分隔）。借助join()将数组转化为字符串

```
const arr = [3,4,4,5,4,6,5,7];
console.log(arr.join('-')); // 3-4-4-5-4-6-5-7
console.log(arr.join('')) //34454657
```

### slice(start, end)

用于提取原来数组的一部分，会返回一个提取的新数组，原数组不变（字符串适用，不包括 end)。

```
//数组
const arr = [3,4,4,5,4,6,5,7];
const a = arr.slice(2, 5); // [4, 5, 4]
console.log(a)

//字符串
const x = 'abcdefgh';
const y = x.slice(3, 6); // def
console.log(y)
```

### splice()

用于删除原数组的一部分，并且可以在删除的位置添加新的数组成员，返回值是被删除的数组元素。（改变原数组）

splice（t, v, s）t: 被删除元素的起始位置；v：被删除元素个数；s:s 以及后面的元素为被插入的新元素。

```
const arr = [3,4,4,5,4,6,5,7];
const a = arr.splice(3, 2, 12); // [5, 4]
console.log(arr); // [3, 4, 4, 12, 6, 5, 7]
```

### map()

依次遍历数组成员，根据遍历结果返回一个新数组。（不会改变原始数组）。

```
const arr = [3,4,4,5,4,6,5,7];
const a = arr.map(item => item*2) // [6, 8, 8, 10, 8, 12, 10, 14]
console.log(a)
```

### forEach()

 map 方法类似，遍历数组，区别是无返回值。

```
const arr = [3,4,4,5,4,6,5,7];
arr.forEach(function(item,index,arr) {
    console.log(item,index,arr)
})
//item（必选）为当前元素，index（可选）为当前元素的索引值，arr（可选）当前元素所属的数组对象。
```

### for in()

跟 map 方法类似，遍历对象或者数组。

但值得注意的是 for in 循环返回的值都是数据结构的键值名。遍历对象返回的对象的 key 值，遍历数组返回的数组的下标 (key)。

```
// 对象
const obj = {a: 123, b: 12, c: 2 };
for (let a in obj) {
    console.log(a)
}
/*a
b
c*/
//数组
const arr = [3,4,4,5];
for(let a in arr) {
    console.log(a)
}
/*0
1
2
3*/
```

### for of()

**`for...of`语句**在[可迭代对象](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Iteration_protocols)（包括 [`Array`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array)，[`Map`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Map)，[`Set`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Set)，[`String`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String)，[`TypedArray`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/TypedArray)，[arguments](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions_and_function_scope/arguments) 对象等等）上创建一个迭代循环，调用自定义迭代钩子，并为每个不同属性的值执行语句

**语法：**

```
for (variable of iterable) {
    //statements
}
```

```
var arr = ['A', 'B', 'C']
for(let x of arr){
    console.log(x)
}
//A
//B
//C
```

### filter（）

一个过滤方法，参数是一个函数，所有的数组成员依次执行该函数，返回结果为 true 的成员组成一个新数组返回。（不会改变原始数组）。

```
const arr = [3,4,4,5,4,6,5,7];
const a = arr.filter(item => item % 3 > 1);
console.log(a); // [5, 5]
```

### some()&every()

这两个方法类似于 “断言”（assert），用来判断数组成员是否符合某种条件。

```
const arr = [3,4,4,5,4,6,5,7];
console.log( arr.some( function( item, index, array ){
    console.log( 'item=' + item + ',index='+index+',array='+array );
    return item > 3;
}));
//  item=3,index=0,array=3,4,4,5,4,6,5,7
//   item=4,index=1,array=3,4,4,5,4,6,5,7
//   true

console.log( arr.every( function( item, index, array ){
    console.log( 'item=' + item + ',index='+index+',array='+array );
    return item > 3;
}));
// item=3,index=0,array=3,4,4,5,4,6,5,7
//false
```

- #### some

  只要有一个item符合判断条件就为true，反之为false

- #### every

  必须全部item符合判断条件才为true，反之为false

### reduce（）

 依次处理数组的每个成员，最终累计成一个值。

 格式：

```php
reduce（() => (pre, cur, curIndex, arr), initialValue）
```

pre: 必填，累计变量；cur：必填，当前变量；curIndex: 可选，当前位置；arr: 可选，原数组；initialValue: 传递给函数的初始值。

```
var num = [65, 44, 12, 4]
num.reduce((pre, cur)=>{
    console.log(pre)//69 109 121
    return pre + cur
})
num.reduce((pre,cur)=>{
    console.log(pre) //10,75,119,131
    return pre + cur
}, 10)
```

### indexOf()

返回给定元素在数组中的第一次出现的位置，如果没有则返回 - 1 (同样适用于字符串)。

语法：*string*.indexOf(*searchvalue*,*start*)

| 参数          | 描述                                                         |
| :------------ | :----------------------------------------------------------- |
| *searchvalue* | 必需。规定需检索的字符串值。                                 |
| *start*       | 可选的整数参数。规定在字符串中开始检索的位置。它的合法取值是 0 到 string Object.length - 1。如省略该参数，则将从字符串的首字符开始检索。 |

```
const arr = [3,4,4,5,4,6,5,7];
console.log(arr.indexOf(4)) // 1
console.log(arr.indexOf('4'))  // -1

//字符串
const string = 'asdfghj';
console.log(string.indexOf('a')) // 0
```

### lastIndexOf()

返回给定元素在数组中最后一次出现的位置，没有返回 - 1 (同样适用于字符串)。

如果指定第二个参数 start，则在一个字符串中的指定位置从后向前搜索。

语法：*string*.lastIndexOf(*searchvalue*,*start*)

| 参数          | 描述                                                         |
| :------------ | :----------------------------------------------------------- |
| *searchvalue* | 必需。规定需检索的字符串值。                                 |
| *start*       | 可选的整数参数。规定在字符串中开始检索的位置。它的合法取值是 0 到 stringObject.length - 1。如省略该参数，则将从字符串的最后一个字符处开始检索。 |

```
const arr = [3,4,4,5,4,6,5,7];
console.log(arr.lastIndexOf(4)) //4
// 4(从左到右数最后出现的位置，字符串同理)
```

### flat()

简写为 flat（），接收一个数组，无论这个数组里嵌套了多少个数组，flat最后都会把其变成一个一维数组 (扁平化)。

flat(depth) 方法会递归到指定深度将所有子数组连接，并返回一个新数组, depth指定嵌套数组中的结构深度，默认值为1，不管多少层则可以用Infinity关键字作为参数。

```
const arr = [[1,2,3],[4,5,[6,7]]];
const a = arr.flat(1);// [1, 2, 3, 4, 5, [6,7]]
// const a = arr.flat(3);// [1, 2, 3, 4, 5, 6, 7]
console.log(a); 
```

### find()

返回符合传入测试（函数）条件的数组元素。

```
const arr = [3,4,4,5,4,6,5,7];
const a = arr.find(item => item > 3);
console.log(a); //4(find() 方法返回通过测试（函数内判断）的数组的第一个元素的值。)

const b = arr.find(item => item == 0);
console.log(b); //undefined(如果没有符合条件的元素返回 undefined)
```



## 二、String

### charAt()

用于返回指定位置的字符。

```
const str = 'hello guys';
console.log(str.charAt(3))  // 1
```

### charCodeAt()

用于返回指定位置的字符的 Unicode 编码。

```
const str = 'hello guys';
console.log(str.charCodeAt(3))  // 108
console.log('A'.charCodeAt(0))//65
```

### fromCharCode()

将 Unicode 编码转为一个字符。可接受一个指定的 Unicode 值，然后返回一个字符串。

String.fromCharCode(*n1*, *n2*, ..., *nX*)，参数为一个或多个 Unicode 值

```
console.log(String.fromCharCode(65)) //A
console.log(String.fromCharCode('A'.charCodeAt(0) + 1))//B
console.log(String.fromCharCode(72,69,76,76,79))//HELLO
```

### match()

用于在字符串内检索指定的值或找到一个或多个正则表达式的匹配，返回的是值而不是值的位置。

```
const str = 'hello guys';
console.log(str.match('guys'))  // ["guys"]

// 使用正则匹配字符串
const strs = '1.hello guys, 2.are you ok?';
console.log(strs.match(/\d+/g)) // ["1", "2"]
```

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

### replace()

替换匹配的字符串，只替换第一次找到的字符串。

```
const str = 'hello guys';
console.log(str.replace('guys', 'man'))  // hello man
```

借助正则表达式实现全局替换

```
var str="Mr Blue has a blue house and a blue car";
var n=str.replace(/blue/g,"red"); 
//Mr Blue has a red house and a red car
console.log(n)
```

### search()

用于检索与字符串匹配的子串，返回的是地址，与 indexOf() 的区别是 search 是强制正则的，而 indexOf 只是按字符串匹配的。

```
const str = 'hello guys';
console.log(str.search('guys'))  // 6
console.log(str.indexOf('guys'))  // 6
// 区别
const string = 'abcdefg.1234';
console.log(string.search(/\./)) // 7（转译之后可以匹配到 . 的位置）
console.log(string.indexOf(/\./)) // -1 （相当于匹配/\./，找不到则返回-1,只能匹配字符串）
```

### split()

将字符串切割成数组。可以借助split()实现字符串到数组的转换。

```
const str = 'hello guys';
console.log(str.split('')) // ["h", "e", "l", "l", "o", " ", "g", "u", "y", "s"] 
console.log(str.split('', 3)) //  ["h", "e", "l"]
```

### toLocaleLowerCase() & toLowerCase()

将字符串转换成小写。

```
const str = 'hello guys';
console.log(str.toLocaleLowerCase())  // hello guys
console.log(str.toLowerCase())  //  hello guys
```

### toLocaleUpperCase() & toUpperCase()

将字符串转换成大写。

```
const str = 'hello guys';
console.log(str.toLocaleUpperCase())  // HELLO GUYS
console.log(str.toUpperCase())  // HELLO GUYS
```

### substr()

用于从起始索引号提取字符串中指定数目的字符。

```
const str = 'hello guys';
console.log(str.substr(2))  // llo guys
console.log(str.substr(2, 7))  // llo guy
```

### substring()

用于提取字符串中两个指定索引号之间的字符。(与 slice() 和 substr() 方法不同的是，substring() 不接受负的参数。)

```
const str = 'hello guys';
console.log(str.substring(2))   // llo guys
console.log(str.substring(2, 7))  //  llo g
```

### trim()

去掉字符串两端的空格。不会改变原数组

```
const str = '    hello guys    ';
console.log(str.trim()) // hello guys(不会改变原数组)
```



## 三、JSON

### JSON.parse()

用于把字符串转化为对象。

```
const str = '{"name": "phoebe", "age": 20}';
const obj = JSON.parse(str)  // {name: "phoebe", age: 20}（object类型）
console.log(obj)
```

### JSON.stringify()

用于把对象转化为字符串。

```
const obj = {"name": "Tins", "age": 22};
const str = JSON.stringify(obj)  // {"name":"Tins","age":22}(string类型)
console.log(str)
```



## 四、Object

### Object.prototype.valueOf()

返回当前对象对应的值。（Object.valueOf（）相当于 Object.Prototype.ValueOf（））

我们创建一个取代 valueOf() 方法的函数，但是需要注意的是方法必须不能传入参数 。假设我们有个对象叫 ObjectrType 而我想为它创建一个 valueOf() 方法。下面的代码为 valueOf() 方法赋予了一个自定义函数:

```javascript
ObjectrType.prototype.valueOf = function() { return customValue; };
```

有了这样的一个方法，下一次每当 ObjectrType 要被转换为原始类型值时，JavaScript 在此之前会自动调用自定义的 valueOf() 方法。valueOf() 方法一般都会被 JavaScript 自动调用，但我们也可以像下面代码那样自己调用：

```css
ObjectrType.valueOf()
```

valueOf 同样适用于 string，number， symbol，boolean，date。

```
var fruits = ["Banana", "Orange", "Apple", "Mango"];
var v=fruits.valueOf();//['Banana', 'Orange', 'Apple', 'Mango']
console.log(v)
```

### Object.toString()

返回当前对象对应的字符串形式

```
function Dog(name) {
    this.name = name;
}

const dog1 = new Dog('Gabby');

Dog.prototype.toString = function dogToString() {
    return '' + this.name;
}

console.log(dog1.toString());  // Gabby
```

### Object.prototype.toLocaleString()

返回当前对象对应的模块字符串。

```
let foo = {};
console.log(foo.toLocaleString()); // "[object Object]"
```

### Object.prototype.isPrototypeOf()

判断当前对象是否为另一个对象的原型。语法：Object.prototype.isPrototypeOf(targetObj)

```
const arr = [];

Array.prototype.isPrototypeOf(arr); // true

// 修改obj的原型
Object.setPrototypeOf(arr, String.prototype);
console.log(Array.prototype.isPrototypeOf(arr)); // false
console.log(String.prototype.isPrototypeOf(arr)); // true
```

### Object.prototype.hasOwnProperty()

判断某个属性是否为当前对象自身的属性，还是继承自原型对象的属性，并返回一个布尔值。

语法：Object.prototype.hasOwnProperty(prop)

```
let obj = {};// 定义一个object实例
obj.prop1 = 'value1'; // prop1是一个自有属性
obj.constructor.prototype.prop2 = 'value2'; // prop2是一个原型链属性
// 无论自有属性还是原型链属性，我们都可以访问到
console.info(obj.prop1); // value1
console.info(obj.prop2); // value2
// 使用`hasOwnProperty()`方法判断属性是否为自有属性
console.log(obj.hasOwnProperty('prop1')); // true
console.log(obj.hasOwnProperty('prop2')); // false
```

### Object.prototype.PropertyIsEnumerable()

判断某个属性是否可枚举。

语法：Object.prototype.propertyIsEnumerable(prop)

```
const obj = { name: 'ecmaer'};

Object.getOwnPropertyDescriptor(obj, 'name').enumerable; // true
obj.propertyIsEnumerable('name'); // true

// 将属性name设置成不可枚举
Object.defineProperty(obj, 'name', {enumerable: false});
obj.propertyIsEnumerable('name'); // false

for(let i in obj){
    console.info(obj[i]); // 没有遍历出'ecmaer'
}
```

### typeOf()

typeof 可用来检测数据类型：需要注意的是 typeof 无法区分 null、Array 和 通常意义上的 object。

```
typeof 123 //number
typeof '123' //string
typeof true // boolean
typeof false //boolean
typeof undefined // undefined
typeof Math.abs // function
typeof function () {} // function




// 当遇上`null`、`Array`和通常意义上的`object`,都会返回 object
typeof null // object
typeof [] // object（所以判断数组时可以使用Array.isArray(arr)）
typeof {} // object




// 当数据使用了new关键字和包装对象以后，数据都会变成Object类型，不加new关键字时会被当作普通的函数处理。
typeof new Number(123); //'object'
typeof Number(123); // 'number'


typeof new Boolean(true); //'object'
typeof Boolean(true); // 'boolean'


typeof new String(123); // 'object'
typeof String(123); // 'string'
```

### instanceOf()

instanceOf（）运算符用于检测构造函数的 prototype 属性是否出现在某个实例对象的原型链。

```
function Car(make, model, year) {
    this.make = make;
    this.model = model;
    this.year = year;
}
const auto = new Car('Honda', 'Accord', 1998);

console.log(auto instanceof Car); // true
console.log(auto instanceof Object); // true
```

### Object.prototype.toString() （推荐）

可以精准的判断对象类型。

对于 array、null、object 来说，其关系错综复杂，使用 typeof 都会统一返回 object 字符串，要想区别对象、数组、函数单纯使用 typeof 是不行的，想要准确的判断对象类型，推荐使用 Object.Prototype.toString（）, 它可以判断某个对象值属于哪种内置类型。

```
const arrs = [1,2,3];
console.log(arrs)
console.log(typeof arrs) // object
console.log(Object.prototype.toString.call(arrs))  // [object Array]
```

### Object.keys()

`Object.keys` 返回一个所有元素为字符串的数组，其元素来自于从给定的`object`上面可直接枚举的属性。这些属性的顺序与手动遍历该对象属性时的一致。

```
var arr = ['a', 'b', 'c'];
console.log(Object.keys(arr)); // console: ['0', '1', '2']

// array like object
var obj = { 0: 'a', 1: 'b', 2: 'c' };
console.log(Object.keys(obj)); // console: ['0', '1', '2']

// array like object with random key ordering
var anObj = { 100: 'a', 2: 'b', 7: 'c' };
console.log(Object.keys(anObj)); // console: ['2', '7', '100']

// getFoo is a property which isn't enumerable
var myObj = Object.create({}, {
    getFoo: {
        value: function () { return this.foo; }
    }
});
myObj.foo = 1;
console.log(Object.keys(myObj)); // console: ['foo']
```

### Object.create()

**`Object.create()`**方法创建一个新对象，使用现有的对象来提供新创建的对象的__proto__。

```
const person = {
    isHuman: false,
    printIntroduction: function() {
        console.log(`My name is ${this.name}. Am I human? ${this.isHuman}`);
    }
};

const me = Object.create(person);

me.name = 'Matthew'; // "name" is a property set on "me", but not on "person"
me.isHuman = true; // inherited properties can be overwritten

console.log(me.__proto__) //{isHuman: false, printIntroduction: ƒ}
me.printIntroduction();
// expected output: "My name is Matthew. Am I human? true"
```

### call & apply & bind

- #### call

  直接调用该执行函数，在执行的时候，将函数内部的作用域绑定到指定的作用域。（call() 方法接受若干个参数的列表）

  ```
  const arr = [2,5,4,7,6]
  const a = Function.prototype.apply.call(Math.max, null,arr)
  const b = Function.prototype.call.call(Math.max, null,...arr)
  console.log(a)  // 7
  console.log(b)  //7
  console.log(Math.max(...arr)) //7
  // Function.prototype.apply.call( fn, thisArg, args ) 这个调用其实等价于 fn.apply( thisArg, args ) 这个调用。
  ```

- #### apply

  直接调用该执行函数，在执行的时候，将函数内部的作用域绑定到指定的作用域。

  call() 是 apply() 的一颗语法糖，作用和 apply() 一样，同样可实现继承，唯一的区别就在于 call() 接收的是参数列表，而 apply() 则接收参数数组。

  ```
  const arr = [7,2,5,4,6]
  const a = Function.prototype.call.apply(Math.max, arr)
  console.log(a)  // 6
  //Function.prototype.call.apply( fn ,args) 这个调用其实等价于 fn.call( arr[1], splice(1,arr.length) ) 这个调用。
  
  //如果apply的第二个参数是个null，会返回-Infinity
  const b = Function.prototype.call.apply(Math.max, null, arr)
  console.log(b)  // -Infinity
  
  const c = Function.prototype.apply.apply(Math.max, [null,arr]) //7
  console.log(c)
  
  const d = Function.prototype.call.apply(Math.max, [null,...arr]) //7
  console.log(d)
  ```

- #### bind

  创建一个新的函数的引用，并绑定到一个作用域特定作用域上，同时支持传参。

  bind 则和 call 的用法差不多，唯一区别是，call 和 apply 会立刻调用函数(返回函数的返回值)，bind 只是绑定 this（返回的是函数）。

  格式为：bind(作用域参数，参数 1，参数 2)

  ```
  const fruits = {
      name: "apple",
      getOtherFriut: function() {
          return this.name;
      }
  }
  
  const color = {
      name: " is red"
  }
  
  const fruitColor = fruits.getOtherFriut.bind(color)
  console.log(fruitColor()) //is red
  ```

- #### 相似之处

  - 都是用来改变函数的 this 对象
  - 第一个参数都是 this 要指向的对象
  - 都可利用后继参数传参
  - 都可以用来代替另一个对象调用一个方法，将一个函数的对象上下文从初始的上下文改变为由 thisObj 指定的新对象

- #### 区别

  - bind() 是返回一个新函数，供以后调用，而 apply() 和 call() 是立即调用
  - call() 和 apply() 唯一区别是参数不一样，call() 是 apply() 的语法糖

- #### 选择使用

  - 如果不需要关心具体有多少参数被传入函数，选用 apply()
  - 如果确定函数可接收多少个参数，并且想一目了然表达形参和实参的对应关系，用 call()
  - 如果想要将来再调用方法，不需立即得到函数返回结果，则使用 bind()

## 五、Set()相关

set本质上是一个object

### Set.add()

向 Set 添加新元素

```
const a = "a";
const b = "b";
const c = "c";
// 创建 Set
const letters = new Set();
const newletters = new Set(["d","e","f"]);

console.log(newletters) //{'d', 'e', 'f'}
// Add the values to the Set
letters.add(a);
letters.add(b);
letters.add(c);
console.log(letters)/*可以理解为{a, b, c}*/
console.log(typeof letters); //object
console.log(letters instanceof Set) //true
```

### Set.has()

如果值存在则返回 true

```
console.log(letters.has('a')) //true
```

### Set.delete()

删除由其值指定的元素：

```
letters.delete('a')
console.log(letters.has('a')) //false
console.log(letters); //{'b', 'c'}
```

### Set.keys()

返回 Set 对象中值的数组

```
console.log(letters.keys()) /*{'a', 'b', 'c'}*/
console.log(typeof letters.keys()) //object
console.log(letters.keys() instanceof Array) //false
```

### Set.size()

 返回元素计数

```
console.log(letters.size) //3
```

### Set.forEach()

 为每个元素调用回调

### Set.clear()

从 Set 中删除所有元素

```
letters.clear()
console.log(letters.keys())//{}
```

## 六、Map()相关

可以将 Array 传递给 new Map() 构造函数：

```
const apples = {name: 'Apples'};
const bananas = {name: 'Bananas'};
const oranges = {name: 'Oranges'};

// 创建新的 Map
const fruits = new Map([
[apples, 500],
    [bananas, 300],
    [oranges, 200]
]);
console.log(fruits)//{{name: 'Apples'} => 500, {name: 'Bananas'} => 300, {name: 'Oranges'} => 200}
```

### Map.set()

为 Map 对象中的键设置值:

```
const apples = {name: 'Apples'};
const bananas = {name: 'Bananas'};
const oranges = {name: 'Oranges'};

// 创建新的 Map
const fruits = new Map();

// Add new Elements to the Map
fruits.set(apples, 500);
fruits.set(bananas, 300);
fruits.set(oranges, 200);
console.log(fruits) //{{name: 'Apples'} => 500, {name: 'Bananas'} => 300, {name: 'Oranges'} => 200}
```

### Map.get()

get() 方法获取 Map 中键的值：

```
console.log(fruits.get(apples));//500
```

```
fruits.get("apples");  // 返回 undefined
```

### Map.entries()

返回 Map 对象中键/值对的数组：

```
console.log(fruits.entries()) //MapIterator {{name: 'Apples'} => 500, {name: 'Bananas'} => 300, {name: 'Oranges'} => 200}
```

### Map.keys()

返回 Map 对象中键的数组：

```
console.log(fruits.keys()) //MapIterator {{name: 'Apples'}, {name: 'Bananas'}, {name: 'Oranges'}}
```

### Map.values()

返回 Map 对象中值的数组：

```
console.log(fruits.values()) //MapIterator {500, 300, 200}
```

### Map.has()

如果 Map 中存在键，则 Map.has() 返回 true：

```
console.log(fruits.has(apples))//true
```

### Map.size

Map.size 返回 Map 中元素的数量：

```
console.log(fruits.size)//3
```

### Map.delete()

Map.delete() 删除 Map 元素：

```
fruits.delete(apples)
console.log(fruits) //{{name: 'Bananas'} => 300, {name: 'Oranges'} => 200}
```

### Map.clear()

Map.clear() 从 Map 中移除所有元素：

```
fruits.clear()
console.log(fruits) //Map(0) {size: 0}
```

### Map.forEach()

为每个键/值对调用回调

## 七、Math相关

- Math.ceil (): 对数进行上舍入（天花板函数）

- Math.floor (): 对数进行下舍入（地板函数）

- Math.max (x,y): 返回 x,y 中的最大值

  - Math.max(*n1*,*n2*,*n3*,...,nX)，在 ECMASCript v3 之前，该方法只有两个参数。

  - 返回参数中最大的值。如果没有参数，则返回 -Infinity。如果有某个参数为 NaN，或是不能转换成数字的非数字值，则返回 NaN。

    ```
    var c = [1,8,10,21,14,22,51,66,32,42,11];
    var a = Math.max(5,10);
    var b = Math.max(0,150,30,20,38);
    var d = Math.max(...c);
    console.log(a); //10
    console.log(b); //150
    console.log(d); //66
    ```

- Math.min (x,y): 返回 x,y 中的最小值

- Math.pow (x,y): 返回 x 的 y 次方

- Math.random () : 返回 0-1（不包含） 之间的随机数

  min到max之间的随机数

  ```
  function getRndInteger(min, max) {
      return Math.floor(Math.random() * (max - min) ) + min;
  }
  console.log(getRndInteger(10,20))
  ```

- Math.round (x): 四舍五入

- Math.abs (x): 返回数的绝对值

- Math.acos (x): 返回数的反余弦值

- Math.asin (x): 返回数的反正弦值

- Math.atan (x): 返回数的反正切值

- Math.atan2 (y,x): 返回由 x 轴到点（x，y）的角度（以弧度为单位）

- Math.cos (x): 返回数的余弦值

- Math.exp (e): 返回 e 的指数

- Math.log (x): 返回数的自然对数（以 e 为底数）

- Math.sin (x): 返回数的正弦值

- Math.sqrt (x): 返回数的平方根

- Math.tan (x): 返回角的正切值

- Math.toSource (): 返回该对象的源代码

- Math.valueOf (): 返回 Math 对象的原始值

## 八、数据转换

### 1.转换函数

#### parseInt()

parseInt(string, radix)可解析一个字符串，并返回一个整数:

string(必须)，要被解析的字符串；radix（可选），表示要解析的数字的基数。该值介于 2 ~ 36 之间

- 如果 string 以 "0x" 开头，parseInt() 会把 string 的其余部分解析为十六进制的整数。

- 如果 string 以 0 开头，那么 ECMAScript v3 允许 parseInt() 的一个实现把其后的字符解析为八进制或十六进制的数字。

- 如果 string 以 1 ~ 9 的数字开头，parseInt() 将把它解析为十进制的整数。

  ```
  console.log(parseInt("10")); //10
  console.log(parseInt("10.33")) //10
  console.log(parseInt("34 45 66")) //34
  console.log(parseInt(" 60 ")) //60
  console.log(parseInt("40 years")) //40
  console.log(parseInt("10",10)) //10
  console.log(parseInt("010")) //10
  console.log(parseInt("10",8)) //8
  console.log(parseInt("0x10")) //16
  console.log(parseInt("10",16)) //16
  ```

 **注意**：

-  只有字符串中的第一个数字会被返回
-  开头和结尾的空格是允许的
- 如果字符串的第一个字符不能被转换为数字，那么 parseInt() 会返回 NaN
- 在字符串以"0"为开始时旧的浏览器默认使用八进制基数。ECMAScript 5，默认的是十进制的基数

#### parseFloat()

parseFloat(string)函数可解析一个字符串，并返回一个浮点数：

string（必须），要被解析的字符串

**注意事项同parseInt()**

```
console.log(parseFloat("10")) //10
console.log(parseFloat("10.33")) //10.33
console.log(parseFloat("34 45 66")) //34
console.log(parseFloat(" 60 ")) //60
console.log(parseFloat("40 years")) //40
console.log(parseFloat("He was 40")) //NaN
```

### 2.强制类型转换

#### Boolean()

Boolean 对象用于转换一个不是 Boolean 类型的值转换为 Boolean 类型值 (true 或者false)

```
console.log(Boolean(""));   //false   –   empty   string
console.log(Boolean("hi"));   //true   –   non-empty   string
console.log(Boolean(100));   //true   –   non-zero   number
console.log(Boolean(null));   //false   -   null
console.log(Boolean(0));   //false   -   zero
console.log(Boolean(new Object()));   //true   –   object
```

#### Number()

强制类型转换与parseInt()和parseFloat()方法的处理方式相似，只是它转换的是整个值，而不是部分值

```
console.log(Number(false)) //0
console.log(Number(true)) //1
console.log(Number(undefined)) //NaN
console.log(Number(null)) //0
console.log(Number("5.5 ")) //5.5
console.log(Number("56 ")) //56
console.log(Number("5.6.7 ")) //NaN
console.log(Number(new Object())) //NaN
console.log(Number(100)) //100
```

#### String()

```
console.log(String(null));   //"null"
var oNull = null;
console.log(oNull.toString());   //won't   work,   causes   an   error
```

## 九、其他

#### isNaN()

isNaN(value)：value,必须要检测的值。检查其参数是否是非数字值

```
console.log(isNaN(123));//false
console.log(isNaN(-1.23));//false
console.log(isNaN(5-2));//false
console.log(isNaN(0));//false
console.log(isNaN("Hello"));//true
console.log(isNaN("2005/12/12"));//true
```
