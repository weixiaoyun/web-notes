# HTML5 + CSS3

## 一、HTML

### 1.实体

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

### 2.meta标签

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
