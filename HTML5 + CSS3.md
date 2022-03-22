# HTML5 + CSS3

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

#### 标题标签：

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

####  属性：

- src 属性指定的是外部图片的路径（路径规则和超链接是一样的）

- alt 图片的描述，这个描述默认情况下不会显示，有些浏览器会图片无法加载时显示， 搜索引擎会根据alt中的内容来识别图片，如果不写alt属性则图片不会被搜索引擎所收录

- width 图片的宽度 (单位是像素)

- height 图片的高度

  ​    宽度和高度中如果只修改了一个，则另一个会等比例缩放

- 注意：

   一般情况在pc端，不建议修改图片的大小，需要多大的图片就裁多大

  但是在移动端，经常需要对图片进行缩放（大图缩小）

#### 图片的格式：

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

### 14.音视频

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

除了通过src来指定外部文件的路径以外，还可以通过source来指定文件的路径，可以同时指定多个文件，当第一个source不能用时则使用第二个source，都不能用时则显示提示信息，可以借此解决兼容性问题:

```
<audio controls>
     对不起，您的浏览器不支持播放音频！请升级浏览器！ 
    <source src="./source/audio.mp3">
    <source src="./source/audio.ogg">
</audio>
```

对于IE8这种不支持audio标签的浏览器，会提示内部的文字信息：

![IE8audio](https://raw.githubusercontent.com/weixiaoyun/Images/html-%252B-css/IE8audio.png)

通过embed标签兼容IE8：

```
<audio controls>
<!--         对不起，您的浏览器不支持播放音频！请升级浏览器！-->
        <source src="./source/audio.mp3">
        <source src="./source/audio.ogg">
        <embed src="./source/audio.mp3" type="audio/mp3" width="300" height="100">
    </audio>
```

![IE8embed](https://raw.githubusercontent.com/weixiaoyun/Images/html-%252B-css/IE8embed.png)

#### video

使用方式和audio基本上是一样

```
<video controls>
    <source src="./source/flower.webm">
    <source src="./source/flower.mp4">
    <embed src="./source/flower.mp4" type="video/mp4">
</video>
```

![video](https://raw.githubusercontent.com/weixiaoyun/Images/html-%252B-css/video.png)

复制视频的通用代码，将其引入到自己的iframe当中，该处引用腾讯视频的通用代码：

```
<iframe frameborder="0" src="https://v.qq.com/txp/iframe/player.html?vid=b00318l66nt" allowFullScreen="true" width="500" height="300"></iframe>
```

![ifvideo](https://raw.githubusercontent.com/weixiaoyun/Images/html-%252B-css/ifvideo.png)
