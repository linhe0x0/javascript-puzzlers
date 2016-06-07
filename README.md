# javascript-puzzlers

> Do you really know JavaScript ?

这是一些网上广为传播的关于 Javascript 方面的小题，好多题还是相当有深度的，在这里汇总一下，便于学习和研究。

这些题主要针对 [ECMA 262 (5.1)](http://www.ecma-international.org/ecma-262/5.1/#sec-15.4.4.19) 的浏览器环境，如果你使用的是 Node 或是其他环境，可能表现会有点不一样。例如 `this` 和 `global` 在火狐浏览器控制台和 Node 环境中是不一样的。

本人基于自己的理解和网上的资料，整理了一份[非标准参考答案](https://github.com/sqrthree/javascript-puzzlers/tree/master/annotations)。

#### 1、下面这个表达式的结果是什么？

```
["1", "2", "3"].map(parseInt)
```

* ["1", "2", "3"]
* [1, 2, 3]
* [0, 1, 2]
* other

#### 2、下面这个表达式的结果是什么？

```
[typeof null, null instanceof Object]
```

* ["object", false]
* [null, false]
* ["object", true]
* other

#### 3、下面这个表达式的结果是什么？

```
[ [3,2,1].reduce(Math.pow), [].reduce(Math.pow) ]
```

* an error
* [9, 0]
* [9, NaN]
* [9, undefined]

#### 4、下面这个表达式的结果是什么？

```
var val = 'smtg';
console.log('Value is ' + (val === 'smtg') ? 'Something' : 'Nothing');
```

* Value is Something
* Value is Nothing
* NaN
* other

#### 5、下面这个表达式的结果是什么？

```
var name = 'World!';
(function () {
    if (typeof name === 'undefined') {
        var name = 'Jack';
        console.log('Goodbye ' + name);
    } else {
        console.log('Hello ' + name);
    }
})();
```

* Goodbye Jack
* Hello Jack
* Hello undefined
* Hello World

#### 6、下面这个表达式的结果是什么？

```
var END = Math.pow(2, 53);
var START = END - 100;
var count = 0;
for (var i = START; i <= END; i++) {
    count++;
}
console.log(count);
```

* 0
* 100
* 101
* other

#### 7、下面这个表达式的结果是什么？

```
var ary = [0,1,2];
ary[10] = 10;
ary.filter(function(x) {
  return x === undefined;
});
```

* [undefined × 7]
* [0, 1, 2, 10]
* []
* [undefined]

#### 8、下面这个表达式的结果是什么？

```
var two   = 0.2
var one   = 0.1
var eight = 0.8
var six   = 0.6
[two - one == one, eight - six == two]
```

* [true, true]
* [false, false]
* [true, false]
* other

#### 9、下面这个表达式的结果是什么？

```
function showCase(value) {
    switch(value) {
    case 'A':
        console.log('Case A');
        break;
    case 'B':
        console.log('Case B');
        break;
    case undefined:
        console.log('undefined');
        break;
    default:
        console.log('Do not know!');
    }
}
showCase(new String('A'));
```

* Case A
* Case B
* Do not know!
* undefined

#### 10、下面这个表达式的结果是什么？

```
function showCase2(value) {
    switch(value) {
    case 'A':
        console.log('Case A');
        break;
    case 'B':
        console.log('Case B');
        break;
    case undefined:
        console.log('undefined');
        break;
    default:
        console.log('Do not know!');
    }
}
showCase2(String('A'));
```

* Case A
* Case B
* Do not know!
* undefined

#### 11、下面这个表达式的结果是什么？

```
function isOdd(num) {
    return num % 2 == 1;
}
function isEven(num) {
    return num % 2 == 0;
}
function isSane(num) {
    return isEven(num) || isOdd(num);
}
var values = [7, 4, '13', -9, Infinity];
values.map(isSane);
```

* [true, true, true, true, true]
* [true, true, true, true, false]
* [true, true, true, false, false]
* [true, true, false, false, false]

#### 12、下面这个表达式的结果是什么？

```
parseInt(3, 8)
parseInt(3, 2)
parseInt(3, 0)
```

* 3, 3, 3
* 3, 3, NaN
* 3, NaN, NaN
* other

#### 13、下面这个表达式的结果是什么？

```
Array.isArray( Array.prototype )
```

* true
* false
* error
* other

#### 14、下面这个表达式的结果是什么？

```
var a = [0];
if ([0]) {
  console.log(a == true);
} else {
  console.log("wut");
}
```

* true
* false
* "wut"
* other

#### 15、下面这个表达式的结果是什么？

```
[]==[]
```

* true
* false
* error
* other

#### 16、下面这个表达式的结果是什么？

```
'5' + 3
'5' - 3
```

* "53", 2
* 8, 2
* error
* other

#### 17、下面这个表达式的结果是什么？

```
1 + - + + + - + 1
```

* 2
* 1
* error
* other

#### 18、下面这个表达式的结果是什么？

```
var ary = Array(3);
ary[0]=2
ary.map(function(elem) {
  return '1';
});
```

* [2, 1, 1]
* ["1", "1", "1"]
* [2, "1", "1"]
* other

#### 19、下面这个表达式的结果是什么？

```
function sidEffecting(ary) {
  ary[0] = ary[2];
}
function bar(a,b,c) {
  c = 10
  sidEffecting(arguments);
  return a + b + c;
}
bar(1,1,1)
```

* 3
* 12
* error
* other

#### 20、下面这个表达式的结果是什么？

```
var a = 111111111111111110000,
    b = 1111;
a + b;
```

* 111111111111111111111
* 111111111111111110000
* NaN
* Infinity

#### 21、下面这个表达式的结果是什么？

```
var x = [].reverse;
x();
```

* []
* undefined
* error
* window

#### 22、下面这个表达式的结果是什么？

```
Number.MIN_VALUE > 0
```

* false
* true
* error
* other

#### 23、下面这个表达式的结果是什么？

```
[1 < 2 < 3, 3 < 2 < 1]
```

* [true, true]
* [true, false]
* error
* other

#### 24、下面这个表达式的结果是什么？

```
// the most classic wtf
2 == [[[2]]]
```

* true
* false
* undefined
* other

#### 25、下面这个表达式的结果是什么？

```
3.toString()
3..toString()
3...toString()
```

* "3", error, error
* "3", "3.0", error
* error, "3", error
* other

#### 26、下面这个表达式的结果是什么？

```
(function(){
  var x = y = 1;
})();
console.log(y);
console.log(x);
```
* 1, 1
* error, error
* 1, error
* other

#### 27、下面这个表达式的结果是什么？

```
var a = /123/,
    b = /123/;
a == b
a === b
```

* true, true
* true, false
* false, false
* other


#### 28、下面这个表达式的结果是什么？

```
var a = [1, 2, 3],
    b = [1, 2, 3],
    c = [1, 2, 4]
a ==  b
a === b
a >   c
a <   c
```

* false, false, false, true
* false, false, false, false
* true, true, false, true
* other

#### 29、下面这个表达式的结果是什么？

```
var a = {}, b = Object.prototype;
[a.prototype === b, Object.getPrototypeOf(a) === b]
```

* [false, true]
* [true, true]
* [false, false]
* other

#### 30、下面这个表达式的结果是什么？

```
function f() {}
var a = f.prototype, b = Object.getPrototypeOf(f);
a === b
```

* true
* false
* null
* other

#### 31、下面这个表达式的结果是什么？

```       
function foo() { }
var oldName = foo.name;
foo.name = "bar";
[oldName, foo.name]
```

* error
* ["", ""]
* ["foo", "foo"]
* ["foo", "bar"]

#### 32、下面这个表达式的结果是什么？

```
"1 2 3".replace(/\d/g, parseInt)
```

* "1 2 3"
* "0 1 2"
* "NaN 2 3"
* "1 NaN 3"

#### 33、下面这个表达式的结果是什么？

```
function f() {}
var parent = Object.getPrototypeOf(f);
f.name // ?
parent.name // ?
typeof eval(f.name) // ?
typeof eval(parent.name) //  ?
```

* "f", "Empty", "function", "function"
* "f", undefined, "function", error
* "f", "Empty", "function", error
* other

#### 34、下面这个表达式的结果是什么？

```
var lowerCaseOnly =  /^[a-z]+$/;
[lowerCaseOnly.test(null), lowerCaseOnly.test()]
```

* [true, false]
* error
* [true, true]
* [false, true]

#### 35、下面这个表达式的结果是什么？

```
[,,,].join(", ")
```

* ", , , "
* "undefined, undefined, undefined, undefined"
* ", , "
* ""

#### 36、下面这个表达式的结果是什么？

```
var a = {class: "Animal", name: 'Fido'};
a.class
```

* "Animal"
* Object
* an error
* other

#### 37、下面这个表达式的结果是什么？

```
var a = new Date("epoch")
```

* Thu Jan 01 1970 01:00:00 GMT+0100 (CET)
* current time
* error
* other

#### 38、下面这个表达式的结果是什么？

```
var a = Function.length,
    b = new Function().length
a === b
```

* true
* false
* error
* other

#### 39、下面这个表达式的结果是什么？

```
var a = Date(0);
var b = new Date(0);
var c = new Date();
[a === b, b === c, a === c]
```

* [true, true, true]
* [false, false, false]
* [false, true, false]
* [true, false, false]

#### 40、下面这个表达式的结果是什么？

```
var min = Math.min(), max = Math.max()
min < max
```

* true
* false
* error
* other

#### 41、下面这个表达式的结果是什么？

```
function captureOne(re, str) {
  var match = re.exec(str);
  return match && match[1];
}
var numRe  = /num=(\d+)/ig,
    wordRe = /word=(\w+)/i,
    a1 = captureOne(numRe,  "num=1"),
    a2 = captureOne(wordRe, "word=1"),
    a3 = captureOne(numRe,  "NUM=2"),
    a4 = captureOne(wordRe,  "WORD=2");
[a1 === a2, a3 === a4]
```

* [true, true]
* [false, false]
* [true, false]
* [false, true]

#### 42、下面这个表达式的结果是什么？

```
var a = new Date("2014-03-19"),
    b = new Date(2014, 03, 19);
[a.getDay() === b.getDay(), a.getMonth() === b.getMonth()]
```

* [true, true]
* [true, false]
* [false, true]
* [false, false]

#### 43、下面这个表达式的结果是什么？


```
if ('http://giftwrapped.com/picture.jpg'.match('.gif')) {
  'a gif file'
} else {
  'not a gif file'
}
```

* 'a gif file'
* 'not a gif file'
* error
* other

#### 44、下面这个表达式的结果是什么？

```
function foo(a) {
    var a;
    return a;
}
function bar(a) {
    var a = 'bye';
    return a;
}
[foo('hello'), bar('hello')]
```

* ["hello", "hello"]
* ["hello", "bye"]
* ["bye", "bye"]
* other

### 资料链接

* [http://javascript-puzzlers.herokuapp.com/](http://javascript-puzzlers.herokuapp.com/)
