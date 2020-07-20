<template>
  <div>
    <span :class="['emoji']" :style="styleSize" v-html="emoji.data" />
  </div>
</template>
<script>
export default {
  name: 'EmojiItem',
  props: {
    emoji: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      size: 32
    }
  },
  computed: {
    styleSize() {
      return {
        fontSize: `${this.size - 5}px`,
        lineHeight: `${this.size}px`,
        height: `${this.size}px`,
        width: `${this.size}px`
      }
    }
  }
}
</script>
<style lang="scss" scoped>
.emoji {
  display: inline-block;
  text-align: center;
  padding: 3px;
  box-sizing: content-box;
  overflow: hidden;
  transition: transform 0.2s;

  cursor: pointer;

  &:hover {
    transform: scale(1.05);
  }
}
</style>
