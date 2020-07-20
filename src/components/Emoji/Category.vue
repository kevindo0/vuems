<template>
  <div id="Categories">
    <div
      v-for="(category, index) in categories"
      :key="index"
      :class="['category', { active: category.label === current }]"
      @click="onSelect(category)"
    >
      <category-item :label="category.label" :icon="category.icon" />
    </div>
  </div>
</template>
<script>
import { categoriesDefault } from './utils/Categories'
import CategoryItem from './CategoryItem'
export default {
  name: 'Category',
  components: {
    CategoryItem
  },
  data() {
    return {
      current: 'peoples',
      categories: categoriesDefault
    }
  },
  methods: {
    onSelect(cg) {
      this.current = cg.label
      this.$emit('select', cg.label)
    }
  }
}
</script>
<style lang="scss" scoped>
#Categories {
  display: flex;
  width: 100%;
  flex-direction: row;
  align-items: center;
  border-bottom: 1px solid #e4e4e4;
  background: #f0f0f0;
  color: white;
  overflow-x: auto;
}

.category {
  padding: 5px;
  text-align: center;
  cursor: pointer;

  &.active {
    border-bottom: 3px solid #009688;
    filter: saturate(3);
    padding-bottom: 2px;
  }

  & > img {
    width: 22px;
    height: 22px;
  }

  &:hover {
    filter: saturate(3);
  }
}
</style>

