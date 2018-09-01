### Array 中所有属性方法速查表
------
### Array.length
##### length 是Array的实例属性。返回或设置一个数组中的元素个数。该值是一个无符号 32-bit 整数，并且总是大于数组最高项的下标。
    基本用法
```javascript
var namelistA = new Array(4294967296); // 2的32次方 = 4294967296 
var namelistC = new Array(-100) // 负号

console.log(namelistA.length); // RangeError: 无效数组长度 
console.log(namelistC.length); // RangeError: 无效数组长度 

var namelistB = []; 
namelistB.length = Math.pow(2,32)-1; //set array length less than 2 to the 32nd power 
console.log(namelistB.length); 
// 4294967295
```
------
### Array.from()
##### Array.from() 方法从一个类似数组或可迭代对象中创建一个新的数组实例。
##### 语法： Array.from(arrayLike[, mapFn[, thisArg]])
* **arrayLike** 想要转换成数组的伪数组对象或可迭代对象。
* **mapFn** (可选参数) 如果指定了该参数，新数组中的每个元素会执行该回调函数。
* **thisArg** (可选参数) 可选参数，执行回调函数 mapFn 时 this 对象。

```javascript
// Array from a String
Array.from('foo'); 
// ["f", "o", "o"]
```
[传送门](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/from)

------
### Array.isArray   
##### Array.isArray() 用于确定传递的值是否是一个 Array。
#### 语法
##### Array.isArray(obj)
```js
// 下面的函数调用都返回 true
Array.isArray([]);
Array.isArray([1]);
Array.isArray(new Array());
// 鲜为人知的事实：其实 Array.prototype 也是一个数组。
Array.isArray(Array.prototype); 

// 下面的函数调用都返回 false
Array.isArray();
Array.isArray({});
Array.isArray(null);
Array.isArray(undefined);
Array.isArray(17);
Array.isArray('Array');
Array.isArray(true);
Array.isArray(false);
Array.isArray({ __proto__: Array.prototype });
```
<a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/isArray" target="_blank">传送门</a>

-------
### ~~~Array.observe()~~~ 已经废弃
-------
### Array.of()
##### Array.of() 方法创建一个具有可变数量参数的新数组实例，而不考虑参数的数量或类型。
```js
Array.of(7);       // [7] 
Array.of(1, 2, 3); // [1, 2, 3]

Array(7);          // [ , , , , , , ]
Array(1, 2, 3);    // [1, 2, 3]
```
##### 如果原生不支持的话，在其他代码之前执行以下代码会创建 Array.of() 。
```js
if (!Array.of) {
  Array.of = function() {
    return Array.prototype.slice.call(arguments);
  };
}
```
<a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/of" target="_blank">传送门</a>

-------
### Array.prototype.concat()
#####  concat() 方法用于合并两个或多个数组。此方法不会更改现有数组，而是返回一个新数组。
```js
//以下代码将两个数组合并为一个新数组：
var alpha = ['a', 'b', 'c'];
var numeric = [1, 2, 3];
alpha.concat(numeric);
// result in ['a', 'b', 'c', 1, 2, 3]


//以下代码将三个数组合并为一个新数组：
var num1 = [1, 2, 3],
    num2 = [4, 5, 6],
    num3 = [7, 8, 9];
var nums = num1.concat(num2, num3);
console.log(nums); 
// results in [1, 2, 3, 4, 5, 6, 7, 8, 9]


//以下代码将三个值连接到数组：
var alpha = ['a', 'b', 'c'];
var alphaNumeric = alpha.concat(1, [2, 3]);
console.log(alphaNumeric); 
// results in ['a', 'b', 'c', 1, 2, 3]


//以下代码合并数组并保留引用：
var num1 = [[1]];
var num2 = [2, [3]];
var nums = num1.concat(num2);
console.log(nums);
// results in [[1], 2, [3]]
// modify the first element of num1
num1[0].push(4);
console.log(nums);
// results in [[1, 4], 2, [3]]
```
<a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/concat" target="_blank">传送门</a>

-------
### Array.prototype.copyWithin()
##### copyWithin() 方法浅复制数组的一部分到同一数组中的另一个位置，并返回它，而不修改其大小。
```javascript
var array1 = [1, 2, 3, 4, 5];

// place at position 0 the element between position 3 and 4
console.log(array1.copyWithin(0, 3, 4));
// expected output: Array [4, 2, 3, 4, 5]

// place at position 1 the elements after position 3
console.log(array1.copyWithin(1, 3));
// expected output: Array [4, 4, 5, 4, 5]
```
#### 语法 
```
arr.copyWithin(target[, start[, end]])
```
* **target**
* 0 为基底的索引，复制序列到该位置。如果是负数，target 将从末尾开始计算。
* 如果 target 大于等于 arr.length，将会不发生拷贝。如果 target 在 start 之后，复制的序列将被修改以符合 arr.length。
* **start**
* 0 为基底的索引，开始复制元素的起始位置。如果是负数，start 将从末尾开始计算。
* 如果 start 被忽略，copyWithin 将会从0开始复制。
* **end**
* 0 为基底的索引，开始复制元素的结束位置。copyWithin 将会拷贝到该位置，但不包括 end 这个位置的元素。如果是负数， end 将从末尾开始计算。
* 如果 end 被忽略，copyWithin 将会复制到 arr.length。
```javascript
[1, 2, 3, 4, 5].copyWithin(-2);
// [1, 2, 3, 1, 2]

[1, 2, 3, 4, 5].copyWithin(0, 3);
// [4, 5, 3, 4, 5]

[1, 2, 3, 4, 5].copyWithin(0, 3, 4);
// [4, 2, 3, 4, 5]

[1, 2, 3, 4, 5].copyWithin(-2, -3, -1);
// [1, 2, 3, 3, 4]

[].copyWithin.call({length: 5, 3: 1}, 0, 3);
// {0: 1, 3: 1, length: 5}

// ES2015 Typed Arrays are subclasses of Array
var i32a = new Int32Array([1, 2, 3, 4, 5]);

i32a.copyWithin(0, 2);
// Int32Array [3, 4, 5, 4, 5]

// On platforms that are not yet ES2015 compliant: 
[].copyWithin.call(new Int32Array([1, 2, 3, 4, 5]), 0, 3, 4);
// Int32Array [4, 2, 3, 4, 5]
```
#### Polyfill
```javascript
if (!Array.prototype.copyWithin) {
  Array.prototype.copyWithin = function(target, start/*, end*/) {
    // Steps 1-2.
    if (this == null) {
      throw new TypeError('this is null or not defined');
    }

    var O = Object(this);

    // Steps 3-5.
    var len = O.length >>> 0;

    // Steps 6-8.
    var relativeTarget = target >> 0;

    var to = relativeTarget < 0 ?
      Math.max(len + relativeTarget, 0) :
      Math.min(relativeTarget, len);

    // Steps 9-11.
    var relativeStart = start >> 0;

    var from = relativeStart < 0 ?
      Math.max(len + relativeStart, 0) :
      Math.min(relativeStart, len);

    // Steps 12-14.
    var end = arguments[2];
    var relativeEnd = end === undefined ? len : end >> 0;

    var final = relativeEnd < 0 ?
      Math.max(len + relativeEnd, 0) :
      Math.min(relativeEnd, len);

    // Step 15.
    var count = Math.min(final - from, len - to);

    // Steps 16-17.
    var direction = 1;

    if (from < to && to < (from + count)) {
      direction = -1;
      from += count - 1;
      to += count - 1;
    }

    // Step 18.
    while (count > 0) {
      if (from in O) {
        O[to] = O[from];
      } else {
        delete O[to];
      }

      from += direction;
      to += direction;
      count--;
    }

    // Step 19.
    return O;
  };
}
```
<a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/copyWithin" target="_blank">传送门</a>


-------
Array.prototype.entries()
-------
Array.prototype.every()
-------
Array.prototype.fill()
-------
Array.prototype.filter()
-------
Array.prototype.find()
-------
Array.prototype.findIndex()
-------
Array.prototype.flat()
-------
Array.prototype.flatMap()
-------
Array.prototype.forEach()
-------
Array.prototype.includes()
-------
Array.prototype.indexOf()
-------
Array.prototype.join()
-------
Array.prototype.keys()
-------
Array.prototype.lastIndexOf()
-------
Array.prototype.map()
-------
Array.prototype.pop()
-------
Array.prototype.push()
-------
Array.prototype.reduce()
-------
Array.prototype.reduceRight()
-------
Array.prototype.reverse()
-------
Array.prototype.shift()
-------
Array.prototype.slice()
-------
Array.prototype.some()
-------
Array.prototype.sort()
-------
Array.prototype.splice()
-------
Array.prototype.toLocaleString()
-------
Array.prototype.toSource()
-------
Array.prototype.toString()
-------
Array.prototype.unshift()
-------
Array.prototype.values()
-------
Array.unobserve()
