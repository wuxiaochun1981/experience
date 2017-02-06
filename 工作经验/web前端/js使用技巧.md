### JavaScript split() 方法

由于split(separator)拆分字符串有多个不同分隔符有的时候，不能直接所把有分隔符组成一个字符串传给split方法，没有得到我们预想效果。所以需要使用 /分隔符1|分隔符2|分隔符3/  **注意：** *其中由于分隔符有|所以需要转义\\|*。

**错误列子**
```
var test = "aaa,bbb;ddd|hh";
console.log(test.split(',;|').length);
```

**正确列子**
```
var test = "aaa,bbb;ddd|hh";
console.log(test.split(/,|;|\|/).length);
```
