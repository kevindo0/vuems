<template>
  <div>
    <span class="svg" :title="label" v-html="icon" />
  </div>
</template>
<script>
export default {
  name: 'CategoryItem',
  props: {
    label: {
      type: String,
      required: true
    },
    icon: {
      type: String,
      required: true
    }
  }
}
</script>
