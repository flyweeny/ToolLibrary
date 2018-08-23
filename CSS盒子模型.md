# CSS盒子模型
### 标准盒子模型
---
设置方式
```CSS
box-sizing: content-box;
```
* content-box  是默认值。如果你设置一个元素的宽为100px，那么这个元素的内容区会有100px宽，并且任何边框和内边距的宽度都会被增加到最后绘制出来的元素宽度中。
* 意思就是 width = width + padding-left + padding-right + border-left + border-right
* 把padding 和 border 都计算在内
---
### 怪异盒子模型（IE盒子模型）
---
设置方式
```CSS
box-sizing: border-box;
```
* border-box 告诉浏览器去理解你设置的边框和内边距的值是包含在width内的。也就是说，如果你将一个元素的width设为100px,那么这100px会包含其它的border和padding，内容区的实际宽度会是width减去border + padding的计算值。大多数情况下这使得我们更容易的去设定一个元素的宽高。
* 意思就是 width = width
* 不计算 padding 和 border
