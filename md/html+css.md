# html&css规范

浏览器兼容ie8+，如要使用动画，则采用优雅降级处理ie8，9效果。

## html规范

### 基础

- 使用html5文档申明
- 尽量使用更加语义化的html5标签，参考：[Sections and Outlines of an HTML5 Document](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/Sections_and_Outlines_of_an_HTML5_document)，考虑到`ie8`不支持html5标签，可以引入html5.js
- 若需支持响应式设计（pc+pad）,则需要为ie8引入[respond.js](https://github.com/scottjehl/Respond)
- 一般按照从上至下、从左到右的视觉顺序书写HTML结构，但有时候为了便于搜索引擎抓取或布局考虑，我们也会不按照视觉顺序书写
- HTML标签名、属性名必须全部采用小写，属性必须加引号，并且必须闭合，单标签也必须闭合，如：`<input type=”text” />`、`<br />`	
- 结构(html)，表现(css)，行为(js)相分离，避免直接将css或js写在标签结构里
- 标签挂靠的class不要过多，最多别超过4个
- 请不要在内联元素中嵌入块级元素，如span里面有div标签，a里面包裹h2等(h5 a元素可以嵌套块级元素)
- ul/ol的直接子元素只能是li
- 数据类内容，大胆的使用table
- a元素提供title属性，img提供alt属性，如果img大小固定，请记得使用width和height属性（如`<img src="" alt="" width="200" height="100" />`）
- 页面中不要使用&nbsp进行缩进，如需缩进，使用CSS的text-indent来控制，如text-indent:2em用于中文的缩进两个空格
- js操作属性，请以`data-`为前缀
- i标签用于图标

### 注释

采用类似标签闭合的写法，与HTML统一格式；注释文案两头空格 。 允许只有开始注释！

	<!-- header -->
	<div class="header">
	    <div class="inner-center"></div>
	</div>
	<!-- /header -->

### 常用结构

#### 空白模板

	<!doctype html>
	<html>
	<head>
		<meta charset="UTF-8">
		<meta name="renderer" content="webkit">
		<meta http-equiv="X-UA-Compatible" content="IE=edge" />
		<meta name="keywords" content="">
		<meta name="description" content="">
		<meta name="viewport" content="width=device-width, initial-scale=1, user-scalable=no" />
		<meta content="yes" name="apple-mobile-web-app-capable"/>
	 	<meta content="black" name="apple-mobile-web-app-status-bar-style"/>
		<meta name="format-detection"content="telephone=no,email=no"/>
		<title>page title</title>
	    <!--[if lt IE 9]>
	    	<script src="js/html5-respond.js"></script>
	    <![endif]-->
	</head>
	<body></body>
	</html>

#### 常规布局

一般来说header和footer可能有全屏背景，所以居中部分添加`.inner-center`，container我们可以设计成全屏或居中，而其余的全屏部分我们可以独立出来，与header，container等并列，如全屏的滚动图片

	header.header>.inner-center^
	[section.featured>.inner-center^]
	div.container.clearfix>aside.aside-left+main.main.clearfix+aside.aside-right^^
	footer.footer>.inner-center

#### 区块

边栏区块，特殊化区块请使用`.x-block`或`.aside-block--xxx`

	.aside-block>.block-hd>h3.block-tt+.block-bd

内容区块，特殊化区块请使用`.x-block`或`.section-block--xxx`

	.section-block>.block-hd>h2.block-tt+.block-bd

#### 等分

	//两列等分
	.col-half.clearfix>.col-block*2>(.block-hd>h2.block-tt)+.block-bd
	//三列等分
	.col-third.clearfix>.col-block*3>(.block-hd>h2.block-tt)+.block-bd
	//四列等分
	.col-quarter.clearfix>.col-block*4>(.block-hd>h2.block-tt)+.block-bd

### 常用html转义符

- space空格(`&nbsp;`)
- 1个汉字空格(`&emsp;`)
- 小于号<(`&lt;`)
- 大于号>(`&gt;`)
- 连接号&(`&amp;`)
- 双引号"(`&quot;`)
- 单引号'(`&apos;`)
- 版权©(`&copy;`)
- 间隔符·(`&middot`)
- 人民币￥(`&yen;`)

## scss/css

### 基础
* scss/css文件开始添加编码：`@charset "utf-8";`
* 简写模式，如：`border:1px solid #ccc;`
* 请不要直接定义标签样式，如`span{},div{}`
* 选择器如无特殊情况最多不要超过4层，请使用高效率选择器,可参阅：[CSS选择器的优化](http://www.w3cplus.com/css/css-selector-performance)
* 多数值为0时可以省略单位（好像`0deg`要带单位，某个浏览器有bug，然后`@keyframes`的`0%`单位不可省略）
* `z-index`一般以5为一个步长（如50,55,60），方便以后增加或修改
* 如果是自己写前缀，请把所有前缀写在标准的前面(如`-webkit-transition:0.3s;transition:0.3s;`)，关于前缀情况，可参考[can i use](http://caniuse.com/)
* 使用`!important`请小心，确认是否有必要
* 使用`clearfix`或`overflow`或`inline-block`清除子元素的浮动，而不是空标签
* 不使用影响到页面性能expression表达式与filter，`opacity`的filter兼容除外
* 禁止使用`.parent *{}`选择器，即`*{}`选择器只能单独使用，绝对禁止在前面再加上父级元素
* ie8只支持`:first-child`选择器，而不支持`:last-child`选择器，所以列表类的元素，可以使用`:first-child`对第一个元素进行特殊化处理，如需要对最后一个元素特殊化处理，则先考虑能否转成第一个元素，如果不能则对最后一个元素添加class`last`
* ie8只支持`:before/after`写法，不支持`::before/after`写法

### scss文件注意事项

* 基础文件名以`_`为前缀，导入时可以省略`_`和后缀名`.scss`，默认不编译成css文件
* 合理定义变量及使用`@mixin`
* 选择器合理嵌套，最多嵌套不超过四层
* 不要`@extend .class`，因为会产生冗余代码，如非得使用`@extend`，最好先定义一个`%`
* 可以使用自动化工具生成各个浏览器前缀

### class命名

* 小写英文，单词之间使用中划线（-）链接，如`line-item`
* 列表类的class可采用`.*-list>.*-item>.item-*`,如`ul.line-list>li.line-item>span.item-title`
* 特殊化某个类，采用两个中划线连接（--），如`.line-list.line-list--arrow`，基础类是`.line-list`右侧没有箭头，如需要右侧有箭头的可以追加类`.line-list--arrow`
* 图标的class以`.icon-`为前缀，字体图标的class为`.icon-font.i-name`，另字体图标可参考字体图标规范

### 常用class关键词：

* 布局类：header,footer,container,main,content,aside,page,section
* 包裹类：wrap,inner
* 区块类：region,block,box
* 结构类：hd,bd,ft,top,bottom,left,right,middle,col,row,grid,span
* 列表类：list,item,field
* 主次类：primary,secondary,sub,minor
* 大小类：s,m,l,xl
* 状态类：active,current,checked,hover,fail,success,warn,error,on,off
* 导航类：nav,prev,next,breadcrumb,forward,back,indicator,paging,first,last
* 交互类：tips,alert,modal,pop,panel,tab,accordion,slide,scroll,overlay
* 星级类：rate,star
* 分割类：group,seperate,divider
* 等分类：full,half,third,quarter
* table类: table,tr,td,cell,row
* 图片类：img,thumbnail,original,album,gallery
* 语言类：cn,en
* 其他语义类：btn,close,ok,cancel,switch; link,title,info,intro,more,icon; form,label,search,contact,phone,date,email,user; view,loading...

### 选择器权重

* !important
* 行内样式，指的是html文档中定义的style
* ID选择器
* 类，属性选择器和伪类选择器
* 元素和伪元素

### 雪碧图

注意事项：

* 单个图标之间必须保留空隙，空隙大小由容器大小及显示方式决定。这样做的好处是既考虑了“容错性”又提高了图片的可维护性。
* 图标的排列方式排列方式分为以下几种：横向排列（容器宽度有限）、纵向排列（容器高度有限）、斜线排列（容器宽高不限），靠左排列（容器背景居左）、靠右排列（容器背景居右）、水平居中排列（容器背景水平居中）、垂直居中排列（容器背景垂直居中）。
* 合并后图片大小不宜超过50K，建议大小在20K-50K之间。
* 请保留雪碧图片的psd源文件，以方便后来的增删改，后来的所有的修改请在psd源文件中修改，然后再导出图片。

合并图片的一些原则（专题页面除外）：

* 按照图片排列方式，把排列方式一样的图片进行合并，便于样式控制。
* 按照模块或元件，把同属于一个模块或元件的图片进行合并，方便模块或元件的维护。以导航模块为例，整个导航栏的icon为一个雪碧图片，而不是和其他的混合在一起，方便后来的修改或扩展。
* 按照图片大小，把大小一致或差不多的图片进行合并，可充分利用图片空间。
* 按照图片色彩，把色彩一致或差不多的图片进行合并，保证合并后图片的色彩不过于丰富，可防止色彩失真。

最后请不要过度使用sprite背景图片，而是按照或页面，或模块，或元件的方式合并为雪碧图，更好的考虑到未来的修改或扩展。

### css注释

css块级注释及单行注释

	/* -------------------------------------------------
	 * 块级注释
	 * -------------------------------------------------
	*/ 

	 /* 单行注释 */

scss块级注释及单行注释

	// 块级注释
	//----------------------------------------------------
	
	// 单行注释

[scss文件中的html结构注释法](http://imweb.io/topic/558cba8eedd682a62453a6bd)

	- 以emmet书写方法为骨架
	- ()表示特殊化追加的class，[]表示需要的属性，｛｝表示标签内的文本内容
	- 单行判断采用单行注释法，以if开头
	- 多行判断采用if,else,end if

### 给各大浏览器打hack

请以标准浏览器为准书写css代码，如遇兼容问题，先考虑换实现方法，在万不得已的情况下，采用hack解决

**firefox**
	
	/* Firefox 3+ */
	@-moz-document url-prefix() {}

**chrome及safari**
	
	/* Chrome, Safari 3+ */
	@media screen and (-webkit-min-device-pixel-ratio:0) {}

**ie8-**

	.selector { property: value\9; }

filter不可使用该方法

**ie9+及其他高级浏览器 **

	:root .selector {}

**ie10+及其他高级浏览器**

	html[lang='\
	en'] .selector 
	{}

更多请查阅：[hack速查英文版](http://browserhacks.com/) / [hack速查中文版](http://www.w3cplus.com/css/browser-hacks.html)


## 更多资料

* [css guideline](http://cssguidelin.es/)


