

## 原生DOM Class属性( IE11 支持,IE10部分支持)

> 前情提要

```html
<div class='box box1 box2' id='appbox'></div>
```

```javascript
const dom = document.querySelector('#appbox')
```

> 使用console.dir(DOM元素)可以查看该元素的具体信息

### className (可读，可写)

```javascript
// 获取该元素的类名
const name = dom.className // box box1 box2
// 设置该元素的class为xxx
dom.className = 'xxxx' // <div class='xxxx' id='appbox'></div>
```

### classList 

> 一个对象，含有多个属性

#### length （只读属性）

```javascript
// 查看该dom元素有多少个类名
const classLength = dom.classList.length // 3
// 从左到右获取 class
const firstClass = dom.classList[0] // box
const secondClass = dom.classList[1] // box1
const thirdClass = dom.classList[2] // box2
```

#### value (可读，可写)

```javascript
// 获取该元素的类名 等同于 dom.className
const name = dom.classList.value // box box1 box2
// 设置元素的class
dom.classList.value = 'xxxx' // <div class='xxxx' id='appbox'></div>
```

#### .item(index)

```javascript
/*
* 传入索引值，返回该元素class列表索引对应的项,如果没有返回null
*/
const firstClass = dom.classList.item(0) // box 等同于 dom.classList[0]
```

#### .values()

```javascript
// 返回迭代器 使用 forof 循环
const domClassValues = dom.classList.values(0)
for(const int of domClassValues){
    console.log(int) // box box1 box2
}
```

#### .**entries**()

```javascript
// 返回迭代器 使用 forof 循环
const domClassValues = dom.classList.entries()
for(const int of domClassValues){
    console.log(int) // [0,'box'] [1,'box1'] [2,'box2']
}
```

#### .**forEach**(callback)

```javascript
/* 传入一个函数作为参数
* @{params} value 每个class
* @{params} key class的索引
* @{params} parent (DOMTokenList)原classList
*/
dom.classList.forEach(function (value, key, parent) {
	console.log(value, key, parent);
    // box 0 DOMTokenList(3) ["box", "box1", "box2", value: "box box1 box2"]
})
```

#### .add()

```javascript
// 给该元素添加指定的 class
dom.classList.add('box3', 'box4') // <div class='box box1 box2 box3 box4'></div>
```

#### .remove()

```javascript
// 移除该元素指定的 class
dom.classList.add('box1', 'box2') // <div class='box'></div>
```

#### .toggle(class,flag)

```javascript
// 如果该元素有该class就移除并返回 false ,没有则添加并返回 true
dom.classList.toggle('box') // <div class='box1 box2'></div>
/* 如果有第二个参数, 
*  ->true  强制添加类,如果存在则不做操作
*  ->false 强制删除类
*/
dom.classList.toggle('box',i<10)

```

#### .replace(old,new)

```javascript
// 替换该元素指定的 class
dom.classList.replace('box','newbox') // <div class='newbox box1 box2'></div>
```

#### . **contains**()

```javascript
//检查该元素是否有指定的 class ,有返回true ,没有返回 false
dom.classList.contains('box') // true
dom.classList.contains('box11') // false
```

#### 

