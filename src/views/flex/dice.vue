<!-- 使用flex模拟骰子1-6个点的显示 -->
<template>
  <div style="margin: 20px;">
    <six-dice />
    <transform-dice />
  </div>
</template>

<script>
import SixDice from './components/six-dice'
import TransformDice from './components/transform-dice'

export default {
  name: 'DiceShow',
  data() {
    return {}
  },
  components: { SixDice, TransformDice }
}
</script>
