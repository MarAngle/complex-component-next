<style scoped>
.complex-auto-index{
  cursor: default;
}
</style>
<template>
  <span class="complex-auto-index" v-bind="$attrs">{{ currentIndex }}</span>
</template>

<script lang="ts">
import { defineComponent } from "vue"
import { PaginationData } from 'complex-data-next'

export default defineComponent({
  name: 'ComplexAutoIndex',
  props: {
    index: {
      type: Number,
      required: true
    },
    pagination: {
      type: PaginationData,
      required: false,
      default: null
    }
  },
  computed: {
    currentIndex() {
      let currentIndex = this.index + 1
      if (this.pagination) {
        const page = this.pagination.getCurrent()
        const size = this.pagination.getSize()
        currentIndex = currentIndex + (page - 1) * size
      }
      return currentIndex
    }
  }
})
</script>
