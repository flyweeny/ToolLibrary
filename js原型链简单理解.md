```js
function Fn() {}// Fn为构造函数
var f1 = new Fn();//f1是Fn构造函数创建出来的对象
// 构造函数的prototype属性值就是对象原型。（Fn.prototype就是对象的原型）

// 构造函数的prototype属性值的类型就是对象
typeof Fn.prototype===object

// 对象原型中的constructor属性指向构造函数
Fn.prototype.constructor===Fn

// 对象的__proto__属性值就是对象的原型。（f1.__proto__就是对象原型）

Fn.prototype === f1.__proto__  // 其实它们两个就是同一个对象---对象的原型。

所有Fn.prototype.__proto__ === Object.prototype

typeof Object.prototype === object。

Object.prototype.__proto__ === null。

```
   
