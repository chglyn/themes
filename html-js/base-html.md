#### 前言：

对HTML页面标签内容进行简单总结，在这里做个简单笔记汇总。

页面头部的desc字段: **网站是关于什么内容的，对本站点的描述。**

页面头部的keywords字段: **告诉搜索爬虫引擎，网站是关于什么内容的。**

#### 有序列表与无序列表

有序列表：

```
<ol>
	<li>demo</li>
</ol>
```

可以设置序号从第几开始，添加start字段即可：

```
<ol start="10">
	<li>demo</li>
</ol>
```
无序列表：

```
<ul>
	<li>demo</li>
</ul>
```

在无序列表中使用 type 属性：

```
<ul>
	<li type="fruits">app</li>
</ul>
```

在 HTML 4.01 中，不赞成 type 属性；在 XHTML 1.0 Strict DTD 中，不支持 type 属性。请使用 CSS 代替。

#### a标签

* 在页面中当作超链接使用：

```
<a href="/404.html">...</a>
```

* 在页面中当作锚点使用：

```
<a href="#Id">...</a>
```

* 在页面中调起电话使用：

```
<a href="tel:130XXXXXXXX">...</a>
```

* 在页面中调起邮件使用：

```
<a href="mailto:liu@xxx.com">...</a>
```

* 在页面中协议限定符：

```
<a href="javascript:while(1){alert(1)}">...</a>
```

#### 主流浏览器内核

|  主流浏览器   | 内核  |
|  ----  | ----  |
| Firefox  | Gecko |
| Chrome  | Webkit /Blink |
| IE  | Trident |
| Safari  | Webkit |
| Opera  | Presto |


cascading style sheet
/* (darryring roseonly) */
引入方式
	1、行间样式
	2、页面级
	3、外链
选择器
	id
	class
	标签
顺序：
	!important > 行间样式 > id > class | 属性 > 标签选择器 > 通配符
css权重
	!important   --> Infinity
	行间样式	--> 1000
	id 	--> 100
	class | 属性 | 伪类	 --> 10
	标签 | 伪元素 --> 1
	通配符 -->  0
 	
 	原理：
		id，100并不是指id的一个权重值就是100，实际上这个100是一个进制数，不是2进制，也不是10进制；而是256进制，
		就是0到255后+1才是1。列如：通配符的权重值0到标签、伪元素的权重值1，中时间实际上差了255。依次类推。
	1、父子选择器 div span
	2、直接选择器 div > span
	3、并列选择器 div.class
	4、分组选择器 span, div

	font-family:arial(arial --> 乔布斯研发)

	1、土鳖式（纯英文）
		color:red;
	2、颜色代码
		color:#0000ff (16进制)
	3、颜色函数
		color:rgb(0-255, 0-255, 0-255);

	border:1px solid red; --> border-width + border-style + border-color
	//border-left-color
	//transparent 透明色

	1em = 16px;
伪类
	a:hover
	...
行内元素(内联) inline
	feature 内容决定元素所占位置
		不可以通过css改变宽高
	span strong em a del
块级元素 block
	feature 独占一行
		可以通过css改变宽高
	div p ul ol li form address
行级块元素 inline-block
	feature 内容决定大小
		以改宽高
	img
	<!--
		凡是带有inline的元素，都有文字特性 留白间距
		文本分隔符 元素与元素直接有空白间隔
	-->

盒子模型 margin + border + padding + content(width + height)
	盒子壁 border
	内边距 padding
	盒内容 width + height
	
	盒子可视区域  border + padding + width/height
定位技术
	position: relative | absolute | fixed | static
	relative 相对定位 保留原来位置进行定位 相对于自己原来的位置进行定位
	absolute 绝对定位 脱离原来位置进行定位 相对于最近有定位的父级进行定位；如果没有，相对于文档进行定位
	**** 上下左右居中 设置50%，margin自身的一半
常识
	body有个默认的8像素 margin值

两栏布局
	<div class="right"></div>
	<div class="left"></div>
	注意以上布局顺序
	.right{width:100px;height:100px;background-color:yellow;position:absolute;top:0;right:0;}
	.left{ height:100px;background-color:blue; margin-right:100px;}
margin塌陷
	垂直方向上父子上的margin，取最大的那个值
	解决：
		1、给父级添加border-top属性
		2、BFC（给父级改变渲染规则）
			如何触发一个盒子BFC
				1、position:absoulte
				2、display:inline-block
				3、float:left/right
				4、overflow:hidden

	margin塌陷添加css
	margin合并添加html
float模型
	left/right
	1、浮动元素产生了浮动流（只有块级元素会产生）
	所有产生了浮动流的元素，块级元素看不到他们
	产生了BFC的元素和文本类属性的元素以及文本都能看到浮动元素（带有inline属性的都属于文本类属性）
	<!-- 清除周边浮动在父级元素添加一个标签，设置使用clear:both 不推荐 -->
	伪元素(inline属性) ::before{content:'';clear:both;display:block;}
	content只能适用于伪元素，添加clear清除必须是块级元素所以添加block属性
文字溢出
	单行文本 三件套 *** white-space:nowrap overflow:hidden text-overflow:ellipsis
	多行文本 只做截断

图片处理
	1、text-indent:设置超过盒子宽; overflow:hidden; white-space:nowrap
	2、height:0;设置padding-top:设置一个高度;overflow:hidden;
元素嵌套规则
	行级元素只能嵌套行级元素
	块级元素可以嵌套任何元素 
	p标签特殊、a标签不能嵌套a标签

	常识
		凡是设置position:absoulte;float:left/right 打内部把元素转化成inline-block;
		图片环绕文字 图片设置float:left
		行内元素设置行块级属性里面文字和外面文字上对齐，使用vertical-align;
		行内元素里面文字和外面文字底对齐


