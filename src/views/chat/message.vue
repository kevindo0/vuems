<template>
  <div>
    <VEmojiPicker @select="selectEmoji" />
    <emoji-picker @select="selectEmoji" />
  </div>
</template>
<script>
import VEmojiPicker from 'v-emoji-picker'
import EmojiPicker from '@/components/Emoji'
export default {
  name: 'ChatMessage',
  components: {
    VEmojiPicker,
    EmojiPicker
  },
  data: () => ({}),
  methods: {
    selectEmoji(emoji) {
      console.log('get:', emoji)
    }
  }
}
</script>
