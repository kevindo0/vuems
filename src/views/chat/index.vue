<template>
  <div
    ref="maindiv"
    class="container"
    :style="{height: (screenHeight - 50) + 'px'}"
  >
    <div class="header">
      <p>Header</p>
    </div>
    <div class="msg-content">
      <div v-for="(item, index) in conversations" :key="index">
        <div v-if="item.id!==2" class="item item-other">
          <div class="head">
            <span v-if="item.avater===''" class="head-name">{{ item.name[4] }}</span>
            <img v-else :src="item.avater" alt="">
          </div>
          <p class="content">
            {{ item.content }}
          </p>
          <!-- 撑开剩余空间 -->
          <div class="contentafter" />
          <div class="item-opt">
            <el-button size="mini" type="danger">删除</el-button>
          </div>
        </div>
        <div v-else class="item item-owner">
          <div class="head">
            <span v-if="item.avater===''" class="head-name">{{ item.name[4].toUpperCase() }}</span>
            <img v-else :src="item.avater" alt="">
          </div>
          <p class="content">
            WoW, Nice Job!
          </p>
        </div>
      </div>
    </div>
    <div class="footer">
      <el-select v-model="value" placeholder="请选择">
        <el-option
          v-for="index in 8"
          :key="index"
          :label="`user${index}`"
          :value="index"
        />
      </el-select>
      <el-input v-model="content" placeholder="请输入要发送的内容" @keyup.enter.native="send" />
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      value: '',
      content: '',
      screenHeight: document.documentElement.clientHeight,
      conversations: [
        { id: 1, avater: 'https://s3-us-west-2.amazonaws.com/s.cdpn.io/131045/smileycoffee.gif', name: 'kk', content: "So, I quickly migrated the whole thing in NoSQL. I did have to redevelop the framework's data access layer in a hurry though..." },
        { id: 2, avater: '', name: 'usernice', content: '获取100件虚拟服装！' },
        { id: 3, avater: '', name: 'user3', content: 'good man' }]
    }
  },
  mounted() {
    var _this = this
    window.onresize = function() { // 定义窗口大小变更通知事件
      console.log('resize')
      _this.screenHeight = document.documentElement.clientHeight // 窗口高度
    }
  },
  methods: {
    getWindowHeight() {
      return document.documentElement.clientHeight || window.innerHeight || document.body.clientHeight
    },
    send() {
      if (this.value === '') {
        this.$notify.warning('请选择用户')
        return
      }
      if (this.content === '') {
        this.$notify.warning('请填写要发送的内容')
        return
      }
      const obj = {
        id: this.value,
        avater: '',
        name: 'user' + this.value,
        content: this.content
      }
      console.log(obj)
      this.conversations.push(obj)
    }
  }
}
</script>
<style scoped lang='scss'>
.container{
    display:flex;
    flex-direction: column;
}
.header{
    height:50px;
    background-color: blue;
}
.msg-content{
    flex:1;
    overflow-y: scroll;
    height: 100%;
    /*background-color: red;*/
}
.footer{
    height:50px;
    background-color: yellow;
    display: flex;
}
.item {
  display: flex;
  align-items: flex-start;
  padding: 10px;
  .item-opt {
    width: 100px;
    display: flex;
    justify-content: center;
  }
  .head {
    margin-right: 15px;
  }
}
.head {
  width: 60px;
  height: 60px;
  border-radius: 5px;
  box-shadow: 2px 3px 6px 4px rgba(0, 0, 0, .6);
  img {
    display: block;
    width: 100%;
    height: 100%;
  }
}
.content {
  padding: 10px;
  margin: 0;
  display: inline;
  border-radius: 5px;
  position: relative;
}
.contentafter {
  flex: 1;
}
.item-other .content{
  background: #d7dbda;
  // box-shadow: 1px 5px 8px 4px rgba(0, 0, 0, .8);
}
.item-owner {
  flex-direction: row-reverse;
  .head {
    margin-left: 15px;
  }
  .content {
    background: #06e0b1;
    box-shadow: 1px 5px 8px 4px rgba(0, 0, 0, .8);
  }
}
.item-other .content:before,
.item-owner .content:before {
  content: "";
  position: absolute;
  top: 20px;
  z-index: 10;
  border: solid transparent;
  border-width: 8px 10px;
}
.item-other .content:before {
  left: -19px;
  border-right-color: #d7dbda;
}
.item-owner .content:before {
  right: -18px;
  border-left-color: #06e0b1;
}
.head-name {
  display: flex;
  justify-content: center;
  // align-items: center;
  width: 60px;
  height: 60px;
  color: red;
  font-size: 30px;
}
</style>
