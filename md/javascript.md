Javascript编码规范
=====

## 1.分号

#### `强制`语句必须都有分号结尾，除了for, function, if, switch, try, while

## 2. 缩进

#### `强制` 使用空格而非Tab来缩进, 一层缩进=4个空格

## 3. 命名

#### `强制` 常量使用大写字符, 下划线连接
```javascript
var SECONDS_IN_A_MINUTE = 60;
obj.TEXT_WARNNING = '警告';
```

#### `强制` 标准变量: 驼峰
```javascript
var myCount = 1;
```

#### `强制` 构造函数: 驼峰且大写第一个字母
```javascript
function Point(x, y) {
    this.x = x;
    this.y = y;
}
```

#### `建议` 私有方法: 驼峰且加`_`前缀
```javascript
function MyClass() {
    var _privateNum;
    this.getNum = function() {
        return _privateNum;
    };
}

// 虽然不建议这么写一个对象(建议用闭包来写)
// 但如果真这么写了, 请把意图上不想暴露的变量, 用_开头
var myCounter = {
    _count: 1,
    get: function() {
        return this._count;
    }
};
```

#### `建议` 对布尔型的变量, 命名时加`is`,`has`,`can`前缀

#### `强制` 不要使用让人糊涂的命名
```javascript
var isNotError;
var isNotClosed;
```

#### `强制` 当出现以下字符时,统一拼写

```javascript
var iOSVersion; //iOS
var AndroidVersion; //Android
var classID,teacherID,mID; //ID
var jumpURL; //URL
var normalHTML, isXML; //HTML
var HTTPHeader; //HTTP
//... 待补充
```

#### `建议` 字符串常量或字面量使用时, 使用单引号而非双引号

```javascript
var str = '<span class="info">';
str += 'some infomation</span>';
```

## 4. 代码风格

#### `强制` 即使是单行,也需要加花括号
`正确`
```javascript
//更建议换行写
if (isUndead) {
    grabFire();
}
//一定要一行,也必须这样
if (isUndead) { grabFire(); }
```

`错误`
```javascript
if (isUndead) grabFire();
```

#### `强制`操作符前后要有空格分隔
```javascript
//运算符
var a = 1 + 2;
var thaco = hit + adjustment - randomFactor;

//三元操作符
var num = val ? foo() : bar();
var fn = JSON.parse ? JSON.parse : function() {
    //...
};
```

#### `强制`对象属性的冒号前无空格,后跟一个空格
```javascript
var myObject = {
    propA: 1
};
```

#### `建议`逗号位置: Last comma

`建议` (last comma)
```javascript
var foo = 1,
    bar = 2,
    baz = 3;

var obj = {
    foo: 1,
    bar: 2,
    baz: 3
};
```

`不推荐` (first comma)
```javascript
var foo = 1
  , bar = 2
  , baz = 3;

var obj = {
    foo: 1
  , bar: 2
  , baz: 3
};
```

#### `注意`一定不要多写逗号了
`错误`
```javascript
var list = [
    {n: 1},
    {n: 2}, //<----- 会导致IE报错, GCC默认参数压缩也会报错
];
```

#### `建议`function的参数括号: 前后都加一个空格, 若非匿名函数, 则名字和括号之间不再需要空格
```javascript
//匿名函数, function和括号间有空格, 括号和花括号间也有空格
var fn = function (param) {
    //...
}
//带名字的函数, function和括号间有空格, 但插入的名字和括号间就无需再加空格了
function foo() {
    return "bar";
}
```

#### `建议`条件判断括号: 前后都加一个空格
`推荐`
```javascript
if (true) {
    //...
}

while (true) {
    //...
}

switch (v) {
    //...
}
```

`不推荐`
```javascript
if(true) {
    //...
}

while(true) {
    //...
}

switch(v) {
    //...
}
```

#### `建议`括号紧挨两端处不要空格, 中间有逗号, 逗号后加空格

`推荐`
```javascript
function fn(arg1, arg2) {
    //...
}
var fn = function (arg) {
    //...
}
if (true) {
    //...
} else {
    //...
}
var arr = [1, 2, 3];
```

`不推荐`
```javascript
function fn( arg1, arg2 ) {
    //...
}
var fn = function ( arg ) {
    //...
}
if ( true ) {
    //...
}
else {
    //...
}
var arr = [ 1, 2, 3 ];
```

#### `建议` if...else 写法
```javascript
if (condition1) {
    doSomething1();
} else if (condition2) {
    doSomething2();
} else {
    doSomethingElse();
}
```

#### `建议` switch...case 写法

```javascript
switch (condition) {
    case "first":
        // code
        break;

    case "third":
        // code
        break;

    default:
        // code
        break;
}
```

```javascript
switch (condition) {
    case "first":
    case "second": //上一行不用加fall though: 两个case紧挨, jshint不会报错
        // code
        break;

    case "third":
        // code
        /* falls through */
    case "fourth": //上一行必须加, 否则jshint会报错
        // code
        break;

    default:
        // code
        break;
}
```


#### `强制`函数参数过多时的排版: 两层缩进

`正确`
```javascript
var localMonsterRumors = getLocalGossip(inkeeper,
        localInn, numberOfClerics, pintsOfAlePurchased,
        charismaAjustment);
```

`错误`
```javascript
var localMonsterRumors = getLocalGossip(inkeeper,
                                          localInn,
                                          numberOfClerics,
                                          pintsOfAlePurchased,
                                          charismaAjustment);
```

#### `建议`采用临时变量来提高复杂判断或字符串拼接的可读性

`错误`
```javascript
if ( (conditionAA && conditionAB) || (conditionBA && conditionBB) ){
    //...
}

var elem = document.getElementById('charClass-' + charClass +
      + '_combatStats-' + armorClass + '-' + toHitBonus);
```

`正确`
```javascript
var conditionA = conditionAA && conditionAB;
var conditionB = conditionBA && conditionBB;
if (conditionA || conditionB) {
    //...
}

var strChar = 'charClass-' + charClass;
var strCombat = 'combatStatus-' + armorClass + '-' + toHitBonus;
var elem = document.getElementById(strChar + '_' + strCombat);
```

#### `建议`逻辑块 之间使用空行

## 5. 杂项

#### `建议`尽量使用标准方法而不是用非标准方法

例:
优先用string.charAt(3) 而不用 string[3]

#### `强制`不要修改内置对象的原型
主要是为了不污染原型从而对外部造成不好的影响
如`Array.prototype`,`Object.prototype`

#### `强制`避免 == != 的使用， 用严格比较条件 === !==

### for...in

#### `建议`对数组遍历时, 用下标的for循环而非for...in

#### `注意`使用for...in时要注意利用hasOwnProperty排除掉可能的原型污染干扰

### with,eval

#### `强制`如非特殊情况, 不允许使用with,eval

### 多行字符串

#### `强制`不要使用转义字符'\'的方式来写多行字符串
#### `强制`也不要使用function内注释再toString的hack来定义和使用多行字符串

## 保留字
#### `强制`对象的属性如果是保留字, 请务必使用引号定义,方括号引号引用
`正确`
```javascript
var example = {
    "new": function () {}
};

var fn = example['new'];
```

`错误`
```javascript
var example = {
    new: function () {}
};

var fn = example.new;
```

## 注释

#### 单行注释优先

#### 优先使用单行注释(即使是需要写多行), 除了以下情况

#### 优先使用多行注释的情况

 - fileoverview / constructors
 - public method

#### 多行注释
```javascript
/**
 * this method is ...
 * @param {Object} ...
 * @return {Object} ...
 */
```

## //todo: 大块注释怎么写

## //todo: switch规避jshint的一种特殊情形
