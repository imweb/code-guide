## 总体原则

1. **As short as possible（如无必要，勿增注释）**。尽量提高代码本身的清晰性、可读性。
1. **As long as necessary（如有必要，尽量详尽）**。合理的注释、空行排版等，可以让代码更易阅读、更具美感。

总之，注释的目的是：**提高代码的可读性，从而提高代码的可维护性。**


## 哪些需要注释

1. 某段代码的写法，需要注释说明原因时：
```js
// Using loop is more efficient than `rest = slice.call(arguments, 1)`.
for (i = 1, len = arguments.length; i < len; i++) {
    rest[i - 1] = arguments[i];
}
```

2. 添加上注释，能让代码结构更清晰时：
```js
init: function(selector, context, rootjQuery) {
    var match, elem, ret, doc;

    // Handle $(""), $(null), or $(undefined)
    if ( !selector ) {
        ...
    }

    // Handle $(DOMElement)
    if ( selector.nodeType ) {
        ...
    }

    // The body element only exists once, optimize finding it
    if ( typeof selector === "string" ) {
        ...
     }
}
```

3. 有借鉴第三方代码，需要说明时：
```js
// Inspired by https://github.com/jquery/jquery/blob/master/src/core.js
function ready() {
    ...
}
```

4. 当有值的判断或者选择，有不同的分支时：
```js
// It need to do when the value of a  is one or two. 
if(a === 1 || a === 2) {
    ...
}
```


## 起始约定

每个源码文件的开头，保留为空：

```js

define('lego',[],function() {
    // 源代码
});

```



注意点：

1. 文件头不注明Author信息，通过README来提供author & contributors。（组件规则，业务代码需要注明方便查看）


##  注释书写规范

1. 源码中的注释，推荐用英文。
2. 含有中文时，标点符号用中文全角。
3. 中英文夹杂时，英文与中文之间要用一个空格分开。
4. 注释标识符与注释内容要用一个空格分开：`// 注释` 与 `/* 注释 */`。
5. 单行注释用`// 注释` 与多行注视用 `/* 注释 */`区分开来，能够一行注视明白的不写过多注视


## JSDoc 注释

- 不推荐 JSDoc 式注释，推荐 Backbone 风格的注释。
- API 请通过 README 等文档表达清楚。
- 不写 JSDoc 类文档，可以让开发者在写代码时更专注于写代码，在写文档时则更专注于写文档。**让工作解耦，更专注。**
