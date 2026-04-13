<script setup>
import TodoItem from './TodoItem.vue'

defineProps({
  todos: {
    type: Array,
    required: true
  }
})

const emit = defineEmits([
  'remove',
  'toggle',
  'start-edit',
  'save-edit',
  'cancel-edit'
])
</script>

<template>
  <ul class="todo-list">
    <TodoItem
      v-for="todo in todos"
      :key="todo.id"
      :todo="todo"
      @remove="emit('remove', $event)"
      @toggle="emit('toggle', $event)"
      @start-edit="emit('start-edit', $event)"
      @save-edit="emit('save-edit', $event.id, $event.text)"
      @cancel-edit="emit('cancel-edit', $event)"
    />
  </ul>
</template>

<style scoped>
.todo-list {
  list-style: none;
  padding: 0;
}
</style>