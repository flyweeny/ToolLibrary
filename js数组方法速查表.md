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
    Array.isArray() 用于确定传递的值是否是一个 Array。
### 语法
### Array.isArray(obj)
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
Array.prototype.concat()
-------
Array.prototype.copyWithin()
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
