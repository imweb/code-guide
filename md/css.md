CSS规范
=====

##黄金法则
####`GOAL` 不管多少人同时参与编码，所有代码都应该看上去像是一个人编写的一样。

##语法

####`强制` 使用四个空格的 soft tabs
> 这是保证代码在各种环境下显示一致的唯一方式。
> 暂时可使用tab代替4空格，未来我们会通过工具自动转换

####`强制` 使用组合选择器时，保持每个独立的选择器占用一行

####`强制` 声明块的右括号应该另起一行

####`强制` 每条声明 : 后应该插入一个空格

####`强制` 每条声明应该只占用一行来保证错误报告更加准确

####`强制` 所有声明应该以分号结尾。
> 虽然最后一条声明后的分号是可选的，但是如果没有他，你的代码会更容易出错。

####`强制` 逗号分隔的取值，都应该在逗号之后增加一个空格

####`强制` 尽量使用十六进制颜色代码 #ffffff 来写颜色，除非是rgba

####`建议` 尽量不使用需要特定雪碧图合成方案的css背景方案
> 便于自动化雪碧图合并

####`建议` 尽量使用Pixels，而非Ems
> Ems应当更多用在line-height中

####`建议` 使用[KSS](https://github.com/kneath/kss)对公共模块写文档

####`建议` 使用[.editorconfig](http://editorconfig.org/)保证缩进、换行等统一

####`兼容` 尽量不使用rgba、background-size等不兼容IE6的css属性

####`兼容` 尽量不使用input[type="text"]、a > b、.c.d等不兼容IE6的css选择器

```css
/* Bad CSS */
.selector, .selector-secondary, .selector[type=text] {
  padding:15px;
  margin:0px 0px 15px;
  background-color:rgba(0,0,0,0.5);
  box-shadow:0 1px 2px #CCC,inset 0 1px 0 #FFFFFF
}

/* Good CSS */
.selector,
.selector-secondary,
.selector[type="text"] {
  padding: 15px;
  margin: 0 0 15px;
  background-color: rgba(0, 0, 0, .5);
  box-shadow: 0 1px 2px #ccc, inset 0 1px 0 #fff;
}
```

##类命名

####`强制` 全小写 中划线`-`连接
- 不要使用下划线和 camelCase命名
- 短划线应该作为相关类的自然间断。如:`.btn` 和 `.btn-danger`

####`强制` js-前缀样式应当只用于js，is-前缀代表即在js又在css使用的css
> css层叠样式中不应当包含js-前缀的class

####`强制` 用ie6-前缀表明，对ie6专用的兼容样式

####`建议` Class 的命名应该尽量短，也要尽量明确
> 避免过度使用简写。如: .btn 可以很好地描述 button，但是 .s 不能代表任何元素

##IDs VS Class

####`强制`对于在单独页面只出现一次的东西，使用IDs，否则使用类，不确定也使用类

##选择器

####`强制` 确保一个选择器只出现一个ID
> 规则#header .search #quicksearch { ... } 被视为有害的。

####`强制` 强制 disabled, mousedown, danger, hover, selected, 和active必须跟在一个命名空间下使用
> 例如：button.selected

##SASS

####`强制` 所有scss文件开头都应当是@charset "utf-8";
> 这样可以解决编码问题

####`强制` @extend置于块状声明头部

####`建议` @include置于块状声明头部，@extend之后

####`建议` 避免大于3层的嵌套
> 这样能有效避免过于具体的选择器
