### Array 中所有属性方法速查表
---
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
#### Array.from() 方法从一个类似数组或可迭代对象中创建一个新的数组实例。
#### 语法
##### Array.from(arrayLike[, mapFn[, thisArg]])
##### arrayLike 想要转换成数组的伪数组对象或可迭代对象。
##### mapFn (可选参数) 如果指定了该参数，新数组中的每个元素会执行该回调函数。
##### thisArg (可选参数) 可选参数，执行回调函数 mapFn 时 this 对象。
```javascript
// Array from a String
Array.from('foo'); 
// ["f", "o", "o"]
```
[传送门](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/from)

------
### isArray
    Array.isArray() 用于确定传递的值是否是一个 Array。
### 语法
### Array.isArray(obj)
[传送门](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/isArray)

-------
Array.observe()<br>
Array.of()<br>
Array.prototype.concat()<br>
Array.prototype.copyWithin()<br>
Array.prototype.entries()<br>
Array.prototype.every()<br>
Array.prototype.fill()<br>
Array.prototype.filter()<br>
Array.prototype.find()<br>
Array.prototype.findIndex()<br>
Array.prototype.flat()<br>
Array.prototype.flatMap()<br>
Array.prototype.forEach()<br>
Array.prototype.includes()<br>
Array.prototype.indexOf()<br>
Array.prototype.join()<br>
Array.prototype.keys()<br>
Array.prototype.lastIndexOf()<br>
Array.prototype.map()<br>
Array.prototype.pop()<br>
Array.prototype.push()<br>
Array.prototype.reduce()<br>
Array.prototype.reduceRight()<br>
Array.prototype.reverse()<br>
Array.prototype.shift()<br>
Array.prototype.slice()<br>
Array.prototype.some()<br>
Array.prototype.sort()<br>
Array.prototype.splice()<br>
Array.prototype.toLocaleString()<br>
Array.prototype.toSource()<br>
Array.prototype.toString()<br>
Array.prototype.unshift()<br>
Array.prototype.values()<br>
Array.prototype[@@iterator]()<br>
Array.unobserve()<br>
get Array[@@species]<br>
