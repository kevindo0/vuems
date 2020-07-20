<template>
  <div id="Emojis">
    <div ref="container-emoji" class="container-emoji">
      <div class="grid-emojis" :style="gridDynamic">
        <emoji-item
          v-for="(emoji, index) in datas"
          :key="index"
          :emoji="emoji"
          @click.native="onSelect(emoji)"
        />
      </div>
    </div>
  </div>
</template>
<script>
import EmojiItem from './EmojiItem'

export default {
  name: 'EmojiList',
  components: {
    EmojiItem
  },
  props: {
    datas: {
      type: Array,
      required: true
    },
    emojisEveryRow: {
      type: Number,
      required: true
    },
    emojiesWidth: {
      type: Number,
      required: true
    }
  },
  computed: {
    gridDynamic() {
      const percent = this.emojiesWidth / this.emojisEveryRow
      const columns = 'repeat(' + this.emojisEveryRow + ',' + percent + 'px)'
      return {
        'grid-template-columns': columns
      }
    }
  },
  methods: {
    onSelect(emoji) {
      this.$emit('select', emoji)
    }
  }
}
</script>
<style lang="scss" scoped>
#Emojis {
  font-family: Twemoji, NotomojiColor, Notomoji, EmojiOne Color, Symbola, Noto,
    Segoe UI Emoji, OpenSansEmoji, monospace;
  display: block;
  width: 100%;
  max-width: 100%;

  ::-webkit-scrollbar {
    border-radius: 4px;
    width: 4px;
    background: #7c7c7c5b;
  }

  ::-webkit-scrollbar-track {
    border-radius: 4px;
  }

  ::-webkit-scrollbar-thumb {
    border-radius: 4px;
    background: #00000038;

    &:hover {
      background: #00000062;
    }
  }
}

.container-emoji {
  overflow-x: hidden;
  overflow-y: scroll;
  height: 200px;
}

.grid-emojis {
  display: grid;
  margin: 5px 0;
  justify-items: center;
}
</style>
