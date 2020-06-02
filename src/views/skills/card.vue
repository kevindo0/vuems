<!-- 用css3模拟翻牌效果 -->
<template>
  <div class="container">
    <div class="wraper">
      <div class="card" :class="{active: cardshow}" @click="rotate">
        <div class="card-face card-front">front</div>
        <div class="card-face card-back">back</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Card',
  data() {
    return {
      cardshow: false
    }
  },
  methods: {
    rotate() {
      this.cardshow = !this.cardshow
    }
  }
}
</script>

<style lang='scss' scoped>
.container {
  margin-top: 30px;
  margin-left: 30px;
}
.wraper {
  width: 200px;
  height: 200px;
  border: 1px solid #ccc;
  perspective: 600;
}
.card {
  position: relative;
  width: 100%;
  height: 100%;
  transition: transform 1s;
  transform-style: preserve-3d;
  backface-visibility: visible;
  cursor: pointer;
  &.active {
    transform: rotateY(180deg);
  }
}
.card-face {
  position: absolute;
  width: 100%;
  height: 100%;
  color: #fff;
  text-align: center;
  font-weight: bold;
  font-size: 40px;
  backface-visibility: hidden;
  &.card-front {
    background-color: #f00;
  }
  &.card-back {
    background-color: #4577dc;
    transform: rotateY(180deg);
  }
}
</style>
