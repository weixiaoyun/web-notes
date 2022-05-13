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