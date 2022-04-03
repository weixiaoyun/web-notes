# HTML5 + CSS3

网页分成三个部分：

- 结构(HTML)

- 表现(CSS)

-  行为(JavaScript)

## 一、HTML

### 1.标签和注释

#### HTML的注释

注释中的内容会被浏览器所忽略，不会在网页中直接显示，但是可以在源码中查看注释，注释用来对代码进行解释说明的，开发中要养成良好的编写注释的习惯，注释要求简单明了

- 注释还可以将一些不希望显示的内容隐藏


- 注释不能嵌套

  ```
  <!--
        <!-- 
           我是注释中的注释 注释不能嵌套
        -->
  
  -->
  ```

#### 标签

标签一般成对出现，但是也存在一些自结束标签：

```
<img>
<img />
<input>
<input />
```

### 2.属性

在标签中（开始标签或自结束标签）可以设置属性

- 属性是一个名值对（x=y）
- 属性用来设置标签中的内容如何显示

- 属性和标签名或其他属性应该使用空格隔开


- 属性不能瞎写，应该根据文档中的规定来编写

   有些属性有属性值，有些没有。如果有属性值，属性值应该使用引号引起来

  ```
  <h1>这是我的<font color="red" size='3'>第三个</font>网页！</h1>
  ```

### 3.文档声明

#### 网页的版本

-  HTML4
-  XHTML2.0
- HTML5
-  ...

#### 文档声明（doctype）

   - 文档声明用来告诉浏览器当前网页的版本

   - html5的文档声明

     ```
     <!doctype html>
     <!Doctype HTML>
     ```

### 4.进制

#### 十进制（日常使用）

   - 特点：满10进1
   - 计数：0 1 2 3 4 5 6 7 8 9 10 11 12 13 ... 19 20
   - 单位数字：10个 （0-9）

#### 二进制（计算机底层的进制）

   - 特点：满2进1
   - 计数：0 1 10 11 100 101 110 111
   - 单位数字：2个 （0-1）
   - 扩展：
      - 所有数据在计算机底层都会以二进制的形式保存
      - 可以将内存想象为一个有多个小格子组成的容器，每一个小格子中可以存储一个1或一个0
         这一个小格子在内存中被称为1位（bit）
         
         8bit = 1byte(字节)
         1024byte = 1kb(千字节)
         1024kb = 1mb(兆字节)
         1024mb = 1gb(吉字节)
         1024gb = 1tb(特字节)
         1024tp = 1pb

#### 八进制(很少用)

   - 特点：满8进1
   - 计数： 0 1 2 3 4 5 6 7 10 11 12 ... 17 20
   - 单位数字：8个 （0-7）

#### 十六进制(一般显示一个二进制数字时，都会转换为十六进制)

   - 特点：满16进1
   - 计数：0 1 2 3 4 5 6 7 8 9 a b c d e f 10 11 12 ... 1a 1b 1c 1d 1e 1f 20 ..
   - 单位数字：16个（0-f）

### 5.字符编码

xxx -> 110000110110 （编码）
110000110110 -> xxx （解码）

- 所有的数据在计算机中存储时都是以二进制形式存储的，文字也不例外。
   所以一段文字在存储到内存中时，都需要转换为二进制编码
   当我们读取这段文字时，计算机会将编码转换为字符，供我们阅读
   
- 编码
   - 将字符转换为二进制码的过程称为编码
- 解码
   - 将二进制码转换为字符的过程称为解码
- 字符集（charset）
    - 编码和解码所采用的规则称为字符集
- 乱码问题：
   - 如果编码和解码所采用的字符集不同就会出现乱码问题
- 常见的字符集：
   ASCII
   ISO88591
   GB2312
   GBK
   UTF-8，在开发时我们使用的字符集都是UTF-8

### 6.文档的使用

```
<!-- 文档声明，声明当前网页的版本 -->
<!doctype html>

<!-- html的根标签（元素），网页中的所有内容都要写根元素的里边 -->
<html>

   <!-- head是网页的头部，head中的内容不会在网页中直接出现，主要用来帮助浏览器或搜索引擎来解析网页 -->
   <head>

      <!-- meta标签用来设置网页的元数据，这里meta用来设置网页的字符集，避免乱码问题 -->
      <meta charset="utf-8">
      
      <!-- title中的内容会显示在浏览器的标题栏，搜索引擎会主要根据title中的内容来判断网页的主要内容 -->
      <title>网页的标题</title>

   </head>

   <!-- body是html的子元素，表示网页的主体，网页中所有的可见内容都应该写在body里 -->
   <body>

      <!-- h1网页的一级标题 -->
      <h1>网页的大标题</h1>

   </body>

</html>
```

![网页的标题](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E7%BD%91%E9%A1%B5%E7%9A%84%E6%A0%87%E9%A2%98.png)

![文档的使用](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E6%96%87%E6%A1%A3%E7%9A%84%E4%BD%BF%E7%94%A8.png)

### 7.实体

在网页中编写的多个空格默认情况会自动被浏览器解析为一个空格

在HTML中有些时候，我们不能直接书写一些特殊符号
    比如：多个连续的空格，比如字母两侧的大于和小于号

如果我们需要在网页中书写这些特殊的符号，则需要使用html中的实体（转义字符）
实体的语法：

​	&实体的名字;
​	    &nbsp; 空格
   	 &gt; 大于号
   	 &lt; 小于号
​    	&copy; 版权符号

```
<p>
    今天&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;天气真不错！
</p>

<p>
    a&lt;b&gt;c
</p>
```

![实体](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E5%AE%9E%E4%BD%93.png)

### 8.meta标签

meta主要用于设置网页中的一些元数据，元数据不是给用户看
    charset 指定网页的字符集
    name 指定的数据的名称
    content 指定的数据的内容

-  keywords 表示网站的关键字，可以同时指定多个关键字，关键字间使用,隔开

```
<meta name="Keywords" content="网上购物,网上商城,手机,笔记本,电脑,MP3,CD,VCD,DV,相机,数码,配件,手表,存储卡,京东"/>
<meta name="keywords" content="网购,网上购物,在线购物,网购网站,网购商城,购物网站,网购中心,购物中心,卓越,亚马逊,卓越亚马逊,亚马逊中国,joyo,amazon">
```

通过keywords中配置的content进行seo

![关键字content](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E5%85%B3%E9%94%AE%E5%AD%97content.png)

- description 用于指定网站的描述

  网站的描述会显示在搜索引擎的搜索的结果中

```
<meta name="description" content="京东JD.COM-专业的综合网上购物商城，为您提供正品低价的购物选择、优质便捷的服务体验。商品来自全球数十万品牌商家，囊括家电、手机、电脑、服装、居家、母婴、美妆、个护、食品、生鲜等丰富品类，满足各种购物需求。">
```

![关键字description](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E5%85%B3%E9%94%AE%E5%AD%97description.png)

- title标签的内容会作为搜索结果的超链接上的文字显示

```
<title>京东(JD.COM)-正品低价、品质保障、配送及时、轻松购物！</title>
```

![title标签](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/title%E6%A0%87%E7%AD%BE.png)

- http-equiv="refresh"

​	content中的数字代表跳转时间，分号后的url代表跳转的地址：

```
<meta http-equiv="refresh" content="3;url=https://www.mozilla.org">
```

​	3秒后跳转到百度页面：

```
<meta http-equiv="refresh" content="3;url=https://www.baidu.com">
```

### 9.语义化标签

在网页中HTML专门用来负责网页的结构
    所以在使用html标签时，应该关注的是标签的语义，而不是它的样式

#### 标题标签

​       h1 ~ h6 一共有六级标题

​        从h1~h6重要性递减，h1最重要，h6最不重要

​        h1在网页中的重要性仅次于title标签，一般情况下一个页面中只会有一个h1

​        一般情况下标题标签只会使用到h1~h3，h4~h6很少用

​        标题标签都是块元素。在页面中独占一行的元素称为块元素（block element）

![标题标签](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E6%A0%87%E9%A2%98%E6%A0%87%E7%AD%BE.png)

- hgroup标签

  用来为标题分组，可以将一组相关的标题同时放入到hgroup

  ```
  <hgroup>
        <h1>回乡偶书二首</h1>
        <h2>其一</h2>
  </hgroup>
  ```

![分组标签](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E5%88%86%E7%BB%84%E6%A0%87%E7%AD%BE.png)

- p标签

  p标签表示页面中的一个段落，p也是一个块元素


```
<p>在p标签中的内容就表示一个段落</p>
<p>在p标签中的内容就表示一个段落</p>
```

![p标签](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/p%E6%A0%87%E7%AD%BE.png)

- em标签

  em标签用于表示语音语调的一个加重，是一个行内元素。

  在页面中不会独占一行的元素称为行内元素（inline element）

  ```
  <p>今天天气<em>真</em>不错！</p>
  ```

  ![em标签](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/em%E6%A0%87%E7%AD%BE.png)

- strong标签

  strong表示强调重要内容

  ```
  <p>你今天必须要<strong>完成作业</strong>！</p>
  ```

  ![strong标签](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/strong%E6%A0%87%E7%AD%BE.png)

- blockquote标签

  blockquote 表示一个长引用

  ```
    鲁迅说：
  <blockquote>
      这句话我是从来没有说过的！
  </blockquote>
  ```

  ![blockquote标签](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/blockquote%E6%A0%87%E7%AD%BE.png)

- q标签

  q表示一个短引用

  ```
  子曰<q>学而时习之，乐呵乐呵！</q>
  ```

  ![q标签](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/q%E6%A0%87%E7%AD%BE.png)

- br标签

  br标签表示页面中的换行

  ```
  <br>
  今天天气真不错
  ```

![br标签](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/br%E6%A0%87%E7%AD%BE.png)

#### 语义化标签的一些修正

块元素（block element）

​		在网页中一般通过块元素来对页面进行布局
行内元素（inline element）

- 行内元素主要用来包裹文字


- 一般情况下会在块元素中放行内元素，而不会在行内元素中放块元素
- 块元素中基本上什么都能放
- p元素中不能放任何的块元素

浏览器在解析网页时，会自动对网页中不符合规范的内容进行修正
    比如：
        标签写在了根元素的外部
        p元素中嵌套了块元素
        根元素中出现了除head和body以外的子元素
        ... ...

```
     <p>
         <h1>哈哈</h1>
     </p>
   
    
</body>
</html>

<h1>我就要写在html标签的外部！</h1>
```

![语义化标签修正](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E8%AF%AD%E4%B9%89%E5%8C%96%E6%A0%87%E7%AD%BE%E4%BF%AE%E6%AD%A3.png)

#### 布局标签（结构化语义标签）

- header 表示网页的头部
- main 表示网页的主体部分(一个页面中只会有一个main)
- footer 表示网页的底部
- nav 表示网页中的导航
- aside 和主体相关的其他内容（侧边栏）
- article 表示一个独立的文章
- section 表示一个独立的区块，上边的标签都不能表示时使用section

- div 没有语义，就用来表示一个区块，目前来讲div还是我们主要的布局元素
- span 行内元素，没有任何的语义，一般用于在网页中选中文字

### 10.列表

html列表一共有三种：

#### 有序列表

使用ol标签来创建无序列表，使用li表示列表项

```
<ol>
    <li>结构</li>
    <li>表现</li>
    <li>行为</li>
</ol>
```

![有序列表](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E6%9C%89%E5%BA%8F%E5%88%97%E8%A1%A8.png)

#### 无序列表

使用ul标签来创建无序列表，使用li表示列表项

```
<ul>
    <li>结构</li>
    <li>表现</li>
    <li>行为</li>
</ul>
```

![无序列表](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E6%97%A0%E5%BA%8F%E5%88%97%E8%A1%A8.png)

#### 定义列表

使用dl标签来创建一个定义列表，使用dt来表示定义的内容，使用dd来对内容进行解释说明

```
<dl>
    <dt>结构</dt>
    <dd>结构表示网页的结构，结构用来规定网页中哪里是标题，哪里是段落</dd>
    <dd>结构表示网页的结构，结构用来规定网页中哪里是标题，哪里是段落</dd>
    <dd>结构表示网页的结构，结构用来规定网页中哪里是标题，哪里是段落</dd>
</dl>
```

![定义列表](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E5%AE%9A%E4%B9%89%E5%88%97%E8%A1%A8.png)

#### 列表之间可以互相嵌套

```
<ul>
    <li>
        aa
        <ul>
            <li>aa-1</li>
            <li>aa-2
                <ul>
                    <li>aa-1</li>
                    <li>aa-2</li>
                </ul>
            </li>
        </ul>
    </li>
</ul>
```

![列表嵌套](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E5%88%97%E8%A1%A8%E5%B5%8C%E5%A5%97.png)

### 11.超链接

超链接可以让我们从一个页面跳转到其他页面，或者是当前页面的其他的位置

使用 a 标签来定义超链接，相关属性：

#### href 

指定跳转的目标路径：值可以是一个外部网站的地址，也可以写一个内部页面的地址

超链接也是一个行内元素，在a标签中可以嵌套除它自身外的任何元素

```
<a href="https://www.baidu.com">超链接</a>
<br><br>
<!-- <a href="https://www.baidu123.com">超链接</a> -->
<a href="07.列表.html">超链接2</a>
```

![超链接](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E8%B6%85%E9%93%BE%E6%8E%A5.png)

- 可以直接将超链接的href属性设置为#，这样点击超链接以后，页面不会发生跳转，而是转到当前页面的顶部的位置

  ```
  <!-- 在开发中可以将#作为超链接的路径的展位符使用 -->
  <a href="#">这是一个新的超链接</a> <!--单击该超链接后回到页面顶部-->
  ```

![超链接#](../../Typora图片/Images/HTML5 + CSS3/超链接%23.png)

- 可以使用 javascript:; 来作为href的属性，此时点击这个超链接什么也不会发生

  ```
  <a href="javascript:;">这是一个新的超链接</a>
  ```

- 可以跳转到页面的指定位置，只需将href属性设置 #目标元素的id属性值

#### target

用来指定超链接打开的位置，可选值：

- _self 默认值 在当前页面中打开超链接

- _blank 在一个新的页面中打开超链接

  ```
  <a href="07.列表.html" target="_blank">超链接</a> //打开一个新的页面
  ```

#### id（唯一不重复的）

 每一个标签都可以添加一个id属性，id属性就是元素的唯一标识，同一个页面中不能出现重复的id属性

```
<br><br>
<a href="#bottom">去底部</a><!--通过#id到达指定位置-->
```

```
<a id="bottom" href="#">回到顶部</a>
```

```
<br><br>
<a href="#p3">去第三个自然段</a><!--通过#id到达指定位置-->

<br><br>

<p>在我的后园，可以看见墙外有两株树，一株是枣树，还有一株也是枣树。 这上面的夜的天空，奇怪而高，我生平没有见过这样奇怪而高的天空。</p>
<p>在我的后园，可以看见墙外有两株树，一株是枣树，还有一株也是枣树。 这上面的夜的天空，奇怪而高，我生平没有见过这样奇怪而高的天空。</p>
<p id="p3">在我的后园，可以看见墙外有两株树，一株是枣树，还有一株也是枣树。 这上面的夜的天空，奇怪而高，我生平没有见过这样奇怪而高的天空。</p>
```

### 12.图片标签

图片标签用于向当前页面中引入一个外部图片
 使用img标签来引入外部图片，img标签是一个自结束标签
 img这种元素属于替换元素（块和行内元素之间，具有两种元素的特点）

####  属性

- src 属性指定的是外部图片的路径（路径规则和超链接是一样的）

- alt 图片的描述，这个描述默认情况下不会显示，有些浏览器会图片无法加载时显示， 搜索引擎会根据alt中的内容来识别图片，如果不写alt属性则图片不会被搜索引擎所收录

- width 图片的宽度 (单位是像素)

- height 图片的高度

  ​    宽度和高度中如果只修改了一个，则另一个会等比例缩放

- 注意：

   一般情况在pc端，不建议修改图片的大小，需要多大的图片就裁多大

  但是在移动端，经常需要对图片进行缩放（大图缩小）

#### 图片的格式

-  jpeg(jpg)

  支持的颜色比较丰富，不支持透明效果，不支持动图，一般用来显示照片

-  gif

     支持的颜色比较少，支持简单透明，支持动图，单一的图片，一般用来支持颜色单一的图片，动图

- png

     支持的颜色丰富，支持复杂透明，不支持动图（专为网页而生）

- webp

  这种格式是谷歌新推出的专门用来表示网页中的图片的一种格式
  备其他图片格式的所有优点，而且文件还特别的小

  缺点：兼容性不好

- base64 

  将图片使用base64编码，这样可以将图片转换为字符，通过字符的形式来引入图片    ，一般都是一些需要和网页一起加载的图片才会使用base64

​    （效果一样，用小的，效果不一样，用效果好的）

```
<img src="./img/1.gif" alt="松鼠">

<img width="200"  src="https://d2ggl082rr1mkp.cloudfront.net/category/IronMan_preview_1521810286_220_310.jpeg" alt="钢铁侠">

<img src="data:image/jpeg;base64,/9j/...">
<img src="data:image/gif;base64,R0lGODlhaAFoAcQAAOfn5y0tLdfX1xQUFsbGxre3t5qamqOjpP7+/...>
```

![图片标签](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E5%9B%BE%E7%89%87%E6%A0%87%E7%AD%BE.png)

### 13.内联框架

内联框架，用于向当前页面中引入一个其他页面

- src 指定要引入的网页的路径

- frameborder 指定内联框架的边框

  0表示没有 ，1表示有

```
<iframe src="https://www.qq.com" width="800" height="600" frameborder="0"></iframe>
```

![内联框架](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E5%86%85%E8%81%94%E6%A1%86%E6%9E%B6.png)



## 二、CSS

### 1.CSS简介

层叠样式表，网页实际上是一个多层的结构，通过CSS可以分别为网页的每一个层来设置样式，而最终我们能看到只是网页的最上边一层，总之一句话，CSS用来设置网页中元素的样式   

使用CSS来修改元素的样式：

#### 第一种方式(内联样式，行内样式)

   - 在标签内部通过style属性来设置元素的样式

   - 问题：
       使用内联样式，样式只能对一个标签生效，
           如果希望影响到多个元素必须在每一个元素中都复制一遍
           并且当样式发生变化时，我们必须要一个一个的修改，非常的不方便


   - 注意：开发时尽量不要使用内联样式

```
<p style="color:red; font-size: 60px;">少小离家老大回，乡音无改鬓毛衰</p>

<p style="color: red; font-size: 60px;">今天天气真不错！</p>
```

![内联样式](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E5%86%85%E8%81%94%E6%A0%B7%E5%BC%8F.png)

#### 第二种方式（内部样式表）

- 将样式编写到head中的style标签里，然后通过CSS的选择器来选中元素并为其设置各种样式，可以同时为多个标签设置样式，并且修改时只需要修改一处即可全部应用
- 内部样式表更加方便对样式进行复用
- 问题：
  我们的内部样式表只能对一个网页起作用，它里边的样式不能跨页面进行复用

```
 <style>

    p{
        color: green;
        font-size: 50px;
    }

</style> 
```

![内部样式表](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E5%86%85%E9%83%A8%E6%A0%B7%E5%BC%8F%E8%A1%A8.png)

#### 第三种方式 （外部样式表） 最佳实践

- 可以将CSS样式编写到一个外部的CSS文件中,然后通过link标签来引入外部的CSS文件
- 外部样式表需要通过link标签进行引入，意味着只要想使用这些样式的网页都可以对其进行引用，使样式可以在不同页面之间进行复用
- 将样式编写到外部的CSS文件中，可以使用到浏览器的缓存机制，从而加快网页的加载速度，提高用户的体验。

```
<link rel="stylesheet" href="./style.css">
```

![外部样式表](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E5%A4%96%E9%83%A8%E6%A0%B7%E5%BC%8F%E8%A1%A8.png)

![外部样式表1](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E5%A4%96%E9%83%A8%E6%A0%B7%E5%BC%8F%E8%A1%A81.png)

### 2.CSS语法

CSS的基本语法:选择器 声明块

- 选择器，通过选择器可以选中页面中的指定元素，比如 p 的作用就是选中页面中所有的p元素

- 声明块，通过声明块来指定要为元素设置的样式，声明块由一个一个的声明组成，声明是一个名值对结构，一个样式名对应一个样式值，名和值之间以:连接，以;结尾

```
p{
    color: red;
    font-size: 40px;
}

h1{
    color: green;
}
```

### 3.常用选择器

```
<h1 class="blue abc">我是标题</h1>
<p>少小离家老大回</p>
<p>乡音无改鬓毛衰</p>
<p id="red">儿童相见不相识</p>
<p>笑问客从何处来</p>
<!--
    class 是一个标签的属性，它和id类似，不同的是class可以重复使用
        可以通过class属性来为元素分组
        可以同时为一个元素指定多个class属性
-->
<p class="blue">秋水共长天一色</p>
<p class="blue">落霞与孤鹜齐飞</p>
```

#### 元素选择器

- 作用：根据标签名来选中指定的元素
- 语法：标签名{}
- 例子：p{}  h1{}  div{}

```
 p{
    color: red;
}

h1{
    color: green;
} 
```

#### id选择器

- 作用：根据元素的id属性值选中一个元素
- 语法：#id属性值{}
- 例子：#box{} #red{}

```
#red{
    color: red;
}
```

#### 类选择器

- 作用：根据元素的class属性值选中一组元素
- 语法：.class属性值

```
.blue{
    color: blue;
}

.abc{
    font-size: 20px;
}
```

#### 通配选择器

- 作用：选中页面中的所有元素
- 语法: *

```
*{
    color: red;
}
```

### 4.复合选择器

#### 交集选择器

- 作用：选中同时复合多个条件的元素
- 语法：选择器1选择器2选择器3选择器n{}
- 注意点： 交集选择器中如果有元素选择器，必须使用元素选择器开头

```
div.red{
    font-size: 30px;
}

.a.b.c{
    color: blue
}
```

#### 选择器分组（并集选择器）

- 作用：同时选择多个选择器对应的元素

- 语法：选择器1,选择器2,选择器3,选择器n{}

  #b1,.p1,h1,span,div.red{}

```
h1, span{
    color: green
}
```

### 5.关系选择器

```
<div class="box">
    我是一个div
    <p>
        我是div中的p元素
        <span>我是p元素中的span</span>
    </p>
    <div></div>
    <span>我是div中的span元素</span>
    <span>我是div中的span元素</span>
    <span>我是div中的span元素</span>
    <span>我是div中的span元素</span>

</div>

<span>
    我是div外的span
</span>
```

#### 子元素选择器

- 作用：选中指定父元素的指定子元素
- 语法：父元素 > 子元素

```
div.box > span{
    color: orange;
} 
```

#### 后代元素选择器

- 作用：选中指定元素内的指定后代元素
- 语法：祖先 后代

```
div span{
    color: skyblue
}
```

等价于：

```
div > p > span{
    color: skyblue;
} 
```

#### 兄弟元素选择器

- 选择下一个兄弟

  ​    语法：前一个 + 下一个

- 选择下边所有的兄弟

  ​    语法：兄 ~ 弟

```
p + span{
    color: red;
}


p ~ span{
    color: red;
}
```

#### 备注

- 父元素：直接包含子元素的元素叫做父元素

- 子元素：直接被父元素包含的元素是子元素

- 祖先元素

  - 直接或间接包含后代元素的元素叫做祖先元素

  - 一个元素的父元素也是它的祖先元素

- 后代元素

    - 直接或间接被祖先元素包含的元素叫做后代元素

  - 子元素也是后代元素

- 兄弟元素：拥有相同父元素的元素是兄弟元素

### 6.属性选择器

- [属性名] 选择含有指定属性的元素
- [属性名=属性值] 选择含有指定属性和属性值的元素
- [属性名^=属性值] 选择属性值以指定值开头的元素
- [属性名$=属性值] 选择属性值以指定值结尾的元素
- [属性名*=属性值] 选择属性值中含有某值的元素的元素

```
/* p[title]{ */
/* p[title=abc]{ */
/* p[title^=abc]{ */
/* p[title$=abc]{ */
p[title*=e]{
    color: orange;
}
```

### 7.伪类选择器

```
<ul>
<!--        <span>我是一个span</span>-->
        <li>第〇个</li>
        <li>第一个</li>
        <li>第二个</li>
        <li>第三个</li>
        <li>第四个</li>
        <li>第五个</li>
    </ul>
```

伪类（不存在的类，特殊的类）

- 伪类用来描述一个元素的特殊状态，比如：第一个子元素、被点击的元素、鼠标移入的元素...

- 伪类一般情况下都是使用:开头

  - :first-child 第一个子元素

  - :last-child 最后一个子元素

    ```
    ul > li:first-child{
        color: red;
    }
    
     ul > li:last-child{
        color: red;
    }
    ```

    ![伪类](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E4%BC%AA%E7%B1%BB.png)

    但是如果第一个li前为<span>，则无效，可以理解为第一个被span占位了：

    ```
    <ul>
        <span>我是一个span</span>//这是第一个
        <li>第〇个</li>//这是第二个
        <li>第一个</li>//这是第三个
        <li>第二个</li>
        <li>第三个</li>
        <li>第四个</li>
        <li>第五个</li>
    </ul>
    ```

    ![第一个为span](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E7%AC%AC%E4%B8%80%E4%B8%AA%E4%B8%BAspan.png)

  - :nth-child() 选中第n个子元素

  - 特殊值：
       n ：第n个（ n的范围0到正无穷）

       2n 或 even 表示选中偶数位的元素

       2n+1 或 odd 表示选中奇数位的元素

       ```
       ul > li:nth-child(2n+1){
           color: red;
       } 
       ```

       ![选择奇数个子元素](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E9%80%89%E6%8B%A9%E5%A5%87%E6%95%B0%E4%B8%AA%E5%AD%90%E5%85%83%E7%B4%A0.png)

  - 以上这些伪类都是根据所有的子元素进行排序

  :first-of-type
  :last-of-type
  :nth-of-type()

  这几个伪类的功能和上述的类似，不同点是他们是在同类型元素中进行排序

  ```
  ul > li:first-of-type{
      color: red;
  } //第0个也能生效：如图
  ```

  ![伪类type](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E4%BC%AA%E7%B1%BBtype.png)

- :not() 否定伪类：将符合条件的元素从选择器中去除

     ```
     ul > li:not(:nth-of-type(3)){
         color: yellowgreen;
     }
     ```

![伪类not-type](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E4%BC%AA%E7%B1%BBnot-type.png)

### 8.a元素的伪类

#### :link 

用来表示没访问过的链接（正常的链接）

```
a:link{
    color: red;
    
}
```

#### :visited 

用来表示访问过的链接，由于隐私的原因，所以visited这个伪类只能修改链接的**颜色**

```
a:visited{
    color: orange; 
    /* font-size: 50px;   */
}
```

#### :hover 

用来表示鼠标移入的状态

```
a:hover{
    color: aqua;
    font-size: 50px;
}
```

#### :active 

用来表示鼠标点击

```
a:active{
    color: yellowgreen;
    
}
```

### 9.伪元素选择器

伪元素，表示页面中一些特殊的并不真实的存在的元素（特殊的位置）
    伪元素使用 :: 开头

- ::first-letter 表示第一个字母
- ::first-line 表示第一行
- ::selection 表示选中的内容
- ::before 元素的开始 
- ::after 元素的最后

**before 和 after 必须结合content属性来使用**

```
p::first-letter{
    font-size: 50px;
}

p::first-line{
    background-color: yellow; 
}

p::selection{
    background-color: greenyellow;
}

div::before{
    content: '『';
 }

div::after{
    content: '』';
}
```

```
<div>Hello Hello How are you</div>

<p>
    Lorem ipsum dolor sit amet consectetur adipisicing elit. Atque velit modi veniam nisi veritatis tempore laborum nemo ipsa itaque optio. Id odit consequatur mollitia excepturi, minus saepe nostrum vel porro.
</p>
```

![伪元素选择器](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E4%BC%AA%E5%85%83%E7%B4%A0%E9%80%89%E6%8B%A9%E5%99%A8.png)

### 10.样式的继承

样式的继承，我们为一个元素设置的样式同时也会应用到它的后代元素上

- 继承是发生在祖先后后代之间的


- 继承的设计是为了方便我们的开发， 利用继承我们可以将一些通用的样式统一设置到共同的祖先元素上， 这样只需设置一次即可让所有的元素都具有该样式


**注意**：并不是所有的样式都会被继承：
    比如 背景相关的，布局相关等的这些样式都不会被继承。

```
p{
    color: red;
    background-color: orange;
}

div{
    color: yellowgreen
}
```

```
<p>
    我是一个p元素
    <span>我是p元素中的span</span>
</p>

<span>我是p元素外的span</span>

<div>
    我是div
    <span>
        我是div中的span
        <em>我是span中的em</em>
    </span>
</div>
```

![样式的继承](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E6%A0%B7%E5%BC%8F%E7%9A%84%E7%BB%A7%E6%89%BF.png)

### 11.选择器的权重

样式的冲突：

当我们通过不同的选择器，选中相同的元素，并且为相同的样式设置不同的值时，此时就发生了样式的冲突。

发生样式冲突时，应用哪个样式由选择器的权重（优先级）决定

选择器的权重：

- 内联样式        1,0,0,0
- id选择器        0,1,0,0
- 类和伪类选择器   0,0,1,0
- 元素和伪元素选择器       0,0,0,1
- 通配选择器       0,0,0,0
- 继承的样式       没有优先级

比较优先级时，需要将所有的选择器的优先级进行相加计算，最后优先级越高，则越优先显示（分组选择器是单独计算的。

选择器的累加不会超过其最大的数量级，类选择器在高也不会超过id选择器。

如果优先级计算后相同，此时则优先使用靠下的样式

**注意**：

- 如果是两种相同优先级 为同一个元素 同一个属性设置 的话，是哪个写在代码靠后 最终就按那个的样式

- 交集选择器的优先级 所有优先级 加起来 运算 然后比较

- 并集的话 就是各算各的。

可以在某一个样式的后边添加 !important ，则此时该样式会获取到最高的优先级，甚至超过内联样式，
    **注意**：在开发中这个玩意一定要慎用！

### 12.单位

#### 像素

- 屏幕（显示器）实际上是由一个一个的小点点构成的

- 不同屏幕的像素大小是不同的，像素越小的屏幕显示的效果越清晰
- 所以同样的200px在不同的设备下显示效果不一样

#### 百分比

- 也可以将属性值设置为相对于其父元素属性的百分比

- 设置百分比可以使子元素跟随父元素的改变而改变

#### em

em是相对于元素的字体大小来计算的
- 1em = 1font-size
- em会根据字体大小的改变而改变

#### rem

rem是相对于根元素的字体大小来计算

### 13.颜色

在CSS中可以直接使用颜色名来设置各种颜色：
    比如：red、orange、yellow、blue、green ... ...
    但是在css中直接使用颜色名是非常的不方便

#### RGB值

 RGB通过三种颜色的不同浓度来调配出不同的颜色
- R red，G green ，B blue
- 每一种颜色的范围在 0 - 255 (0% - 100%) 之间
- 语法：RGB(红色,绿色,蓝色)

#### RGBA

就是在rgb的基础上增加了一个a表示不透明度

需要四个值，前三个和rgb一样，第四个表示不透明度：
1表示完全不透明   0表示完全透明  .5半透明

#### 十六进制的RGB值

- 语法：#红色绿色蓝色
- 颜色浓度通过 00-ff
- 如果颜色两位两位重复可以进行简写  
    #aabbcc --> #abc

#### HSL值&HSLA值

- H 色相(0 - 360)
- S 饱和度，颜色的浓度 0% - 100%
- L 亮度，颜色的亮度 0% - 100%

## 三、布局

### 1.文档流

- 网页是一个多层的结构，一层摞着一层
- 通过CSS可以分别为每一层来设置样式
- 作为用户来讲只能看到最顶上一层
- 这些层中，最底下的一层称为文档流，文档流是网页的基础，我们所创建的元素默认都是在文档流中进行排列
- 对于我们来元素主要有两个状态：
    在文档流中
    不在文档流中（脱离文档流）

元素在文档流中的特点：

- 块元素
    - 块元素会在页面中独占一行(自上向下垂直排列)
    - 默认宽度是父元素的全部（会把父元素撑满）
    - 默认高度是被内容撑开（子元素）

- 行内元素
    - 行内元素不会独占页面的一行，只占自身的大小
    - 行内元素在页面中左向右水平排列，如果一行之中不能容纳下所有的行内元素
        则元素会换到第二行继续自左向右排列（书写习惯一致）
    - 行内元素的默认宽度和高度都是被内容撑开

```
<div class="box1">我是div1</div>
<div class="box2">我是div2</div>

<span>我是span1</span>
<span>我是span2</span>
<span>我是span2</span>
<span>我是span2</span>
<span>我是span2</span>
<span>我是span2</span>
<span>我是span2</span>
<span>我是span2</span>
<span>我是span2</span>
<span>我是span2</span>
```

```
.box1{
    width: 100px;
    background-color: yellow;
}

.box2{
    width: 100px;
    background-color: red;
}

span{
    background-color: #bfa;
}
```

![文档流](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E6%96%87%E6%A1%A3%E6%B5%81.png)

### 2.盒模型

- CSS将页面中的所有元素都设置为了一个矩形的盒子
- 将元素设置为矩形的盒子后，对页面的布局就变成将不同的盒子摆放到不同的位置
- 每一个盒子都由一下几个部分组成：
    - 内容区（content）
    - 内边距（padding）
    - 边框（border）
    - 外边距（margin）

```
.box1{
    /* 
        内容区（content），元素中的所有的子元素和文本内容都在内容区中排列  
            内容区的大小由width 和 height两个属性来设置
                width 设置内容区的宽度
                height 设置内容区的高度          
     */
    width: 200px;
    height: 200px;
    background-color: #bfa;

    /* 
        边框（border），边框属于盒子边缘，边框里边属于盒子内部，出了边框都是盒子的外部
            边框的大小会影响到整个盒子的大小
        要设置边框，需要至少设置三个样式：
            边框的宽度 border-width
            边框的颜色 border-color
            边框的样式 border-style
     */

     border-width: 10px;
     border-color: red;
     border-style: solid;
}
```

#### 边框

- 边框的宽度 border-width
- 边框的颜色 border-color
- 边框的样式 border-style

##### border-width：

默认值，一般都是 3个像素
border-width可以用来指定四个方向的边框的宽度值的情况

- 四个值：上 右 下 左
- 三个值：上 左右 下
- 两个值：上下 左右

一个值：上下左右       
除了border-width还有一组 border-xxx-width
       xxx可以是 top right bottom left
       用来单独指定某一个边的宽度

```
 border-width: 10px; 
 border-top-width: 10px;
 border-left-width: 30px; 
```

##### border-color:

border-color用来指定边框的颜色，同样可以分别指定四个边的边框,规则和border-width一样

border-color也可以省略不写，如果省略了则自动使用color的颜色值

```
 border-color: orange red yellow green;
 border-color: orange; 
```

##### border-style:

border-style 指定边框的样式:

- solid 表示实线
- dotted 点状虚线
- dashed 虚线
- double 双线

border-style的默认值是none 表示没有边框

```
border-style: solid dotted dashed double;
border-style: solid; 
```

##### border简写

border简写属性，通过该属性可以同时设置边框所有的相关样式，并且没有顺序要求

除了border以外还有四个 border-xxx

- border-top
- border-right
- border-bottom
- border-left

```
border: solid 10px orange; 
border-top: 10px solid red;
border-left: 10px solid red;
border-bottom: 10px solid red; 
```

#### 内边距

内边距（padding）

内容区和边框之间的距离是内边距：

- 一共有四个方向的内边距：

  - padding-top

  - padding-right

  - padding-bottom

  - padding-left

- 内边距的设置会影响到盒子的大小
- 背景颜色会延伸到内边距上

一般盒子的可见框的大小，由**内容区**、**内边距** 和 **边框**共同决定，所以在计算盒子大小时，需要将这三个区域加到一起计算

padding 内边距的简写属性，可以同时指定四个方向的内边距，规则和border-width 一样：

```
padding: 10px 20px 30px 40px;
padding: 10px 20px 30px ;
padding: 10px 20px ;
padding: 10px ;
```

#### 外边距

- 外边距不会影响盒子可见框的大小

- 但是外边距会影响盒子的位置

- 一共有四个方向的外边距：
  
    - margin-top：上外边距，设置一个正值，元素会向下移动
    - margin-right：默认情况下设置margin-right不会产生任何效果
    - margin-bottom：下外边距，设置一个正值，其下边的元素会向下移动
    - margin-left：左外边距，设置一个正值，元素会向右移动
    
    - margin也可以设置负值，如果是负值则元素会向相反的方向移动
    
- 元素在页面中是按照自左向右的顺序排列的，
    所以默认情况下如果我们设置的左和上外边距则会移动元素自身
    而设置**下和右**外边距会移动**其他元素**

- margin的简写属性
    margin 可以同时设置四个方向的外边距 ，用法和padding一样

- margin会影响到盒子实际占用空间

```
margin-top: 100px;
margin-left: 100px;
margin-bottom: 100px; 
```

### 3.盒子的水平布局

元素在其父元素中水平方向的位置由以下几个属性共同决定：

- margin-left
- border-left
- padding-left
- width
- padding-right
- border-right
- margin-right

一个元素在其父元素中，水平布局必须要满足以下的等式：
margin-left+border-left+padding-left+width+padding-right+border-right+margin-right = 其父元素内容区的宽度 （必须满足）

如果相加结果使等式不成立，则称为过度约束，则等式会自动调整：

- 如果这七个值中没有为 auto 的情况，则浏览器会自动调整margin-right值以使等式满足

- 这七个值中有三个值和可以设置为auto

  - width、margin-left、maring-right

  - 如果某个值为auto，则会自动调整为auto的那个值以使等式成立

    0 + 0 + 0 + auto + 0 + 0 + 0 = 800  auto = 800

    0 + 0 + 0 + auto + 0 + 0 + 200 = 800  auto = 600

    200 + 0 + 0 + auto + 0 + 0 + 200 = 800  auto = 400

    auto + 0 + 0 + 200 + 0 + 0 + 200 = 800  auto = 400


    auto + 0 + 0 + 200 + 0 + 0 + auto = 800  auto = 300

  - 如果将一个宽度和一个外边距设置为auto，则宽度会调整到最大，设置为auto的外边距会自动为0

  - 如果将三个值都设置为auto，则外边距都是0，宽度最大

  - 如果将两个外边距设置为auto，宽度固定值，则会将外边距设置为相同的值，所以经常利用这个特点来使一个元素在其父元素中水平居中：

    ```
    width:xxxpx;
    margin:0 auto;
    ```

### 4.盒子的垂直布局

默认情况下父元素的高度被内容撑开

子元素是在父元素的内容区中排列的，如果子元素的大小超过了父元素，则子元素会从父元素中溢出，使用 overflow 属性来设置父元素如何处理溢出的子元素

可选值：

- visible，默认值 子元素会从父元素中溢出，在父元素外部的位置显示
- hidden 溢出内容将会被裁剪不会显示
- scroll 生成两个滚动条，通过滚动条来查看完整的内容
- auto 根据需要生成滚动条

overflow-x: 处理水平方向的浮动

overflow-y:处理垂直方向的浮动

### 5.外边距的折叠

**垂直**外边距的重叠（折叠）

- 相邻的垂直方向外边距会发生重叠现象
- 兄弟元素：
     - 兄弟元素间的相邻垂直外边距会取两者之间的较大值（两者都是正值）
     - 特殊情况：
         如果相邻的外边距一正一负，则取两者的和
         如果相邻的外边距都是负值，则取两者中绝对值较大的

     - 兄弟元素之间的外边距的重叠，对于开发是有利的，所以我们不需要进行处理

- 父子元素
    - 父子元素间相邻外边距，子元素的会传递给父元素（上外边距）
    - 父子外边距的折叠会影响到页面的布局，必须要进行处理

### 6.行内元素的盒模型

- 行内元素不支持设置宽度和高度
- 行内元素可以设置padding，但是垂直方向padding不会影响页面的布局
- 行内元素可以设置border，垂直方向的border不会影响页面的布局
- 行内元素可以设置margin，垂直方向的margin不会影响布局

#### display 用来设置元素显示的类型

可选值：

- inline 将元素设置为行内元素
- block 将元素设置为块元素
- inline-block 将元素设置为行内块元素 ，既可以设置宽度和高度又不会独占一行
- table 将元素设置为一个表格
- none 元素不在页面中显示

#### visibility 用来设置元素的显示状态

可选值：

- visible 默认值，元素在页面中正常显示
- hidden 元素在页面中隐藏 不显示，但是依然占据页面的位置

### 7.默认样式

#### 重置样式表

专门用来对浏览器的样式进行重置的：

- reset.css 直接去除了浏览器的默认样式
- normalize.css 对默认样式进行了统一

```
<!-- <link rel="stylesheet" href="./css/reset.css"> -->
<link rel="stylesheet" href="./css/normalize.css">
```

#### 默认样式

- 通常情况，浏览器都会为元素设置一些默认样式
- 默认样式的存在会影响到页面的布局，通常情况下编写网页时必须要去除浏览器的默认样式（PC端的页面）

```
*{
    margin: 0;
    padding: 0;
}
```

### 8.盒子的尺寸

默认情况下，盒子可见框的大小由内容区、内边距和边框共同决定

box-sizing 用来设置盒子尺寸的计算方式（设置width和height的作用）

可选值：

- content-box 默认值，宽度和高度用来设置内容区的大小（怪异盒模型）

- border-box 宽度和高度用来设置整个盒子可见框的大小（标准盒模型）

  width 和 height 指的是内容区 和 内边距 和 边框的总大小

  ```
  box-sizing: border-box;
  ```

### 12.轮廓和圆角

#### box-shadow

用来设置元素的阴影效果，阴影不会影响页面布局

- 第一个值 水平偏移量 设置阴影的水平位置 正值向右移动 负值向左移动
- 第二个值 垂直偏移量 设置阴影的水平位置 正值向下移动 负值向上移动
- 第三个值 阴影的模糊半径
- 第四个值 阴影的颜色

```
box-shadow: 0px 0px 50px rgba(0, 0, 0, .3) ;
```

#### outline

用来设置元素的轮廓线，用法和border一模一样,轮廓和边框不同的点，就是轮廓不会影响到可见框的大小

#### border-radius

用来设置圆角(圆角设置的圆的半径大小),border-radius 可以分别指定四个角的圆角:

- 四个值 左上 右上 右下 左下
- 三个值 左上 右上/左下 右下
- 两个值 左上/右下 右上/左下

```
border-radius: 20px / 40px; 
```

或者分别设置：

```
/* border-top-left-radius:  */
/* border-top-right-radius */
/* border-bottom-left-radius:  */
/* border-bottom-right-radius:  */
 border-top-left-radius:50px 100px;
```

用百分比设置：

```
/* 将元素设置为一个圆形 */
border-radius: 50%;
```

## 四、浮动

### 1.简介

通过浮动可以使一个元素向其父元素的左侧或右侧移动，使用 float 属性来设置于元素的浮动，可选值：

- none 默认值 ，元素不浮动
- left 元素向左浮动
- right 元素向右浮动

**注意**：元素设置浮动以后，水平布局的等式便不需要强制成立；元素设置浮动以后，会完全从文档流中脱离，不再占用文档流的位置；所以元素下边的还在文档流中的元素会自动向上移动

浮动的特点：

1. 浮动元素会完全脱离文档流，不再占据文档流中的位置
2. 设置浮动以后元素会向父元素的左侧或右侧移动，
3. 浮动元素默认不会从父元素中移出
4. 浮动元素向左或向右移动时，不会超过它前边的其他浮动元素
5. 如果浮动元素的上边是一个没有浮动的块元素，则浮动元素无法上移
6. 浮动元素不会超过它上边的浮动的兄弟元素，最多最多就是和它一样高

```
<div class="box1"></div>
<div class="box2"></div>
<div class="box3"></div>
```

```
.box1{
    width: 400px;
    height: 200px;
    background-color: #bfa;
    float: left;
}

.box2{
    width: 400px;
    height: 200px;
    background-color: orange;
    float: left;
}

.box3{
    width: 200px;
    height: 200px;
    background-color: yellow;
    float: right;
}
```

![浮动简介](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E6%B5%AE%E5%8A%A8%E7%AE%80%E4%BB%8B.png)

浮动可以让页面中的元素可以水平排列，通过浮动可以制作一些水平方向的布局   

### 2.浮动的其他特点

#### 浮动元素不会盖住文字

文字会自动环绕在浮动元素的周围，所以我们可以利用浮动来设置文字环绕图片的效果

```
.box1{
    width: 100px;
    height: 100px;
    background-color: #bfa;
    float: left;
}
```

```
 <div class="box1"></div>
<p>
    在我的后园，可以看见墙外有两株树，一株是枣树，还有一株也是枣树。 这上面的夜的天空，奇怪而高，我生平没有见过这样奇怪而高的天空。他仿佛要离开人间而去，使人们仰面不再看见...
</p>
```

![浮动的文字环绕](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E6%B5%AE%E5%8A%A8%E7%9A%84%E6%96%87%E5%AD%97%E7%8E%AF%E7%BB%95.png)

#### 脱离文档流

元素设置浮动以后，将会从文档流中脱离，从文档流中脱离后，元素的一些特点也会发生变化

脱离文档流的特点： 

- 块元素：

  - 块元素不在独占页面的一行

  - 脱离文档流以后，块元素的宽度和高度默认都被内容撑开

-  行内元素：

​    行内元素脱离文档流以后会变成块元素，特点和块元素一样，脱离文档流以后，不需要再区分块和行内了

```
.box2{
    background-color: yellowgreen;
    float: left;
}

.box3{
    background-color: orange
}

.s1{
    float: left;
    width: 200px;
    height: 200px;
    background-color: yellow;
}
```

```
<span class="s1">我是一个span</span>
 <div class="box2">helloaaaaa</div>
 <div class="box3">hello</div>
```

![浮动的其他特点](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E6%B5%AE%E5%8A%A8%E7%9A%84%E5%85%B6%E4%BB%96%E7%89%B9%E7%82%B9.png)

### 3.高度塌陷

#### BFC

(Block Formatting Context) 块级格式化环境

- BFC是一个CSS中的一个隐含的属性，可以为一个元素开启BFC

    开启BFC该元素会变成一个独立的布局区域

- 元素开启BFC后的特点：
  
    - 开启BFC的元素不会被浮动元素所覆盖
    - 开启BFC的元素子元素和父元素外边距不会重叠
    - 开启BFC的元素可以包含浮动的子元素
    
- 可以通过一些特殊方式来开启元素的BFC：

    - 设置元素的浮动（不推荐）

    - 将元素设置为行内块元素（不推荐）

    - 将元素的overflow设置为一个非visible的值

        常用的方式 为元素设置 overflow:hidden 开启其BFC 以使其可以包含浮动元素

#### 高度塌陷问题

在浮动布局中，父元素的高度默认是被子元素撑开的，

- 当子元素浮动后，其会完全脱离文档流，子元素从文档流中脱离
- 将会无法撑起父元素的高度，导致父元素的高度丢失

父元素高度丢失以后，其下的元素会自动上移，导致页面的布局混乱，高度塌陷是浮动布局中比较常见的一个问题

```
<div class="outer">

    <div class="inner"></div>

</div>

<div style="width: 200px;height: 200px;background-color:yellow;"></div>
```

```
.outer{
    border: 10px red solid;

    /* 
        开启BFC(Block Formatting Context) 
     */

     /* float: left; */
     /* display: inline-block; */
     overflow: hidden;
}

.inner{
    width: 100px;
    height: 100px;
    background-color: #bfa;

    /* 
        产生高度塌陷
     */
    float: left;
```

![高度塌陷](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E9%AB%98%E5%BA%A6%E5%A1%8C%E9%99%B7.png)

### 4.BFC相关

#### 通过设置开启BFC使得不被浮动元素覆盖

```
.box1{
    width: 200px;
    height: 200px;
    background-color: #bfa;
     float: left;
}

.box2{
    width: 200px;
    height: 200px;
    background-color: orange;
    overflow: hidden;
}
```

```
<div class="box1">

</div>

 <div class="box2">

</div>
```

![BFC1](https://raw.githubusercontent.com/weixiaoyun/Images/html-%252B-css/BFC1.png)

#### 处理父子元素的外边距重叠

由于父子元素外边距重叠，导致子元素的margin影响到了父元素

```
.box1{
    width: 200px;
    height: 200px;
    background-color: #bfa;
}

.box3{
    width: 100px;
    height: 100px;
    background-color: yellow;
    margin-top: 100px;
}
```

```
<div class="box1">

    <div class="box3"></div>
</div>
```

![父子元素外边距重叠 (2)](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E7%88%B6%E5%AD%90%E5%85%83%E7%B4%A0%E5%A4%96%E8%BE%B9%E8%B7%9D%E9%87%8D%E5%8F%A0%20(2).png)

给box1开启BFC

```
.box1{
    width: 200px;
    height: 200px;
    background-color: #bfa;
     /*float: left;*/
    overflow: hidden;
}
```

![父元素开启BFC](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E7%88%B6%E5%85%83%E7%B4%A0%E5%BC%80%E5%90%AFBFC.png)

### 5.清除浮动

如果我们不希望某个元素因为其他元素浮动的影响而改变位置，可以通过clear属性来清除浮动元素对当前元素所产生的影响。

clear：

- 作用：清除浮动元素对当前元素所产生的影响
- 可选值：
    - left 清除左侧浮动元素对当前元素的影响
    - right 清除右侧浮动元素对当前元素的影响
    - both 清除两侧中最大影响的那侧

**原理**：设置清除浮动以后，浏览器会自动为元素添加一个上外边距，以使其位置不受其他元素的影响

```
.box1{
    width: 200px;
    height: 200px;
    background-color: #bfa;
    float: left;
}

.box2{
    width: 400px;
    height: 150px;
    background-color: #ff0;
    float: right;
}

.box3{
    width: 200px;
    height: 200px;
    background-color: orange;
    /* 
        由于box1的浮动，导致box3位置上移
            也就是box3收到了box1浮动的影响，位置发生了改变
     */

     clear: both;
}
```

```
<div class="box1">1</div>
<div class="box2">2</div>
<div class="box3">3</div>
```

![清除浮动](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E6%B8%85%E9%99%A4%E6%B5%AE%E5%8A%A8.png)

### 6.高度塌陷的最终解决方案

通过设置一个子元素，清除前面浮动元素对它的影响，然后父元素又需要适应该子元素的特点来清除浮动

```
.box1{
    border: 10px red solid;

    /* overflow: hidden; */
}

.box2{
    width: 100px;
    height: 100px;
    background-color: #bfa;
    float: left;
}

/*通过设置伪元素来减少页面中的无关元素*/
.box1::after{
    content: '';
    display: block;/*伪元素默认为一个行内元素，所以要设置它的display*/
    clear: both;
}
```

```
<div class="box1">
    <div class="box2"></div>
</div>
```

![高度塌陷的最终解决方案](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E9%AB%98%E5%BA%A6%E5%A1%8C%E9%99%B7%E7%9A%84%E6%9C%80%E7%BB%88%E8%A7%A3%E5%86%B3%E6%96%B9%E6%A1%88.png)

### 7.clearfix

clearfix 这个样式可以同时解决高度塌陷和外边距重叠的问题，当遇到这些问题时，直接使用clearfix这个类即可

```
        .box1{
            width: 200px;
            height: 200px;
            background-color: #bfa;
        }

        .box2{
            width: 100px;
            height: 100px;
            background-color: orange;
            margin-top: 100px;
        }

        .clearfix::before,/*通过before伪元素解决外边距重叠问题，可以理解为父子元素之间加入了一个元素*/
        .clearfix::after{ /*通过after伪类解决高度塌陷*/
            content: '';
            display: table; /*table布局隔开外边距的同时不会占位*/
            clear: both;
        }
```

```
<div class="box1 clearfix">
    <div class="box2"></div>
</div>
```

![clearfix](https://raw.githubusercontent.com/weixiaoyun/Images/html-%252B-css/clearfix.png)

## 五、定位

### 1.定位的简介

- 定位是一种更加高级的布局手段
- 通过定位可以将元素摆放到页面的任意位置
- 使用position属性来设置定位
    可选值：
    -  static 默认值，元素是静止的没有开启定位    
    - relative 开启元素的相对定位   
    - absolute 开启元素的绝对定位
    - fixed 开启元素的固定定位
    - sticky 开启元素的粘滞定位

### 2.相对定位

- 当元素的position属性值设置为relative时则开启了元素的相对定位

- 相对定位的特点：

    - 元素开启相对定位以后，如果不设置偏移量元素不会发生任何的变化
    - 相对定位是相对于元素原来的位置进行定位的
    - 相对定位会提升元素的层级
    - 相对定位不会使元素脱离文档流
    - 相对定位不会改变元素的性质块还是块，行内还是行内

- 偏移量（offset）

    当元素开启了定位以后，可以通过偏移量来设置元素的位置

    - top：定位元素和定位位置上边的距离

    - bottom：

      - 定位元素和定位位置下边的距离


      - 定位元素垂直方向的位置由top和bottom两个属性来控制
        通常情况下我们只会使用其中一
    
      - top值越大，定位元素越向下移动
    
      - bottom值越大，定位元素越向上移动
    
    - left：定位元素和定位位置的左侧距离
    
    - right：
    
      - 定位元素和定位位置的右侧距离
    
      - 定位元素水平方向的位置由left和right两个属性控制
        通常情况下只会使用一个
    
      - left越大元素越靠右
    
      - right越大元素越靠左

```
.box1{
    width: 200px;
    height: 200px;
    background-color: #bfa;
}

.box2{
    width: 200px;
    height: 200px;
    background-color: orange;
    position: relative;
    left: 100px;
    top: -200px;

}

.box3{
    width: 200px;
    height: 200px;
    background-color: yellow;

}
```

```
<div class="box1">1</div>
<div class="box2">2</div>
<div class="box3">3</div>
```

![相对定位](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E7%9B%B8%E5%AF%B9%E5%AE%9A%E4%BD%8D.png)

### 3.绝对定位

- 当元素的position属性值设置为absolute时，则开启了元素的绝对定位
- 绝对定位的特点：
    - 开启绝对定位后，如果不设置偏移量元素的位置不会发生变化
    - 开启绝对定位后，元素会从文档流中脱离
    - 绝对定位会改变元素的性质，行内变成块，块的宽高被内容撑开
    - 绝对定位会使元素提升一个层级
    - 绝对定位元素是相对于其包含块进行定位的

#### 包含块( containing block )

- 正常情况下：
     包含块就是离当前元素最近的祖先块元素

     ```
     <div> <div></div> </div>
     <div><span><em>hello</em></span></div>
     ```

- 绝对定位的包含块:
  包含块就是离它最近的**开启了定位的祖先元素**，如果所有的祖先元素都没有开启定位则根元素就是它的包含块：html（根元素、初始包含块）

### 4.固定定位

- 将元素的position属性设置为fixed则开启了元素的固定定位
- 固定定位也是一种绝对定位，所以固定定位的大部分特点都和绝对定位一样，唯一不同的是固定定位永远参照于浏览器的视口进行定位，固定定位的元素不会随网页的滚动条滚动

### 5.粘滞定位

- 当元素的position属性设置为sticky时则开启了元素的粘滞定位
- 粘滞定位和相对定位的特点基本一致，不同的是粘滞定位可以在元素到达某个位置时将其固定

```
.nav{

    /* 设置宽度和高度 */
    width: 1210px;
    height: 48px;
    /* 设置背景颜色 */
    background-color: #E8E7E3;

    margin:100px auto;

     position: sticky; /*开启粘滞定位：当距离顶部为10px时位置固定*/
     top: 10px;

}

/* 设置nav中li */
.nav li{
    /* 设置li向左浮动，已使菜单横向排列 */
    float: left;
    /* 设置li的高度 */
    /* height: 48px; */
    /* 将文字在父元素中垂直居中 */
    line-height: 48px;

}

/* 设置a的样式 */
.nav a{
    /* 将a转换为块元素 */
    display: block;
    /* 去除下划线 */
    text-decoration: none;
    /* 设置字体颜色 */
    color: #777777;
    /* 修改字体大小 */
    font-size: 18px;

    padding: 0 39px;
}

.nav li:last-child a{
    padding: 0 42px 0 41px;
}

/* 设置鼠标移入的效果 */
.nav a:hover{
    background-color: #3F3F3F;
    color: #E8E7E3;
}
```

```
<!-- 创建导航条的结构 -->
<ul class="nav">
    <li>
        <a href="#">HTML/CSS</a>
    </li>
    <li>
        <a href="#">Browser Side</a>
    </li>
    <li>
        <a href="#">Server Side</a>
    </li>
    <li>
        <a href="#">Programming</a>
    </li>
    <li>
        <a href="#">XML</a>
    </li>
    <li>
        <a href="#">Web Building</a>
    </li>
    <li>
        <a href="#">Reference</a>
    </li>
</ul>
```

刚开始距离顶部有margin-top：100px的距离：

![粘滞定位开始](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E7%B2%98%E6%BB%9E%E5%AE%9A%E4%BD%8D%E5%BC%80%E5%A7%8B.png)

随着滚动条拖动，当距离顶部只有10px时位置将会固定住，后续滚动条再怎么拖动，其位置相对于浏览器视口都不会发生变化：

![粘滞定位变化](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E7%B2%98%E6%BB%9E%E5%AE%9A%E4%BD%8D%E5%8F%98%E5%8C%96.png)

### 5.绝对定位元素的布局

#### 当开启了绝对定位后：

水平方向的布局等式就需要添加left 和 right 两个值：

left + margin-left + border-left + padding-left + width + padding-right + border-right + margin-right + right = 包含块的内容区的宽度

- 此时规则和之前一样只是多添加了两个值，当发生过度约束：
  - 如果9个值中没有 auto 则自动调整right值以使等式满足
  - 如果有auto，则自动调整auto的值以使等式满足

    - 可设置auto的值：margin width left right
      
    
    因为left 和 right的值默认是auto，所以如果不指定left和right
    则等式不满足时，会自动调整这两个值

垂直方向布局的等式的也必须要满足：
    top + margin-top/bottom + padding-top/bottom + border-top/bottom + height = 包含块的高度

### 6.元素的层级

对于开启了定位元素，可以通过z-index属性来指定元素的层级：

z-index需要一个整数作为参数，值越大元素的层级越高，元素的层级越高越优先显示：

-  如果元素的层级一样，则优先显示靠下的元素

-  祖先的元素的层级再高也不会盖住后代元素

```
.box1{
    width: 200px;
    height: 200px;
    background-color: #bfa;
    position: absolute;
     /* z-index: 3; */
}

.box2{
    width: 200px;
    height: 200px;
    background-color: rgba(255 , 0, 0, .3);
    position: absolute;
    top: 50px;
    left: 50px;
    /* z-index: 3; */

}

.box3{
    width: 200px;
    height: 200px;
    background-color: yellow;
    position: absolute;
    top: 100px;
    left: 100px;
    z-index: 3;

}

.box4{
    width: 100px;
    height: 100px;
    background-color: orange;
    position: absolute;
}
```

```
<div class="box1">1</div>
<div class="box2">2</div>
<div class="box3">3
    <div class="box4">4</div>
</div>
```

![元素的层级](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E5%85%83%E7%B4%A0%E7%9A%84%E5%B1%82%E7%BA%A7.png)

## 六、font & background

### 1.字体

字体相关的样式 

- color 用来设置字体颜色

- font-size 字体的大小，和font-size相关的单位

  - em 相当于当前元素的一个font-size
  - rem 相对于根元素的一个font-size

- font-family 字体族（字体的格式）可选值：

  - serif  衬线字体

  - sans-serif 非衬线字体

  - monospace 等宽字体

    指定字体的类别，浏览器会自动使用该类别下的字体

- font-family可以同时指定多个字体，多个字体间使用,隔开。

  字体生效时优先使用第一个，第一个无法使用则使用第二个 以此类推：

  Microsoft YaHei,Heiti SC,tahoma,arial,Hiragino Sans GB,"\5B8B\4F53",sans-serif

#### font-face

可以将服务器中的字体直接提供给用户去使用，但是会产生一些问题：

1. 加载速度
2. 版权
3. 字体格式

```
<link rel="stylesheet" href="./fa/css/all.css">
```

```
@font-face {
        /* 指定字体的名字 */
    font-family:'myfont' ;
    /* 服务器中字体的路径 */
    src: url('./font/ZCOOLKuaiLe-Regular.ttf') format("truetype");/*指定字体的格式*/
}
```

```
p{
    color: blue;
    font-size: 40px;
    font-family: myfont;
}
```

```
<p>
    今天天气真不错，Hello Hello How are you！
</p>
```

![自定义字体](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E8%87%AA%E5%AE%9A%E4%B9%89%E5%AD%97%E4%BD%93.png)

### 2.图标字体

​	在网页中经常需要使用一些图标，可以通过图片来引入图标，但是图片大小本身比较大，并且非常的不灵活；所以在使用图标时，我们还可以将图标直接设置为字体，然后通过font-face的形式来对字体进行引入；这样我们就可以通过使用字体的形式来使用图标

fontawesome 使用步骤：

1. 下载 https://fontawesome.com/

2. 解压

3. 将css和webfonts移动到项目中

4. 将all.css引入到网页中

5. 使用图标字体：

   直接通过类名来使用图标字体
   class="fas fa-bell"
   class="fab fa-accessible-icon"

   其中 fas，fab指定自定义字体，fa-bel，fa-accessible-icon为字体中的某个具体字

```
<i class="fas fa-bell" style="font-size:80px; color:red;"></i>
<i class="fas fa-bell-slash"></i>
<i class="fab fa-accessible-icon"></i>
<i class="fas fa-otter" style="font-size: 160px; color:green;"></i>
```

![图标字体](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E5%9B%BE%E6%A0%87%E5%AD%97%E4%BD%93.png)

#### 通过伪元素设置图标字体

- 找到要设置图标的元素通过before或after选中
- 在content中设置字体的编码
- 设置字体的样式
      fab
      font-family: 'Font Awesome 5 Brands';

  		  fas
  		 font-family: 'Font Awesome 5 Free';
  		 font-weight: 900; 

```
<link rel="stylesheet" href="./fa/css/all.css">
<style>
    li{
        list-style: none;
    }

    li::before{
        content: '\f1b0';
        /* font-family: 'Font Awesome 5 Brands'; */
        font-family: 'Font Awesome 5 Free';
        font-weight: 900; 
        color: blue;
        margin-right: 10px;
    }
```

```
<ul>
    <li>锄禾日当午</li>
    <li>汗滴禾下土</li>
    <li>谁知盘中餐</li>
    <li>粒粒皆辛苦</li>
</ul>
```

![伪元素图标字体](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E4%BC%AA%E5%85%83%E7%B4%A0%E5%9B%BE%E6%A0%87%E5%AD%97%E4%BD%93.png)

#### 通过实体来使用图标字体

&#x图标的编码：

```
<span class="fas">&#xf0f3;</span>
```

![实体图标字体](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E5%AE%9E%E4%BD%93%E5%9B%BE%E6%A0%87%E5%AD%97%E4%BD%93.png)

### 3.阿里字体库

同样引入文件之后：

```
<link rel="stylesheet" href="./iconfont/iconfont.css">
```

既可以通过编码的形式显示目标字体，也可以通过类的形式显示：

```
<i class="iconfont">&#xe61c;</i>
<i class="iconfont">&#xe622;</i>
<i class="iconfont">&#xe623;</i>

<i class="iconfont icon-qitalaji"></i>
```

![阿里图标库](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E9%98%BF%E9%87%8C%E5%9B%BE%E6%A0%87%E5%BA%93.png)

### 4.行高

行高（line height）
- 行高指的是文字**占有的实际高度**

- 可以通过line-height来设置行高

     - 行高可以直接指定一个大小（px em）

     - 也可以直接为行高设置一个整数，如果是一个整数的话，行高将会是字体的指定的倍数

- 行高经常还用来设置文字的行间距：

  行间距 = 行高 - 字体大小

字体框

字体框就是**字体存在的格子**，设置font-size实际上就是在设置字体框的高度；

行高会在字体框的上下平均分配

**可以将行高设置为和高度一样的值，使单行文字在一个元素中垂直居中**

### 5.字体的简写属性

font 可以设置字体相关的所有属性，语法：

​	font: 字体大小/行高 字体族（行高 可以省略不写 如果不写使用默认值）

其它属性没有顺序要求：

font-weight 字重 （字体的加粗）可选值：

- normal 默认值 不加粗
- bold 加粗
- 100-900 九个级别（一般没什么用）

font-style （字体的风格）：

- normal 正常的
- italic 斜体

```
font: bold italic 50px/2  微软雅黑, 'Times New Roman', Times, serif;
```

### 6.文本的样式

#### text-align 

文本的水平对齐，可选值：

- left 左侧对齐
- right 右对齐
- center 居中对齐
- justify 两端对齐

#### vertical-align

设置元素垂直对齐的方式，可选值：

- baseline 默认值 基线对齐
- top 顶部对齐
- bottom 底部对齐
- middle 居中对齐

#### text-decoration 

设置文本修饰，可选值：

- none 什么都没有
- underline 下划线
- line-through 删除线
- overline 上划线

#### white-space 设置网页如何处理空白

可选值：

- normal 正常
- nowrap 不换行
- pre 保留空白

### 7.背景

#### background-color

设置背景颜色：

```
background-color: #bfa;
```

#### background-image

设置背景图片：

- 可以同时设置背景图片和背景颜色，这样背景颜色将会成为图片的背景色
- 如果背景的图片小于元素，则背景图片会自动在元素中平铺将元素铺满
- 如果背景的图片大于元素，将会一个部分背景无法完全显示
- 如果背景图片和元素一样大，则会直接正常显示

```
background-image: url("./img/1.png");
```

#### background-repeat

用来设置背景的重复方式，可选值：

- repeat 默认值 ， 背景会沿着x轴 y轴双方向重复
- repeat-x 沿着x轴方向重复
- repeat-y 沿着y轴方向重复
- no-repeat 背景图片不重复

#### background-position

用来设置背景图片的位置：

设置方式：
通过 top left right bottom center 几个表示方位的词来设置背景图片的位置，使用方位词时必须要同时指定两个值，如果只写一个则第二个默认就是center

通过偏移量来指定背景图片的位置：

```
background-position: -50px 300px;
```

​        水平方向的偏移量 垂直方向变量

#### background-clip

设置背景的范围，可选值：

- border-box 默认值，背景会出现在边框的下边
- padding-box 背景不会出现在边框，只出现在内容区和内边距
- content-box 背景只会出现在内容区

#### background-origin

背景图片的偏移量计算的原点：

- padding-box 默认值，background-position从内边距处开始计算
- content-box 背景图片的偏移量从内容区处计算
- border-box 背景图片的变量从边框处开始计算

#### background-size

设置背景图片的大小：

- 第一个值表示宽度 

- 第二个值表示高度

  如果只写一个，则第二个值默认是 auto

- cover 图片的比例不变，将元素铺满

- contain 图片比例不变，将图片在元素中完整显示

```
background-size: contain;
```

#### 简写属性

backgound，所有背景相关的样式都可以通过该样式来设置，并且该样式没有顺序要求，也没有哪个属性是必须写的

**注意**：

- background-size必须写在background-position的后边，并且使用/隔开
          background-position/background-size
- background-origin background-clip 两个样式 ，orgin要在clip的前边



## 七、表格与表单

### 1.表格

在现实生活中，经常需要使用表格来表示一些格式化数据：
    课程表、人名单、成绩单....

同样在网页中我们也需要使用表格，通过table标签来创建一个表格：

```
<table border="1" width='50%' align="center">
    <!-- 在table中使用tr表示表格中的一行，有几个tr就有几行 -->
    <tr>
        <!-- 在tr中使用td表示一个单元格，有几个td就有几个单元格 -->
        <td>A1</td>
        <td>B1</td>
        <td>C1</td>
        <td>D1</td>
    </tr>
    <tr>
        <td>A2</td>
        <td>B2</td>
        <td>C2</td>
        <!-- rowspan 纵向的合并单元格 -->
        <td rowspan="2">D2</td>
    </tr>
    <tr>
        <td>A3</td>
        <td>B3</td>
        <td>C3</td>
    </tr>
    <tr>
        <td>A4</td>
        <td>B4</td>
        <!-- 
            colspan 横向的合并单元格
         -->
        <td colspan="2">C4</td>
    </tr>
</table>
```

![表格](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E8%A1%A8%E6%A0%BC.png)

#### 长表格

可以将一个表格分成三个部分：

- 头部 thead

- 主体 tbody

- 底部 tfoot

  其中th 表示头部的单元格

```
<table border="1" width='50%' align="center">
    <thead>
        <tr>
            <th>日期</th>
            <th>收入</th>
            <th>支出</th>
            <th>合计</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>2000.1.1</td>
            <td>500</td>
            <td>200</td>
            <td>300</td>
        </tr>
        <tr>
            <td>2000.1.1</td>
            <td>500</td>
            <td>200</td>
            <td>300</td>
        </tr>
        <tr>
            <td>2000.1.1</td>
            <td>500</td>
            <td>200</td>
            <td>300</td>
        </tr>
        <tr>
            <td>2000.1.1</td>
            <td>500</td>
            <td>200</td>
            <td>300</td>
        </tr>
    </tbody>
    <tfoot>
        <tr>
            <td></td>
            <td></td>
            <td>合计</td>
            <td>300</td>
        </tr>
    </tfoot>

</table>
```

![image-20220328211256764](https://raw.githubusercontent.com/weixiaoyun/Images/html-%252B-css/image-20220328211256764.png)

#### 表格的样式

- border-spacing:  指定边框之间的距离
- border-collapse:  设置边框的合并
- display: table-cell   将元素设置为单元格td

```
    table{
        width: 50%;
        border: 1px solid black;
        margin: 0 auto;

        /* border-spacing: 指定边框之间的距离 */
        /* border-spacing: 0px; */

        /* border-collapse: collapse; 设置边框的合并 */
        border-collapse: collapse;
    }

    td{
        border: 1px solid black;
        height: 100px;
        /* 默认情况下元素在td中是垂直居中的 可以通过 vertical-align 来修改*/
        vertical-align:middle;
        text-align: center; 
    }

    /* 
        如果表格中没有使用tbody而是直接使用tr，
            那么浏览器会自动创建一个tbody，并且将tr全都放到tbody中
            tr不是table的子元素
     */
    tbody > tr:nth-child(odd){
        background-color: #bfa;
    }

    .box1{
        width: 300px;
        height: 300px;
        background-color: orange;

        /* 将元素设置为单元格 td  */
        display: table-cell;
        vertical-align: middle;

    }

    .box2{
        width: 100px;
        height: 100px;
        background-color: yellow;
        margin: 0 auto;

    }
</style>
```

```
   <div class="box1">
       <div class="box2"></div>
   </div>
   <table>
       <tr>
           <td>学号</td>
           <td>姓名</td>
           <td>性别</td>
           <td>年龄</td>
           <td>地址</td>
       </tr>
       <tr>
           <td>1</td>
           <td>孙悟空</td>
           <td>男</td>
           <td>18</td>
           <td>花果山</td>
       </tr>
       <tr>
           <td>2</td>
           <td>猪八戒</td>
           <td>男</td>
           <td>28</td>
           <td>高老庄</td>
       </tr>
       <tr>
           <td>3</td>
           <td>沙和尚</td>
           <td>男</td>
           <td>38</td>
           <td>流沙河</td>
       </tr>
       <tr>
           <td>4</td>
           <td>唐僧</td>
           <td>男</td>
           <td>16</td>
           <td>女儿国</td>
       </tr>
   </table>
```

![表格的样式](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E8%A1%A8%E6%A0%BC%E7%9A%84%E6%A0%B7%E5%BC%8F.png)

### 2.表单

- 在现实生活中表单用于提交数据
- 在网页中也可以使用表单，网页中的表单用于将本地的数据提交给远程的服务器
- 使用form标签来创建一个表单

```
<form action="target.html">
    <!--
       文本框
       注意：数据要提交到服务器中，必须要为元素指定一个name属性值
    -->
    文本框 <input type="text" name="username">
    <br><br>
    <!-- 
        密码框
     -->
    密码框 <input type="password" name="password">
    <br><br>

    <!--
         单选按钮
            - 像这种选择框，必须要指定一个value属性，value属性最终会作为用户的填写的值传递给服务器
            - checked 可以将单选按钮设置为默认选中
       -->
    单选按钮 <input type="radio" name="hello" value="a">
    <input type="radio" name="hello" value="b" checked>
    <br><br>

    <!-- 
        多选框
     -->
    多选框 <input type="checkbox" name="test" value="1">
    <input type="checkbox" name="test" value="2">
    <input type="checkbox" name="test" value="3" checked>

    <br><br>

    <!-- 下拉列表 -->
    <select name="haha">
        <option value="i">选项一</option>
        <option selected value="ii">选项二</option>
        <option value="iii">选项三</option>
    </select>



    <br><br>
    <!-- 
        提交按钮
     -->
    <input type="submit" value="注册">
</form>
```

![表单](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E8%A1%A8%E5%8D%95.png)

- autocomplete="off" 关闭自动补全
- readonly 将表单项设置为只读，数据会提交
- disabled 将表单项设置为禁用，数据不会提交
- autofocus 设置表单项自动获取焦点

```
<input type="text" name="username" value="hello" readonly>
<br><br>
<input type="text" name="username" autofocus>
```

## 八、HTML5的新特性

### 1.语义化标签

语义化标签使得页面的内容结构化，见名知义

| 标签                  | 描述                             |
| --------------------- | -------------------------------- |
| <hrader></header>     | 定义了文档的头部区域             |
| <footer></footer>     | 定义了文档的尾部区域             |
| <nav></nav>           | 定义文档的导航                   |
| <section></section>   | 定义文档中的节（section、区段）  |
| <article></article>   | 定义页面独立的内容区域           |
| <aside></aside>       | 定义页面的侧边栏内容             |
| <detailes></detailes> | 用于描述文档或文档某个部分的细节 |
| <summary></summary>   | 标签包含 details 元素的标题      |
| <dialog></dialog>     | 定义对话框，比如提示框           |

### 2.增强型表单

HTML5 拥有多个新的表单 Input 输入类型。这些新特性提供了更好的输入控制和验证：

| 输入类型       | 描述                         |
| -------------- | ---------------------------- |
| color          | 主要用于选取颜色             |
| date           | 从一个日期选择器选择一个日期 |
| datetime       | 选择一个日期（UTC 时间）     |
| datetime-local | 选择一个日期和时间 (无时区)  |
| email          | 包含 e-mail 地址的输入域     |
| month          | 选择一个月份                 |
| number         | 数值的输入域                 |
| range          | 一定范围内数字值的输入域     |
| search         | 用于搜索域                   |
| tel            | 定义输入电话号码字段         |
| time           | 选择一个时间                 |
| url            | URL 地址的输入域             |
| week           | 选择周和年                   |

HTML5 也新增以下表单元素：

| 表单元素   | 描述                                                         |
| ---------- | :----------------------------------------------------------- |
| <datalist> | 元素规定输入域的选项列表使用 <input> 元素的 list 属性与 <datalist> 元素的 id 绑定 |
| <keygen>   | 提供一种验证用户的可靠方法标签规定用于表单的密钥对生成器字段。 |
| <output>   | 用于不同类型的输出比如计算或脚本输出                         |

HTML5 新增的表单属性：

- placehoder 属性，简短的提示在用户输入值前会显示在输入域上。即我们常见的输入框默认提示，在用户输入后消失。

- required  属性，是一个 boolean 属性。要求填写的输入域不能为空
- pattern 属性，描述了一个正则表达式用于验证<input> 元素的值。
- min 和 max 属性，设置元素最小值与最大值。
- step 属性，为输入域规定合法的数字间隔。
- height 和 width 属性，用于 image 类型的 <input> 标签的图像高度和宽度。
- autofocus 属性，是一个 boolean 属性。规定在页面加载时，域自动地获得焦点。
- multiple 属性 ，是一个 boolean 属性。规定<input> 元素中可选择多个值。

### 3.音视频

#### audio

audio 标签用来向页面中引入一个外部的音频文件，音视频文件引入时，默认情况下不允许用户自己控制播放停止

属性：

- controls: 是否允许用户控制播放

- autoplay: 音频文件是否自动播放

  如果设置了autoplay 则音乐在打开页面时会自动播放，但是目前来讲大部分浏览器都不会自动对音乐进行播放 

   - loop: 音乐是否循环播放

```
<audio src="./source/audio.mp3" controls autoplay loop></audio> 
```

![音频1](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E9%9F%B3%E9%A2%911.png)

除了通过src来指定外部文件的路径以外，还可以通过source来指定文件的路径，可以同时指定多个文件，当第一个source不能用时则使用第二source，都不能用时则显示提示信息，可以借此解决兼容性问题:

```
<audio controls>
     对不起，您的浏览器不支持播放音频！请升级浏览器！ 
    <source src="./source/audio.mp3">
    <source src="./source/audio.ogg">
</audio>
```

对于IE8这种不支持audio标签的浏览器，会提示内部的文字信息：

![audioIE8](https://raw.githubusercontent.com/weixiaoyun/Images/html-%252B-css/audioIE8.png)

通过embed标签兼容IE8：

```
<audio controls>
<!--         对不起，您的浏览器不支持播放音频！请升级浏览器！-->
        <source src="./source/audio.mp3">
        <source src="./source/audio.ogg">
        <embed src="./source/audio.mp3" type="audio/mp3" width="300" height="100">
    </audio>
```

![embedIE8](https://raw.githubusercontent.com/weixiaoyun/Images/html-%252B-css/embedIE8.png)

#### video

使用方式和audio基本上是一样

```
<video controls>
    <source src="./source/flower.webm">
    <source src="./source/flower.mp4">
    <embed src="./source/flower.mp4" type="video/mp4">
</video>
```

![video1](https://raw.githubusercontent.com/weixiaoyun/Images/html-%252B-css/video1.png)

复制视频的通用代码，将其引入到自己的iframe当中，该处引用腾讯视频的通用代码：

```
<iframe frameborder="0" src="https://v.qq.com/txp/iframe/player.html?vid=b00318l66nt" allowFullScreen="true" width="500" height="300"></iframe>
```

![iframeVideo](https://raw.githubusercontent.com/weixiaoyun/Images/html-%252B-css/iframeVideo.png)

### 4.Canvas绘图

标签只是图形容器，必须使用脚本来绘制图形。

#### Canvas - 图形

1. 创建一个画布，一个画布在网页中是一个矩形框，通过 <canvas> 元素来绘制。默认情况下 元素没有边框和内容。

   ```
   <canvas id="myCanvas" width="200" height="100" style="border:1px solid #000000;"></canvas>
   ```

   标签通常需要指定一个id属性 (脚本中经常引用), width 和 height 属性定义的画布的大小，使用 style 属性来添加边框。可以在HTML页面中使用多个 <canvas> 元素

2. 使用Javascript来绘制图像，canvas 元素本身是没有绘图能力的。所有的绘制工作必须在 JavaScript 内部完成

   ```
   var c=document.getElementById("myCanvas");
   var ctx=c.getContext("2d");
   ctx.fillStyle="#FF0000";
   ctx.fillRect(0,0,150,75);
   ```

   - getContext("2d") 对象是内建的 HTML5 对象，拥有多种绘制路径、矩形、圆形、字符以及添加图像的方法。

   - 设置 fillStyle 属性可以是CSS颜色，渐变，或图案。fillStyle默认设置是#000000（黑色）。fillRect(x,y,width,height) 方法定义了矩形当前的填充方式。意思是：在画布上绘制 150x75 的矩形，从左上角开始 (0,0)。　

     ![canvas图形](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/canvas%E5%9B%BE%E5%BD%A2.png)

#### Canvas - 路径

在Canvas上画线，我们将使用以下两种方法：

- moveTo(*x,y*) 定义线条开始坐标
- lineTo(*x,y*) 定义线条结束坐标

绘制线条我们必须使用到 "ink" 的方法，就像stroke()。

```
var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");
ctx.moveTo(0,0);
ctx.lineTo(200,100);
ctx.stroke();
```

定义开始坐标(0,0), 和结束坐标 (200,100). 然后使用 stroke() 方法来绘制线条

![canvas路径](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/canvas%E8%B7%AF%E5%BE%84.png)

#### Canvas - 文本

使用 canvas 绘制文本，重要的属性和方法如下：

- font - 定义字体
- fillText(*text,x,y*) - 在 canvas 上绘制实心的文本
- strokeText(*text,x,y*) - 在 canvas 上绘制空心的文本

使用 fillText():

```
var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");
ctx.font="30px Arial";
ctx.fillText("Hello World",10,50);
```

使用 "Arial" 字体在画布上绘制一个高 30px 的文字（实心）

![canvas文本](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/canvas%E6%96%87%E6%9C%AC.png)

#### Canvas - 渐变

渐变可以填充在矩形, 圆形, 线条, 文本等等, 各种形状可以自己定义不同的颜色。

以下有两种不同的方式来设置Canvas渐变：

- createLinearGradient(*x,y,x1,y1*) - 创建线条渐变
- createRadialGradient(*x,y,r,x1,y1,r1*) - 创建一个径向/圆渐变

当我们使用渐变对象，必须使用两种或两种以上的停止颜色。

addColorStop()方法指定颜色停止，参数使用坐标来描述，可以是0至1.

使用渐变，设置fillStyle或strokeStyle的值为渐变，然后绘制形状，如矩形，文本，或一条线。

```
var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");

// Create gradient
var grd=ctx.createLinearGradient(0,0,200,0);
grd.addColorStop(0,"red");
grd.addColorStop(1,"white");

// Fill with gradient
ctx.fillStyle=grd;
ctx.fillRect(10,10,150,80);
```

创建了一个线性渐变，使用渐变填充矩形

![canvas渐变](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/canvas%E6%B8%90%E5%8F%98.png)

#### Canvas - 图像

把一幅图像放置到画布上, 使用 drawImage(*image,x,y*) 方法

```
var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");
var img=document.getElementById("scream");
ctx.drawImage(img,10,10);
```

把一幅图像放置到了画布上

### 5.SVG绘图

- SVG 是一种使用 XML 描述 2D 图形的语言。
- Canvas 通过 JavaScript 来绘制 2D 图形。
- SVG 基于 XML，这意味着 SVG DOM 中的每个元素都是可用的。可以为某个元素附加 JavaScript 事件处理器。
- 在 SVG 中，每个被绘制的图形均被视为对象。如果 SVG 对象的属性发生变化，那么浏览器能够自动重现图形。
- Canvas 是逐像素进行渲染的。在 canvas 中，一旦图形被绘制完成，它就不会继续得到浏览器的关注。如果其位置发生变化，那么整个场景也需要重新绘制，包括任何或许已被图形覆盖的对象。

### 6.地理定位

HTML5 Geolocation（地理定位）用于定位用户的位置。

```
window.navigator.geolocation {
    getCurrentPosition:  fn  用于获取当前的位置数据
    watchPosition: fn  监视用户位置的改变
    clearWatch: fn  清除定位监视
}
```

获取用户定位信息：

```
navigator.geolocation.getCurrentPosition(
    function(pos){
        console.log('用户定位数据获取成功')
        //console.log(arguments);
        console.log('定位时间：',pos.timestamp)
        console.log('经度：',pos.coords.longitude)
        console.log('纬度：',pos.coords.latitude)
        console.log('海拔：',pos.coords.altitude)
        console.log('速度：',pos.coords.speed)

    },    //定位成功的回调
    function(err){
        console.log('用户定位数据获取失败')
        //console.log(arguments);

    }        //定位失败的回调
)
```

![地理定位](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E5%9C%B0%E7%90%86%E5%AE%9A%E4%BD%8D.png)

### 7.拖放API

- 拖放是一种常见的特性，即抓取对象以后拖到另一个位置。在 HTML5 中，拖放是标准的一部分，任何元素都能够拖放。
- 拖放的过程分为源对象和目标对象。源对象是指你即将拖动元素，而目标对象则是指拖动之后要放置的目标位置。

**拖放的源对象(可能发生移动的)可以触发的事件——3个**：

- dragstart：拖动开始
- drag：拖动中
- dragend：拖动结束

整个拖动过程的组成： dragstart*1 + drag*n + *dragend*1*

**拖放的目标对象(不会发生移动)可以触发的事件——4个**：

- dragenter：拖动着进入
- dragover：拖动着悬停
- dragleave：拖动着离开
- drop：释放

整个拖动过程的组成1： dragenter*1 + dragover*n + *dragleave*1*

整个拖动过程的组成2： dragenter*1 + dragover*n + *drop*1*

**dataTransfer：用于数据传递的“拖拉机”对象；**

-  在拖动源对象事件中使用e.dataTransfer属性保存数据：e.dataTransfer.setData( k,  v )

-  在拖动目标对象事件中使用e.dataTransfer属性读取数据：

  var value = e.dataTransfer.getData( k )

### 8.WebWorker

- 当在 HTML 页面中执行脚本时，页面的状态是不可响应的，直到脚本已完成。

- web worker 是运行在后台的 JavaScript，独立于其他脚本，不会影响页面的性能。您可以继续做任何愿意做的事情：点击、选取内容等等，而此时 web worker 在后台运行。

- 首先检测浏览器是否支持 Web Worker

  ```
  if(typeof(Worker)!=="undefined"){
      console.log('支持Web Worker！')
  }else{
      console.log('抱歉! Web Worker 不支持')
  }
  ```

  ![支持webworker](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E6%94%AF%E6%8C%81webworker.png)

- 下面的代码检测是否存在 worker，如果不存在，- 它会创建一个新的 web worker 对象，然后运行 "demo_workers.js" 中的代码

  ```
  if(typeof(w)=="undefined")
  {
      w=new Worker("demo_workers.js");
  }
  ```

- 然后就可以从 web worker 发送和接收消息了。向 web worker 添加一个 "onmessage" 事件监听器：

  ```
  w.onmessage=function(event){
      document.getElementById("result").innerHTML=event.data;
  };
  ```

  - 当 web worker 传递消息时，会执行事件监听器中的代码。event.data 中存有来自 event.data 的数据。当我们创建 web worker 对象后，它会继续监听消息（即使在外部脚本完成之后）直到其被终止为止。

  - 如需终止 web worker，并释放浏览器/计算机资源，使用 terminate() 方法。

#### 完整的Web Worker实例代码

```
<!DOCTYPE html>
<html>
<body>

<p>Count numbers: <output id="result"></output></p>
<button onclick="startWorker()">Start Worker</button>
<button onclick="stopWorker()">Stop Worker</button>
<br><br>

<script>
    var w;

    function startWorker()
    {
        if(typeof(Worker)!=="undefined")
        {
            if(typeof(w)=="undefined")
            {
                w=new Worker("demo_workers.js");
            }
            w.onmessage = function (event) {
                document.getElementById("result").innerHTML=event.data;
            };
        }
        else
        {
            document.getElementById("result").innerHTML="Sorry, your browser does not support Web Workers...";
        }
    }

    function stopWorker()
    {
        w.terminate();
    }
</script>

</body>
</html>
```

创建的计数脚本，该脚本存储于 "demo_workers.js" 文件中：

```
var i=0;

function timedCount()
{
    i=i+1;
    postMessage(i);
    setTimeout("timedCount()",500);
}

timedCount();
```

![WebWorker计数脚本](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/WebWorker%E8%AE%A1%E6%95%B0%E8%84%9A%E6%9C%AC.png)

### 9.Web Storage

使用HTML5可以在本地存储用户的浏览数据。早些时候,本地存储使用的是cookies。但是Web 存储需要更加的安全与快速. 这些数据不会被保存在服务器上，但是这些数据只用于用户请求网站数据上.它也可以存储大量的数据，而不影响网站的性能。数据以 键/值 对存在, web网页的数据只允许该网页访问使用。

客户端存储数据的两个对象为：

- localStorage - 没有时间限制的数据存储

- sessionStorage - 针对一个 session 的数据存储, 当用户关闭浏览器窗口后，数据会被删除。

在使用 web 存储前,应检查浏览器是否支持 localStorage 和sessionStorage

```
if(typeof(Storage)!=="undefined")
{
    console.log('是的! 支持 localStorage  sessionStorage 对象!')
    // 一些代码.....
}
else
{
    console.log('抱歉! 不支持 web 存储。')
}
```

![检查支持storage](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E6%A3%80%E6%9F%A5%E6%94%AF%E6%8C%81storage.png)

不管是 localStorage，还是 sessionStorage，可使用的API都相同，常用的有如下几个（以localStorage为例）：

- 保存数据：localStorage.setItem(key,value);
- 读取数据：localStorage.getItem(key);
- 删除单个数据：localStorage.removeItem(key);
- 删除所有数据：localStorage.clear();
- 得到某个索引的key：localStorage.key(index);

- 

### 10.WebSocket

WebSocket是HTML5开始提供的一种在单个 TCP 连接上进行全双工通讯的协议。在WebSocket API中，浏览器和服务器只需要做一个握手的动作，然后，浏览器和服务器之间就形成了一条快速通道。两者之间就直接可以数据互相传送。浏览器通过 JavaScript 向服务器发出建立 WebSocket 连接的请求，连接建立以后，客户端和服务器端就可以通过 TCP 连接直接交换数据。当你获取 Web Socket 连接后，你可以通过 **send()** 方法来向服务器发送数据，并通过 **onmessage** 事件来接收服务器返回的数据。

```
<!DOCTYPE HTML>
<html>
<head>
    <meta charset="utf-8">
    <title>W3Cschool教程(w3cschool.cn)</title>

    <script type="text/javascript">
        function WebSocketTest()
        {
            if ("WebSocket" in window)
            {
                alert("您的浏览器支持 WebSocket!");

                // 打开一个 web socket
                var ws = new WebSocket("ws://localhost:9998/echo");

                ws.onopen = function()
                {
                    // Web Socket 已连接上，使用 send() 方法发送数据
                    ws.send("发送数据");
                    alert("数据发送中...");
                };

                ws.onmessage = function (evt)
                {
                    var received_msg = evt.data;
                    alert("数据已接收...");
                };

                ws.onclose = function()
                {
                    // 关闭 websocket
                    alert("连接已关闭...");
                };
            }

            else
            {
                // 浏览器不支持 WebSocket
                alert("您的浏览器不支持 WebSocket!");
            }
        }
    </script>

</head>
<body>

<div id="sse">
    <a href="javascript:WebSocketTest()">运行 WebSocket</a>
</div>

</body>
</html>
```

![WebSocket](https://raw.githubusercontent.com/weixiaoyun/Images/html-%252B-css/WebSocket.png)

## 九、CSS3新特性

### 1.CSS3选择器

| 选择器                                                       | 示例                  | 示例说明                                                  | CSS  |
| :----------------------------------------------------------- | :-------------------- | :-------------------------------------------------------- | :--- |
| [.*class*](http://www.runoob.com/cssref/sel-class.html)      | .intro                | 选择所有class="intro"的元素                               | 1    |
| [#*id*](http://www.runoob.com/cssref/sel-id.html)            | #firstname            | 选择所有id="firstname"的元素                              | 1    |
| [*](http://www.runoob.com/cssref/sel-all.html)               | *                     | 选择所有元素                                              | 2    |
| *[element](http://www.runoob.com/cssref/sel-element.html)*   | p                     | 选择所有<p>元素                                           | 1    |
| *[element,element](http://www.runoob.com/cssref/sel-element-comma.html)* | div,p                 | 选择所有<div>元素和<p>元素                                | 1    |
| [*element* *element*](http://www.runoob.com/cssref/sel-element-element.html) | div p                 | 选择<div>元素内的所有<p>元素                              | 1    |
| [*element*>*element*](http://www.runoob.com/cssref/sel-element-gt.html) | div>p                 | 选择所有父级是 <div> 元素的 <p> 元素                      | 2    |
| [*element*+*element*](http://www.runoob.com/cssref/sel-element-pluss.html) | div+p                 | 选择所有紧接着<div>元素之后的<p>元素                      | 2    |
| [[*attribute*\]](http://www.runoob.com/cssref/sel-attribute.html) | [target]              | 选择所有带有target属性元素                                | 2    |
| [[*attribute*=*value*\]](http://www.runoob.com/cssref/sel-attribute-value.html) | [target=-blank]       | 选择所有使用target="-blank"的元素                         | 2    |
| [[*attribute*~=*value*\]](http://www.runoob.com/cssref/sel-attribute-value-contains.html) | [title~=flower]       | 选择标题属性包含单词"flower"的所有元素                    | 2    |
| [[*attribute*\|=*language*\]](http://www.runoob.com/cssref/sel-attribute-value-lang.html) | [lang\|=en]           | 选择一个lang属性的起始值="EN"的所有元素                   | 2    |
| [:link](http://www.runoob.com/cssref/sel-link.html)          | a:link                | 选择所有未访问链接                                        | 1    |
| [:visited](http://www.runoob.com/cssref/sel-visited.html)    | a:visited             | 选择所有访问过的链接                                      | 1    |
| [:active](http://www.runoob.com/cssref/sel-active.html)      | a:active              | 选择活动链接                                              | 1    |
| [:hover](http://www.runoob.com/cssref/sel-hover.html)        | a:hover               | 选择鼠标在链接上面时                                      | 1    |
| [:focus](http://www.runoob.com/cssref/sel-focus.html)        | input:focus           | 选择具有焦点的输入元素                                    | 2    |
| [:first-letter](http://www.runoob.com/cssref/sel-firstletter.html) | p:first-letter        | 选择每一个<P>元素的第一个字母                             | 1    |
| [:first-line](http://www.runoob.com/cssref/sel-firstline.html) | p:first-line          | 选择每一个<P>元素的第一行                                 | 1    |
| [:first-child](http://www.runoob.com/cssref/sel-firstchild.html) | p:first-child         | 指定只有当<p>元素是其父级的第一个子级的样式。             | 2    |
| [:before](http://www.runoob.com/cssref/sel-before.html)      | p:before              | 在每个<p>元素之前插入内容                                 | 2    |
| [:after](http://www.runoob.com/cssref/sel-after.html)        | p:after               | 在每个<p>元素之后插入内容                                 | 2    |
| [:lang(*language*)](http://www.runoob.com/cssref/sel-lang.html) | p:lang(it)            | 选择一个lang属性的起始值="it"的所有<p>元素                | 2    |
| [*element1*~*element2*](http://www.runoob.com/cssref/sel-gen-sibling.html) | p~ul                  | 选择p元素之后的每一个ul元素                               | 3    |
| [[*attribute*^=*value*\]](http://www.runoob.com/cssref/sel-attr-begin.html) | a[src^="https"]       | 选择每一个src属性的值以"https"开头的元素                  | 3    |
| [[*attribute*$=*value*\]](http://www.runoob.com/cssref/sel-attr-end.html) | a[src$=".pdf"]        | 选择每一个src属性的值以".pdf"结尾的元素                   | 3    |
| [[*attribute**=*value*\]](http://www.runoob.com/cssref/sel-attr-contain.html) | a[src*="44lan"]       | 选择每一个src属性的值包含子字符串"44lan"的元素            | 3    |
| [:first-of-type](http://www.runoob.com/cssref/sel-first-of-type.html) | p:first-of-type       | 选择每个p元素是其父级的第一个p元素                        | 3    |
| [:last-of-type](http://www.runoob.com/cssref/sel-last-of-type.html) | p:last-of-type        | 选择每个p元素是其父级的最后一个p元素                      | 3    |
| [:only-of-type](http://www.runoob.com/cssref/sel-only-of-type.html) | p:only-of-type        | 选择每个p元素是其父级的唯一p元素                          | 3    |
| [:only-child](http://www.runoob.com/cssref/sel-only-child.html) | p:only-child          | 选择每个p元素是其父级的唯一子元素                         | 3    |
| [:nth-child(*n*)](http://www.runoob.com/cssref/sel-nth-child.html) | p:nth-child(2)        | 选择每个p元素是其父级的第二个子元素                       | 3    |
| [:nth-last-child(*n*)](http://www.runoob.com/cssref/sel-nth-last-child.html) | p:nth-last-child(2)   | 选择每个p元素的是其父级的第二个子元素，从最后一个子项计数 | 3    |
| [:nth-of-type(*n*)](http://www.runoob.com/cssref/sel-nth-of-type.html) | p:nth-of-type(2)      | 选择每个p元素是其父级的第二个p元素                        | 3    |
| [:nth-last-of-type(*n*)](http://www.runoob.com/cssref/sel-nth-last-of-type.html) | p:nth-last-of-type(2) | 选择每个p元素的是其父级的第二个p元素，从最后一个子项计数  | 3    |
| [:last-child](http://www.runoob.com/cssref/sel-last-child.html) | p:last-child          | 选择每个p元素是其父级的最后一个子级。                     | 3    |
| [:root](http://www.runoob.com/cssref/sel-root.html)          | :root                 | 选择文档的根元素                                          | 3    |
| [:empty](http://www.runoob.com/cssref/sel-empty.html)        | p:empty               | 选择每个没有任何子级的p元素（包括文本节点）               | 3    |
| [:target](http://www.runoob.com/cssref/sel-target.html)      | #news:target          | 选择当前活动的#news元素（包含该锚名称的点击的URL）        | 3    |
| [:enabled](http://www.runoob.com/cssref/sel-enabled.html)    | input:enabled         | 选择每一个已启用的输入元素                                | 3    |
| [:disabled](http://www.runoob.com/cssref/sel-disabled.html)  | input:disabled        | 选择每一个禁用的输入元素                                  | 3    |
| [:checked](http://www.runoob.com/cssref/sel-checked.html)    | input:checked         | 选择每个选中的输入元素                                    | 3    |
| [:not(*selector*)](http://www.runoob.com/cssref/sel-not.html) | :not(p)               | 选择每个并非p元素的元素                                   | 3    |
| [::selection](http://www.runoob.com/cssref/sel-selection.html) | ::selection           | 匹配元素中被用户选中或处于高亮状态的部分                  | 3    |
| [:out-of-range](http://www.runoob.com/cssref/sel-out-of-range.html) | :out-of-range         | 匹配值在指定区间之外的input元素                           | 3    |
| [:in-range](http://www.runoob.com/cssref/sel-in-range.html)  | :in-range             | 匹配值在指定区间之内的input元素                           | 3    |
| [:read-write](http://www.runoob.com/cssref/sel-read-write.html) | :read-write           | 用于匹配可读及可写的元素                                  | 3    |
| [:read-only](http://www.runoob.com/cssref/sel-read-only.html) | :read-only            | 用于匹配设置 "readonly"（只读） 属性的元素                | 3    |
| [:optional](http://www.runoob.com/cssref/sel-optional.html)  | :optional             | 用于匹配可选的输入元素                                    | 3    |
| [:required](http://www.runoob.com/cssref/sel-required.html)  | :required             | 用于匹配设置了 "required" 属性的元素                      | 3    |
| [:valid](http://www.runoob.com/cssref/sel-valid.html)        | :valid                | 用于匹配输入值为合法的元素                                | 3    |
| [:invalid](http://www.runoob.com/cssref/sel-invalid.html)    | :invalid              | 用于匹配输入值为非法的元素                                | 3    |

可以参考第二章中的伪类选择器和伪元素选择器

### 2.CSS3边框

用CSS3，你可以创建圆角边框，添加阴影框，并作为边界的形象而不使用设计程序：

| 属性                                                         | 说明                                           | CSS  |
| :----------------------------------------------------------- | :--------------------------------------------- | :--- |
| [border-image](http://www.runoob.com/cssref/css3-pr-border-image.html) | 设置所有边框图像的速记属性。                   | 3    |
| [border-radius](http://www.runoob.com/cssref/css3-pr-border-radius.html) | 一个用于设置所有四个边框- *-半径属性的速记属性 | 3    |
| [box-shadow](http://www.runoob.com/cssref/css3-pr-box-shadow.html) | 附加一个或多个下拉框的阴影                     | 3    |

#### box-shadow

用来设置元素的阴影效果，阴影不会影响页面布局

- 第一个值 水平偏移量 设置阴影的水平位置 正值向右移动 负值向左移动
- 第二个值 垂直偏移量 设置阴影的水平位置 正值向下移动 负值向上移动
- 第三个值 阴影的模糊半径
- 第四个值 阴影的颜色

```
box-shadow: 0px 0px 50px rgba(0, 0, 0, .3) ;
```

![阴影](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E9%98%B4%E5%BD%B1.png)

**outline**

用来设置元素的轮廓线，用法和border一模一样,轮廓和边框不同的点，就是轮廓不会影响到可见框的大小

#### border-radius

用来设置圆角(圆角设置的圆的半径大小),border-radius 可以分别指定四个角的圆角:

- 四个值 左上 右上 右下 左下
- 三个值 左上 右上/左下 右下
- 两个值 左上/右下 右上/左下

```
border-radius: 20px / 40px; 
```

或者分别设置：

```
/* border-top-left-radius:  */
/* border-top-right-radius */
/* border-bottom-left-radius:  */
/* border-bottom-right-radius:  */
 border-top-left-radius:50px 100px;
```

用百分比设置：

```
/* 将元素设置为一个圆形 */
border-radius: 50%;
```

![圆角](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E5%9C%86%E8%A7%92.png)

#### border-image

指定作为div元素周围边框的图像，border-image属性是速记属性用于设置border-image-source，border-image-slice，border-image-width，border-image-outset和border-image-repeat的值：

```
border-image: source slice width outset repeat|initial|inherit;
```

其中：

- border-image-source：用于指定要用于绘制边框的图像的位置；
- border-image-slice：图像边界向内偏移；
- border-image-width： 图像边界的宽度；
- border-image-outset：用于指定在边框外部绘制 border-image-area 的量
- border-image-repeat： 用于设置图像边界是否应重复（repeat）、拉伸（stretch）或铺满（round）。

```
<p id="borderimg1">在这里，图像平铺（重复），以填补该地区。</p>
<p id="borderimg2">在这里，图像被拉伸以填补该地区</p>
```

```
#borderimg1 {
    border: 10px solid transparent;
    padding: 15px;
    -webkit-border-image: url(border.png) 30 round; /* Safari 3.1-5 */
    -o-border-image: url(border.png) 30 round; /* Opera 11-12.1 */
    border-image: url(border.png) 30 round;
}

#borderimg2 {
    border: 10px solid transparent;
    padding: 15px;
    -webkit-border-image: url(border.png) 30 stretch; /* Safari 3.1-5 */
    -o-border-image: url(border.png) 30 stretch; /* Opera 11-12.1 */
    border-image: url(border.png) 30 stretch;
}
```

![边框图](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E8%BE%B9%E6%A1%86%E5%9B%BE.png)

这是原始图片：

![原始图片](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E5%8E%9F%E5%A7%8B%E5%9B%BE%E7%89%87.png)

### 3.CSS3背景

 CSS3中包含几个新的背景属性，提供更大背景元素控制。

| 顺序                                                         | 描述                     | CSS  |
| :----------------------------------------------------------- | :----------------------- | :--- |
| [background-clip](http://www.runoob.com/cssref/css3-pr-background-clip.html) | 规定背景的绘制区域。     | 3    |
| [background-origin](http://www.runoob.com/cssref/css3-pr-background-origin.html) | 规定背景图片的定位区域。 | 3    |
| [background-size](http://www.runoob.com/cssref/css3-pr-background-size.html) | 规定背景图片的尺寸。     | 3    |

#### background-clip

background-clip属性指定背景绘制区域，语法：

```
background-clip: border-box|padding-box|content-box;
```

- border-box: 默认值。背景绘制在边框方框内（剪切成边框方框）
- padding-box: 背景绘制在衬距方框内（剪切成衬距方框）
- content-box: 背景绘制在内容方框内（剪切成内容方框）

```
<p>没有背景剪裁 (border-box没有定义):</p>
<div class="example1">
    <h2>感谢他的痛苦</h2>
    <p>痛苦本身就是爱</p>
</div>

<p>background-clip: padding-box:</p>
<div class="example2">
    <h2>感谢他的痛苦</h2>
    <p>痛苦本身就是爱</p>
</div>

<p>background-clip: content-box:</p>
<div class="example3">
    <h2>感谢他的痛苦</h2>
    <p>痛苦本身就是爱</p>
</div>
```

```
<style>
    .example1 {
        border: 10px dotted black;
        padding:35px;
        background: yellow;
    }

    .example2 {
        border: 10px dotted black;
        padding:35px;
        background: yellow;
        background-clip: padding-box;
    }

    .example3 {
        border: 10px dotted black;
        padding:35px;
        background: yellow;
        background-clip: content-box;
    }
</style>
```

![background-clip](https://raw.githubusercontent.com/weixiaoyun/Images/html-%252B-css/background-clip.png)

#### background-origin

相对于内容框来定位背景图像，语法：

```
background-origin: padding-box|border-box|content-box;
```

- padding-box: 背景图像填充框的相对位置;
- border-box: 背景图像边界框的相对位置;
- content-box: 背景图像的相对位置的内容框

```
<p>背景图像边界框的相对位置：</p>
<div id="div1">
    Lorem ipsum dolor sit amet, consectetuer adipiscing elit, sed diam nonummy nibh euismod tincidunt ut laoreet dolore magna aliquam erat volutpat. Ut wisi enim ad minim veniam, quis nostrud exerci tation ullamcorper suscipit lobortis nisl ut aliquip ex ea commodo consequat.
</div>

<p>背景图像的相对位置的内容框：</p>
<div id="div2">
    Lorem ipsum dolor sit amet, consectetuer adipiscing elit, sed diam nonummy nibh euismod tincidunt ut laoreet dolore magna aliquam erat volutpat. Ut wisi enim ad minim veniam, quis nostrud exerci tation ullamcorper suscipit lobortis nisl ut aliquip ex ea commodo consequat.
</div>
```

```
div
{
    border:1px solid black;
    padding:35px;
    background-image:url('smiley.gif');
    background-repeat:no-repeat;
    background-position:left;
}
#div1
{
    background-origin:border-box;
}
#div2
{
    background-origin:content-box;
}
```

![background-origin](https://raw.githubusercontent.com/weixiaoyun/Images/html-%252B-css/background-origin.png)

#### background-size

background-size属性指定背景图片大小，语法：

```
background-size: length|percentage|cover|contain;
```

- length：设置背景图片高度和宽度。第一个值设置宽度，第二个值设置的高度。如果只给出一个值，第二个是设置为 **auto**(自动)
- percentage：将计算相对于背景定位区域的百分比。第一个值设置宽度，第二个值设置的高度。如果只给出一个值，第二个是设置为"auto(自动)"
- cover：此时会保持图像的纵横比并将图像缩放成将完全覆盖背景定位区域的最小大小。
- contain：此时会保持图像的纵横比并将图像缩放成将适合背景定位区域的最大大小。

```
<p>
    Lorem ipsum，中文又称“乱数假文”， 是指一篇常用于排版设计领域的拉丁文文章 ，主要的目的为测试文章或文字在不同字型、版型下看起来的效果。
</p>

<p>原始图片: <img src="/try/demo_source/img_flwr.gif"  alt="Flowers" width="224" height="162"></p>
```

```
body{
    background:url(/try/demo_source/img_flwr.gif);
    background-size:80px 60px;
    background-repeat:no-repeat;
    padding-top:40px;
}
```

![background-size](https://raw.githubusercontent.com/weixiaoyun/Images/html-%252B-css/background-size.png)

### 4.CSS3渐变

通过渐变可以设置一些复杂的背景颜色，可以实现从一个颜色向其他颜色过渡

的效果

#### 线性渐变

颜色沿着一条直线变化，linear-gradient()

linear-gradient(red,yellow) 红色在开头，黄色在结尾，中间是过渡区域

- 线性渐变的开头，我们可以指定一个渐变的方向
  - to left
  - to right
  - to bottom
  - to top
  - deg deg表示度数
  - turn 表示圈
- 渐变可以同时指定多个颜色，多个颜色默认情况下平均分布，
  也可以手动指定渐变的分布情况

repeating-linear-gradient()： 可以平铺的线性渐变

通过渐变可以设置一些复杂的背景颜色，可以实现从一个颜色向其他颜色过渡的效果，**渐变是图片，需要通过background-image来设置**：

```
background-image: repeating-linear-gradient(to right ,red, yellow 50px);
```

![线性渐变](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E7%BA%BF%E6%80%A7%E6%B8%90%E5%8F%98.png)

#### 径向渐变(放射性的效果)

- 默认情况下径向渐变的形状根据元素的形状来计算的

  - 正方形 --> 圆形

  - 长方形 --> 椭圆形

   - 也可以手动指定径向渐变的大小

   - circle

     - ellipse

   - 也可以指定渐变的位置

     语法：

     radial-gradient(大小 at 位置, 颜色 位置 ,颜色 位置 ,颜色 位置)

     - 大小：

       circle 圆形

       ellipse 椭圆

       closest-side 近边

       closest-corner 近角

       farthest-side 远边

       farthest-corner 远角

     - 位置：

       top right left center bottom

```
background-image: radial-gradient(farthest-side at 100px 100px, red , #bfa)
```

![径向渐变](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E5%BE%84%E5%90%91%E6%B8%90%E5%8F%98.png)

### 5.CSS3文本效果

| 属性                                                         | 描述                                                    | CSS  |
| :----------------------------------------------------------- | :------------------------------------------------------ | :--- |
| [hanging-punctuation](http://www.runoob.com/cssref/css3-pr-hanging-punctuation.html) | 规定标点字符是否位于线框之外。                          | 3    |
| [punctuation-trim](http://www.runoob.com/cssref/css3-pr-punctuation-trim.html) | 规定是否对标点字符进行修剪。                            | 3    |
| text-align-last                                              | 设置如何对齐最后一行或紧挨着强制换行符之前的行。        | 3    |
| text-emphasis                                                | 向元素的文本应用重点标记以及重点标记的前景色。          | 3    |
| [text-justify](http://www.runoob.com/cssref/css3-pr-text-justify.html) | 规定当 text-align 设置为 "justify" 时所使用的对齐方法。 | 3    |
| [text-outline](http://www.runoob.com/cssref/css3-pr-text-outline.html) | 规定文本的轮廓。                                        | 3    |
| [text-overflow](http://www.runoob.com/cssref/css3-pr-text-overflow.html) | 规定当文本溢出包含元素时发生的事情。                    | 3    |
| [text-shadow](http://www.runoob.com/cssref/css3-pr-text-shadow.html) | 向文本添加阴影。                                        | 3    |
| [text-wrap](http://www.runoob.com/cssref/css3-pr-text-wrap.html) | 规定文本的换行规则。                                    | 3    |
| [word-break](http://www.runoob.com/cssref/css3-pr-word-break.html) | 规定非中日韩文本的换行规则。                            | 3    |
| [word-wrap](http://www.runoob.com/cssref/css3-pr-word-wrap.html) | 允许对长的不可分割的单词进行分割并换行到下一行。        | 3    |

### 6.CSS3字体

 以前CSS3的版本，网页设计师不得不使用用户计算机上已经安装的字体。使用CSS3，网页设计师可以使用他/她喜欢的任何字体。当你发现您要使用的字体文件时，只需简单的将字体文件包含在网站中，它会自动下载给需要的用户。所选择的字体在新的CSS3版本有关于@font-face规则描述。"自己的"的字体是在 CSS3 @font-face 规则中定义的。

**详情可参考第六章字体——@font-face**

### 7.过渡

- 通过过渡可以指定一个属性发生变化时的切换方式
- 通过过渡可以创建一些非常好的效果，提升用户的体验

#### transition-property

指定要执行过渡的属性：

多个属性间使用,隔开 ；如果所有属性都需要过渡，则使用all关键字；大部分属性都支持过渡效果，注意过渡时必须是从一个有效数值向另外一个有效数值进行过渡。

```
transition-property: height , width; 
transition-property: all;
```

#### transition-duration

指定过渡效果的持续时间：时间单位：s 和 ms  1s = 1000ms

```
transition-duration: 100ms; 
transition-duration: 2s; 
```

#### transition-timing-function

过渡的时序函数：

ease 默认值，慢速开始，先加速，再减速

- linear 匀速运动
- ease-in 加速运动
- ease-out 减速运动
- ease-in-out 先加速 后减速
- cubic-bezier() 来指定时序函数
      https://cubic-bezier.com
- steps() 分步执行过渡效果（通过分步实现动画效果）
   可以设置一个第二个值：
          end ， 在时间结束时执行过渡(默认值)
          start ， 在时间开始时执行过渡

```
transition-timing-function: cubic-bezier(.24,.95,.82,-0.88); 
transition-timing-function: steps(2, start); 
```

#### transition-delay

过渡效果的延迟，等待一段时间后在执行过渡

```
transition-delay: 2s;
```

#### transition

可以同时设置过渡相关的所有属性，只有一个要求，如果要写延迟，则两个时间中第一个是持续时间，第二个是延迟

```
transition:2s margin-left 1s cubic-bezier(.24,.95,.82,-0.88);
```

```
.box1{
    width: 800px;
    height: 800px;
    background-color: silver;
    overflow: hidden;
}

.box1 div{
    width: 100px;
    height: 100px;
    margin-bottom: 100px;
    margin-left: 0;

}

.box2{
    background-color: #bfa;
     transition:2s margin-left 1s cubic-bezier(.24,.95,.82,-0.88);
}

.box3{
    background-color: orange;
    transition-property: all;
    transition-duration: 2s;
}

.box1:hover div{
    margin-left: 700px;
}
```

```
<div class="box1">
    <div class="box2"></div>
    <div class="box3"></div>
</div>
```



![过渡](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E8%BF%87%E6%B8%A1.gif)

### 8.动画

- 动画和过渡类似，都是可以实现一些动态的效果
- 不同的是过渡需要在某个属性发生变化时才会触发，动画可以自动触发动态效果   
- 设置动画效果，必须先要设置一个关键帧，关键帧设置了动画执行每一个步骤

#### animation-name

要对当前元素生效的关键帧的名字

```
animation-name: test;
```

#### animation-duration

动画的执行时间

```
animation-duration: 4s;
```

#### animation-delay

动画的延时

```
animation-delay: 2s;
```

#### animation-timing-function

动画的时序函数

```
animation-timing-function: ease-in-out;
```

#### animation-iteration-count

动画执行的次数，可选值：

- 次数
- infinite 无限执行

```
animation-iteration-count: 1;
```

#### animation-direction

指定动画运行的方向，可选值：

- normal 默认值  从 from 向 to运行 每次都是这样 
- reverse 从 to 向 from 运行 每次都是这样 
- alternate 从 from 向 to运行 重复执行动画时反向执行
- alternate-reverse 从 to 向 from运行 重复执行动画时反向执行

```
animation-direction: alternate-reverse;
```

#### animation-play-state

设置动画的执行状态，可选值：

- running 默认值 动画执行
- paused 动画暂停

达到通过鼠标移入来控制动画暂停的效果

```
.box1:hover div{
    animation-play-state: paused;
}
```

#### animation-fill-mode

动画的填充模式，可选值：

- none 默认值 动画执行完毕元素回到原来位置
- forwards 动画执行完毕元素会停止在动画结束的位置
- backwards 动画延时等待时，元素就会处于开始位置（即在延时之前就处于from的状态）
- both 结合了forwards 和 backwards，即延时之前就处于开始的from状态，结束之后停止在动画结束的位置

```
.box1{
    width: 800px;
    height: 800px;
    background-color: silver;
    overflow: hidden;
}

.box1 div{
    width: 100px;
    height: 100px;
    margin-bottom: 100px;
    margin-left: 10px;
    
}

.box2{
    background-color: #bfa;
    animation: test 2s 2 1s alternate;

    
}

.box1:hover div{
    animation-play-state: paused;
}


@keyframes test {
    /* from表示动画的开始位置 也可以使用 0% */
    from{
        margin-left: 0;
        background-color: orange;
    } 

    /* to动画的结束位置 也可以使用100%*/
    to{
        background-color: red;
        margin-left: 700px;
    }
}
```

```
<div class="box1">
    <div class="box2"></div>
</div>
```

![动画](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E5%8A%A8%E7%94%BB.gif)

### 9.变形

变形就是指通过CSS来改变元素的形状或位置

- 变形不会影响到页面的布局

- transform 用来设置元素的变形效果

  平移：

  - translateX() 沿着x轴方向平移

  - translateY() 沿着y轴方向平移

  - translateZ() 沿着z轴方向平移

    当设置百分比时，平移元素的百分比是相对于自身计算的
    

```
transform: translateX(100%);
```

#### z轴平移

- 调整元素在z轴的位置，正常情况就是调整元素和人眼之间的距离，距离越大，元素离人越近
- z轴平移属于立体效果（近大远小），默认情况下网页是不支持透视，如果需要看见效果，必须要设置网页的视距

```
html{
    /* 设置当前网页的视距为800px，人眼距离网页的距离 */
    perspective: 800px;
}
```

```
.box1{
    width: 200px;
    height: 200px;
    background-color: #bfa;
    margin: 200px auto;
    transition:2s;
}

body:hover .box1{
    transform: translateZ(100px);
}
```

#### transform-origin

变形的原点，默认值：center

```
transform-origin:20px 20px; 
```

### 10.旋转

通过旋转可以使元素沿着x y 或 z旋转指定的角度

- rotateX()
- rotateY()
- rotateZ()

```
transform: rotateZ(.25turn); 
transform: rotateY(180deg) translateZ(400px); 
transform: translateZ(400px) rotateY(180deg) ; 
```

#### backface-visibility

是否显示元素的背面

```
backface-visibility: hidden;
```

### 11.缩放

- scaleX() 水平方向缩放
- scaleY() 垂直方向缩放
- scale() 双方向的缩放

```
.box1:hover{
    transform:scale(2)
}
```

```
.box1{
    width: 100px;
    height: 100px;
    background-color: #bfa;
    transition:2s;
    margin: 100px auto;
}
```

```
<div class="box1"></div>
```

![缩放](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E7%BC%A9%E6%94%BE.gif)

### 12.CSS多列

下表列出了所有 CSS3 的多列属性：

| 属性                                                         | 描述                                     |
| :----------------------------------------------------------- | :--------------------------------------- |
| [column-count](http://www.runoob.com/cssref/css3-pr-column-count.html) | 指定元素应该被分割的列数。               |
| [column-fill](http://www.runoob.com/cssref/css3-pr-column-fill.html) | 指定如何填充列                           |
| [column-gap](http://www.runoob.com/cssref/css3-pr-column-gap.html) | 指定列与列之间的间隙                     |
| [column-rule](http://www.runoob.com/cssref/css3-pr-column-rule.html) | 所有 column-rule-* 属性的简写            |
| [column-rule-color](http://www.runoob.com/cssref/css3-pr-column-rule-color.html) | 指定两列间边框的颜色                     |
| [column-rule-style](http://www.runoob.com/cssref/css3-pr-column-rule-style.html) | 指定两列间边框的样式                     |
| [column-rule-width](http://www.runoob.com/cssref/css3-pr-column-rule-width.html) | 指定两列间边框的厚度                     |
| [column-span](http://www.runoob.com/cssref/css3-pr-column-span.html) | 指定元素要跨越多少列                     |
| [column-width](http://www.runoob.com/cssref/css3-pr-column-width.html) | 指定列的宽度                             |
| [columns](http://www.runoob.com/cssref/css3-pr-columns.html) | 设置 column-width 和 column-count 的简写 |

### 13.CSS3盒模型

 在 CSS3 中, 增加了一些新的用户界面特性来调整元素尺寸，框尺寸和外边框，主要包括以下用户界面属性：

- resize：none | both | horizontal | vertical | inherit
- box-sizing: content-box | border-box | inherit
- outline:outline-color outline-style outline-width outine-offset

resize属性指定一个元素是否应该由用户去调整大小。

box-sizing 属性允许您以确切的方式定义适应某个区域的具体内容。

outline-offset 属性对轮廓进行偏移，并在超出边框边缘的位置绘制轮廓。

### 14.弹性盒

**详情参考第十一章flex**

### 15.CSS多媒体查询

**详情参考第十三章媒体查询**

## 十、less

- less是一个css的增强版，通过less可以编写更少的代码实现更强大的样式
- 在less中添加了许多的新特性：像对变量的支持、对mixin的支持... ...
- less的语法大体上和css语法一致，但是less中增添了许多对css的扩展，所以浏览器无法直接执行less代码，要执行必须向将less转换为css，然后再由浏览器执行

### 1.在less中所有的数值都可以直接进行运算

```
.box1{
    // + - * /
    width: 100px + 100px;
    height: 100px/2;
    background-color: #bfa;
    
}
```

### 2.将选择器嵌套

```
body{
    width: 100px;
    height: 100px;
    
    div{
        color: red;
    }
}
```

### 3.less中的注释

css中的注释，内容会被解析到css文件中；less中的单行注释，注释中的内容不会被解析到css中

### 4.变量

在变量中可以存储一个任意的值，并且我们可以在需要时，任意的修改变量中的值。变量的语法： @变量名

- 使用变量时，如果是直接使用则以 @变量名 的形式使用即可
- 作为类名或者一部分值使用时必须以 @{变量名} 的形式使用
- 变量发生重名时，会优先使用比较近的变量
- 可以在变量声明前就使用变量

```
@a:200px;
@b:#bfa;
@c:box6;

.box5{
    //使用变量是，如果是直接使用则以 @变量名 的形式使用即可
    width: @a;
    color:@b;
}

//作为类名，或者一部分值使用时必须以 @{变量名} 的形式使用
.@{c}{
    width: @a;
    background-image: url("@{c}/1.png");
}

@d:200px;
@d:300px;

div{
    // 变量发生重名时，会优先使用比较近的变量
    @d:115px;
    width: @d;
    height: @e;
}

//可以在变量声明前就使用变量
@e:335px;
```

### 5.&

& 表示外层的父元素

```
.box1{
    .box2{
        color: red;
    }

    >.box3{
        color: red;

        &:hover{
            color: blue;
        }
    }

    //为box1设置一个hover
    &:hover{
        color: orange;
    }

    div &{
        width: 100px;
    }
}
```

### 6.mixin混合

直接对指定的样式进行引用

#### 创建mixin

```
.p1{
    width: 100px;
    height: 200px;
}
```

```
.p3{
    //这里就相当于将p1的样式在这里进行了复制
    //mixin 混合
    .p1();
}
```

```
// 使用类选择器时可以在选择器后边添加一个括号，这时我们实际上就创建了一个mixins
.p4(){
    width: 100px;
    height: 100px;
}
```

```
.p5{
    .p4;
}
```

#### 在混合函数中设置变量

```
//在混合函数中可以直接设置变量
.test(@w:100px,@h:200px,@bg-color:red){
    width: @w;
    height: @h;
    border: 1px solid @bg-color;
}

div{
    //调用混合函数，按顺序传递参数
    // .test(200px,300px,#bfa);
    .test(300px);
    // .test(@bg-color:red, @h:100px, @w:300px);
}
```

### 7. :extend()

对当前选择器扩展指定选择器的样式（选择器分组）

```
.p1{
    width: 100px;
    height: 200px;
}
```

```
.p2:extend(.p1){
    color: red;
}
```

## 十一、flex

### 1.弹性盒

flex(弹性盒、伸缩盒)
- 是CSS中的又一种布局手段，它主要用来代替浮动来完成页面的布局

- flex可以使元素具有弹性，让元素可以跟随页面的大小的改变而改变

- 弹性容器

     - 要使用弹性盒，必须先将一个元素设置为弹性容器

     - 通过 display 来设置弹性容器

         display:flex  设置为块级弹性容器

         display:inline-flex 设置为行内的弹性容器

- 弹性元素

     - 弹性容器的子元素是弹性元素（弹性项）
     - 弹性元素可以同时是弹性容器

#### 弹性元素的属性

弹性元素的属性：

flex-grow 指定弹性元素的伸展的系数

- 当父元素有多余空间的时，子元素如何伸展
- 父元素的剩余空间，会按照比例进行分配

flex-shrink 指定弹性元素的收缩系数

​	当父元素中的空间不足以容纳所有的子元素时，如何对子元素进行收缩

flex-direction 指定容器中弹性元素的排列方式，可选值：

- row 默认值，弹性元素在容器中水平排列（左向右）

  主轴 自左向右

- row-reverse 弹性元素在容器中反向水平排列（右向左）

  主轴 自右向左

- column 弹性元素纵向排列（自上向下）

- column-reverse 弹性元素方向纵向排列（自下向上）

 主轴：

​	弹性元素的排列方向称为主轴

 侧轴：

​	与主轴垂直方向的称为侧轴

```
ul{
    width: 500px;
    border: 10px red solid;
    display: flex;
    flex-direction: row;
}

li{
    width: 200px;
    height: 100px;
    background-color: #bfa;
    font-size: 50px;
    text-align: center;
    line-height: 100px;
    flex-shrink: 0;

    
}
li:nth-child(1){
    flex-grow: 0;
    flex-shrink: 1;
}

li:nth-child(2){
    background-color: pink;
    flex-shrink: 2;
}

li:nth-child(3){
    background-color: orange;
    flex-shrink: 3;
}
```

```
<ul>
    <li>1</li>
    <li>2</li>
    <li>3</li>
</ul>
```

![弹性元素](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E5%BC%B9%E6%80%A7%E5%85%83%E7%B4%A0.png)

### 2.弹性容器的样式

#### flex-wrap

设置弹性元素是否在弹性容器中自动换行，可选值：

- nowrap 默认值，元素不会自动换行
- wrap 元素沿着辅轴方向自动换行
- wrap-reverse 元素沿着辅轴反方向换行

#### flex-flow

direction 和wrap的简写属性：

```
flex-flow: row wrap;
```

#### justify-content

如何分配主轴上的空白空间（主轴上的元素如何排列），可选值：

- flex-start 元素沿着主轴起边排列
- flex-end 元素沿着主轴终边排列
- center 元素居中排列
- space-around 空白分布到元素两侧
- space-between 空白均匀分布到元素间
- space-evenly 空白分布到元素的单侧

#### align-items

- 元素在辅轴上如何对齐
- 元素间的关系
- 可选值：
    - stretch 默认值，将元素的长度设置为相同的值
    - flex-start 元素不会拉伸，沿着辅轴起边对齐
    - flex-end 沿着辅轴的终边对齐
    - center 居中对齐
    - baseline 基线对齐

#### align-self

用来覆盖当前弹性元素上的align-items

#### align-content

辅轴空白空间的分布

```
ul{
    width: 600px;
    height: 800px;
    border: 10px red solid;
     align-items: stretch;
     /* align-content: 辅轴空白空间的分布 */
     align-content: space-between;

}

li{
    width: 200px;
    background-color: #bfa;
    font-size: 50px;
    text-align: center;
    line-height: 100px;
    flex-shrink: 0;



}
li:nth-child(1){
    /* align-self: 用来覆盖当前弹性元素上的align-items */
    align-self: stretch;
}

li:nth-child(2){
    background-color: pink;
}

li:nth-child(3){
    background-color: orange;
}

li:nth-child(4){
    background-color: yellow;
}

li:nth-child(5){
    background-color: chocolate;
}
```

```
<ul>
    <li>1</li>
    <li>
        2
       <div>2</div>
    </li>
    <li>
        3
        <div>3</div>
        <div>3</div>
   </li>

   <li>1</li>

   <li>
           2
          <div>2</div>
       </li>
</ul>
```

![弹性盒辅轴](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E5%BC%B9%E6%80%A7%E7%9B%92%E8%BE%85%E8%BD%B4.png)

### 3.弹性元素的样式

#### flex-basis

指定的是元素在主轴上的基础长度，如果主轴是 横向的 则 该值指定的就是元素的宽度；如果主轴是 纵向的 则 该值指定的是就是元素的高度

- 默认值是 auto，表示参考元素自身的高度或宽度
- 如果传递了一个具体的数值，则以该值为准

#### flex

可以设置弹性元素所有的三个样式，flex 增长 缩减 基础;

- initial "flex: 0 1 auto".
- auto  "flex: 1 1 auto"
- none "flex: 0 0 auto" 弹性元素没有弹性

#### order

决定弹性元素的排列顺序：

```
ul{
    width: 900px;
    border: 10px red solid;
    /* 设置弹性盒 */
    display: flex;

}

li{
    width: 200px;
    height: 100px;
    background-color: #bfa;
    font-size: 50px;
    text-align: center;
    line-height: 100px;
    flex: initial;

    
}
li:nth-child(1){
    /* order 决定弹性元素的排列顺序 */
    order: 2;
}

li:nth-child(2){
    background-color: pink;
    order: 3;
}

li:nth-child(3){
    background-color: orange;
    order: 1;
}
```

```
<ul>
    <li>1</li>
    <li>2</li>
    <li>3</li>
</ul>
```

![弹性盒排序](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/%E5%BC%B9%E6%80%A7%E7%9B%92%E6%8E%92%E5%BA%8F.png)

## 十二、像素

### 1.像素

- 屏幕是由一个一个发光的小点构成，这一个个的小点就是像素
- 分辨率：1920 x 1080 说的就是屏幕中小点的数量
- 在前端开发中像素要分成两种情况讨论：CSS像素 和 物理像素
- 物理像素，上述所说的小点点就属于物理像素
- CSS像素，编写网页时，我们所用像素都是CSS像素
    - 浏览器在显示网页时，需要将CSS像素转换为物理像素然后再呈现
    - 一个css像素最终由几个物理像素显示，由浏览器决定：
        默认情况下在pc端，一个css像素 = 一个物理像素

### 2.视口（viewport）

- 视口就是屏幕中用来显示网页的区域
- 可以通过查看视口的大小，来观察CSS像素和物理像素的比值
- 默认情况下：
    - 视口宽度 1920px（CSS像素）
    - 1920px（物理像素）
    - 此时，css像素和物理像素的比是 1:1
- 放大两倍的情况：
    - 视口宽度 960px（CSS像素）
    - 1920px（物理像素）
    - 此时，css像素和物理像素的比是1:2
- 我们可以通过改变视口的大小，来改变CSS像素和物理像素的比值

### 3.移动端的像素

在不同的屏幕中，单位像素的大小是不同的，像素越小屏幕会越清晰

- 24寸 1920x1080
- i6 4.7寸 750 x 1334

智能手机的像素点 远远小于 计算机的像素点

**问题：一个宽度为900px的网页在iphone6中要如何显示呢？**

​	默认情况下，移动端的网页都会将视口设置为980像素（css像素），以确保pc端网页可以在移动端正常访问，但是如果网页的宽度超过了980，移动端的浏览器会自动对网页缩放以完整显示网页

​    https://material.io/resources/devices/

​    所以基本大部分的pc端网站都可以在移动端中正常浏览，但是往往都不会有一个好的体验，为了解决这个问题，大部分网站都会专门为移动端设计网页

### 4.移动端的视口

移动端默认的视口大小是980px(css像素)，

默认情况下，移动端的像素比就是  980/移动端宽度  （980/750），如果我们直接在网页中编写移动端代码，这样在980的视口下，像素比是非常不好，
导致网页中的内容非常非常的小。

编写移动页面时，必须要确保有一个比较合理的像素比：

​	1css像素 对应 2个物理像素

​	1css像素 对应 3个物理像素

- 可以通过meta标签来设置视口大小

- 每一款移动设备设计时，都会有一个最佳的像素比，一般我们只需要将像素比设置为该值即可得到一个最佳效果。将像素比设置为最佳像素比的视口大小我们称其为完美视口

  将网页的视口设置为完美视口
  
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

### 4.视口的其他介绍

不同的设备完美视口的大小是不一样的

- iphone6 -- 375
- iphone6plus -- 414

由于不同设备视口和像素比不同，所以同样的375个像素在不同的设备下意义是不一样，比如在iphone6中 375就是全屏，而到了plus中375就会缺一块。

所以在移动端开发时，就不能再使用px来进行布局了

**vw** 表示的是视口的宽度（viewport width）

- 100vw = 一个视口的宽度
- 1vw = 1%视口宽度

​    vw这个单位永远相当于视口宽度进行计算，例如：

​    设计图的宽度：750px 1125px

​    设计图 ：750px  

​    使用vw作为单位：100vw

​    那么创建一个 48px x 35px 大小的元素：

​	100vw = 750px(设计图的像素) 0.1333333333333333vw = 1px

​	6.4vw = 48px(设计图像素)

​	4.667vw = 35px

### 5.vw适配

```
html{
    /* 
        网页中字体大小最小是12px，不能设置一个比12像素还小的字体
            如果我们设置了一个小于12px的字体，则字体自动设置为12

        0.1333333vw = 1px

        5.3333vw = 40px
    */
    font-size: 5.3333vw;
}

.box1{
    /* 
        rem
            - 1 rem = 1 html的字体大小
            - 1 rem = 40 px(设计图)
    */
    width: 18.75rem;
    height: 0.875rem;
    background-color: #bfa;
}
```

```
<div class="box1"></div>
```

![VW适配](https://raw.githubusercontent.com/weixiaoyun/Images/html-%2B-css/VW%E9%80%82%E9%85%8D.png)

### 6.响应式布局

- 网页可以根据不同的设备或窗口大小呈现出不同的效果
- 使用响应式布局，可以使一个网页适用于所有设备
- 响应布局的关键就是 媒体查询
- 通过媒体查询，可以为不同的设备，或设备不同状态来分别设置样式

使用媒体查询，语法： @media 查询规则{}
媒体类型：

- all 所有设备
- print 打印设备
- screen 带屏幕的设备
- speech 屏幕阅读器

可以使用,连接多个媒体类型，这样它们之间就是一个或的关系

可以在媒体类型前添加一个only，表示只有。（only的使用主要是为了兼容一些老版本浏览器）

```
 @media print,screen{
    body{
        background-color: #bfa;
    }
} 

@media only screen {
    body{
        background-color: #bfa;
    }
}
```

## 十三、媒体查询

媒体特性：

- width 视口的宽度
- height 视口的高度
- min-width 视口的最小宽度（视口大于指定宽度时生效）
- max-width 视口的最大宽度（视口小于指定宽度时生效）

```
 @media (max-width: 500px){
    body{
       background-color: #bfa;
    }
} 
```

样式切换的分界点，我们称其为断点，也就是网页的样式会在这个点时发生变化，一般比较常用的断点

- 小于768 超小屏幕 max-width=768px
- 大于768 小屏幕   min-width=768px
- 大于992 中型屏幕 min-width=992px
- 大于1200 大屏幕  min-width=1200px

```
@media only screen and (min-width: 500px) and (max-width:700px){
    body{
       background-color: #bfa;
    }
}
```
