### 1. 技巧
#### 1. indexOf method in an object array
```js
var myArray = [{id: 5, val: 20}, {id: 6, val: 200}]
// find id = 5
myArray.map(function(e) { return e.id; }).indexOf(6) // 1
myArray.findIndex(i => i.id===6)  // 1
myArray.findIndex(i => i.id===8)  // -1  未找出
```