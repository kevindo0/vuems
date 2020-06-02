### 1. 技巧
#### 1. indexOf method in an object array
```js
var myArray = [{id: 5, val: 20}, {id: 6, val: 200}]
// find id = 5
myArray.map(function(e) { return e.id; }).indexOf(6) // 1
myArray.findIndex(i => i.id===6)  // 1
myArray.findIndex(i => i.id===8)  // -1  未找出
```
#### 2. setInterval，setTimeout
定时器需要在页面销毁的时候清除掉，不然会一直存在！！！

```html
<!-- 循环执行 setInterval（“方法名或方法”，“延时”） -->
<script>
  export default {
    data() {
      return {
        timer: '',
        value: 0
      };
    },
    methods: {
      get() {
        this.value ++;
        console.log(this.value);
      }
    },
    mounted() {
      this.timer = setInterval(this.get, 1000);
    },
    beforeDestroy() {
      clearInterval(this.timer);
    }
  };
</script>

<!-- 定时执行 setTimeout(“方法名或方法”, “延时”) -->
<script>
    mounted() {
      this.timer = setTimeout(this.get, 1000);
    },
    beforeDestroy() {
      clearTimeout(this.timer);
    }
  };
</script>
```
#### 3. getting a random value from a js array
```js
const months = ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"];
const randomMonth = months[Math.floor(Math.random() * months.length)];
console.log("random month =>", randomMonth);
```