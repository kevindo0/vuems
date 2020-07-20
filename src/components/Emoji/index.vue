<template>
  <div id="EmojiPic">
    <emoji-category @select="changeCategory" />
    <emoji-list :datas="emojies" :emojis-every-row="emojisEveryRow" :emojies-width="emojiesWidth" @select="editEmoji" />
  </div>
</template>
<script>
import { mapEmojies } from './utils/Emojies'
import EmojiCategory from './Category'
import EmojiList from './EmojiList'
export default {
  name: 'EmojiPicker',
  components: {
    EmojiCategory,
    EmojiList
  },
  props: {
    emojisEveryRow: {
      type: Number,
      default: 8
    },
    emojiesWidth: {
      type: Number,
      default: 320
    }
  },
  data() {
    return {
      emojies: mapEmojies['peoples']
    }
  },
  methods: {
    changeCategory(cg) {
      this.emojies = mapEmojies[cg]
    },
    editEmoji(emoji) {
      this.$emit('select', emoji)
    }
  }
}
</script>
<style lang="scss">
#EmojiPic {
  display: inline-flex;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-rendering: optimizeSpeed;
  flex-direction: column;
  align-items: center;
  background: #f0f0f0;
  border-radius: 4px;
  border: 1px solid #e4e4e4;
  overflow: hidden;
  user-select: none;

  @media screen and (max-width: 325px) {
    width: 100%;
  }
}
</style>
