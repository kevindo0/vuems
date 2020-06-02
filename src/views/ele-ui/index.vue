<template>
  <div style="margin: 10px;">
    <div class="container">
      <p class="divider" @click="show(1)">分割性</p>
    </div>
    <ms-divider v-if="flag===1" />
  </div>
</template>

<script>
import MsDivider from './components/divider'

export default {
  name: 'EleUiTest',
  components: {
    MsDivider
  },
  data() {
    return {
      flag: 0
    }
  },
  methods: {
    show(id) {
      if (this.flag === 0) {
        this.flag = id
      } else {
        this.flag = 0
      }
    }
  }
}
</script>

<style lang='scss' scoped>
.container {
  display: flex;
}
.divider {
  color: red;
  &:hover {
    color: green;
  }
}
</style>
