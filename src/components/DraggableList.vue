<template>
  <div class="draggable-container">
    <draggable
      v-model="items"
      item-key="id"
      class="list-group"
      ghost-class="ghost"
      @start="drag = true"
      @end="drag = false"
    >
      <template #item="{ element }">
        <div class="list-group-item">{{ element.name }}</div>
      </template>
    </draggable>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import draggable from 'vuedraggable'

interface Item {
  id: number
  name: string
}

const items = ref<Item[]>([
  { id: 1, name: 'Item 1' },
  { id: 2, name: 'Item 2' },
  { id: 3, name: 'Item 3' }
])
const drag = ref(false)
</script>

<style lang="scss" scoped>
.list-group-item {
  padding: 1rem;
  margin: 0.5rem 0;
  background: white;
  border: 1px solid #ddd;
  border-radius: 4px;
  cursor: move;
}

.ghost {
  opacity: 0.5;
  background: #c8ebfb;
}
</style>