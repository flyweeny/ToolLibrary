### promise链式调用

* 因为 当promise对象 then()之后, 会返回一个新的promise对象,所以可以一直then()下去


### jquery链式调用
```js
Ferrinte.prototype.show=function () {
    for(var i=0;i<this.elements.length;i++)
    {
        this.elements[i].style.display='block';
    }

    return this;
};

Ferrinte.prototype.hide=function () {
    for(var i=0;i<this.elements.length;i++)
    {
        this.elements[i].style.display='none';
    }
    return this;
};

```

* 链式处理，只需要在方法内部方法当前的这个实例对象this就可以了，因为返回当前实例的this，从而又可以访问自己的原型了，这样的就节省代码量，提高代码的效率，代码看起来更优雅。
* 但是这种方法有一个问题是：所有对象的方法返回的都是对象本身，也就是说没有返回值，所以这种方法不一定在任何环境下都适合。
