# javascript-puzzlers

> Do you really know JavaScript ?

这是一些网上广为传播的关于 Javascript 方面的小题，好多题还是相当有深度的，在这里汇总一下，便于学习和研究。

这些题主要针对 [ECMA 262 (5.1)](http://www.ecma-international.org/ecma-262/5.1/#sec-15.4.4.19) 的浏览器环境，如果你使用的是 Node 或是其他环境，可能表现会有点不一样。例如 `this` 和 `global` 在火狐浏览器控制台和 Node 环境中是不一样的。

本人基于自己的理解和网上的资料，整理了一份[非标准参考答案](https://github.com/sqrthree/javascript-puzzlers/tree/master/annotations)。

#### 1、下面这个表达式的结果是什么？

```
["1", "2", "3"].map(parseInt)
```

* `["1", "2", "3"]`
* [1, 2, 3]
* [0, 1, 2]
* other
