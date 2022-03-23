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
