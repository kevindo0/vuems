<template>
  <div>
    <p>Up</p>
    <el-divider class="one"></el-divider>
    <el-divider class="one"></el-divider>
    <p>Down</p>
  </div>
</template>

<script>
export default {
  name: 'MsDivider',
  data() {
    return {}
  }
}
</script>

<style lang='scss' scoped>
.one {
  background-color: green;
  margin-bottom: 5px;
  border: 1px solid #e8eaec;
}
</style>
