<template>
  <div ref="maindiv" class="container" 
    :style="{height: (screenHeight - 50) + 'px'}">
    <div class="header">
      <p>Header</p>
    </div>
    <div class="content">
      <div v-for="item in 25">
        <p> {{item}} Content</p>
      </div>
    </div>
    <div class="footer">
      <p>Footer</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      screenHeight: document.documentElement.clientHeight
    }
  },
  created: function() {
    var height = this.getWindowHeight()
    console.log('height:', height)
  },
  mounted () {
    var _this = this
    window.onresize = function () { // 定义窗口大小变更通知事件
      console.log('resize')
      _this.screenHeight = document.documentElement.clientHeight // 窗口高度
    }
  },
  methods: {
    getWindowHeight(){
      return document.documentElement.clientHeight || window.innerHeight || document.body.clientHeight;
    }
  }
  // watch: {
  //   'screenHeight': function (val) { // 监听屏幕高度变化
  //     var oIframe = document.getElementById('maindiv')
  //     console.log('val:', val)
  //     oIframe.style.height = (Number(val) - 50) + 'px'
  //   }
  // }
}
</script>
<style scoped>
.container{
    display:flex;
    flex-direction: column;
}
.header{
    height:50px;
    background-color: blue;
}
.content{
    flex:1;
    overflow-y: scroll;
    height: 100%;
    background-color: red;
}
.footer{
    height:50px;
    background-color: yellow;
}
</style>
