HTML规范
====

### `强制?`缩进使用 4个空格

### `强制`属性使用双引号

### `建议`不在自动闭合标签后加`/`

### `强制`doctype使用大写
```
<!DOCTYPE html>
<html>
    <head>
    </head>
</html>
```

### `强制`除非有特殊需求,一律使用UTF8编码,书写方式约定为:
```
<head>
    <meta charset="UTF-8">
</head>
```

### `强制`引入css/js时,一律不加`type`
```
<link rel="stylesheet" href="main.css">
<style>
/*...*/
</style>
<script>
//...
</script>
```

### `建议`img加alt

### `建议`link加title

### `建议?`统一顺序, 增加gzip的压缩比
```
<a href="javascript:void(0);" target="_blank" class="item" id="xxx" title="xxx">xxx</a>
<a href="javascript:void(0);" target="_blank" class="item" id="yyy" title="yyy">yyy</a>
```
