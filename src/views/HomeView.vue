<script setup>
import { ref, watch, computed } from 'vue'
import TodoInput from '../components/TodoInput.vue'
import TodoList from '../components/TodoList.vue'

const todos = ref([])
const filter = ref('all')

const saved = localStorage.getItem('todos')
if (saved) {
  todos.value = JSON.parse(saved)
}

watch(
  todos,
  (newVal) => {
    localStorage.setItem('todos', JSON.stringify(newVal))
  },
  { deep: true }
)

function addTodo(text) {
  todos.value.push({
    id: Date.now(),
    text,
    done: false,
    editing: false
  })
}

function removeTodo(id) {
  todos.value = todos.value.filter((todo) => todo.id !== id)
}

function toggleTodo(id) {
  const todo = todos.value.find((t) => t.id === id)
  if (todo) {
    todo.done = !todo.done
  }
}

function startEdit(id) {
  const todo = todos.value.find((t) => t.id === id)
  if (todo) {
    todo.editing = true
  }
}

function saveEdit(id, newText) {
  const todo = todos.value.find((t) => t.id === id)
  if (todo && newText.trim()) {
    todo.text = newText.trim()
    todo.editing = false
  }
}

function cancelEdit(id) {
  const todo = todos.value.find((t) => t.id === id)
  if (todo) {
    todo.editing = false
  }
}

const filteredTodos = computed(() => {
  if (filter.value === 'active') {
    return todos.value.filter((todo) => !todo.done)
  }
  if (filter.value === 'completed') {
    return todos.value.filter((todo) => todo.done)
  }
  return todos.value
})

const remainingCount = computed(() => {
  return todos.value.filter((todo) => !todo.done).length
})
</script>

<template>
  <div class="container">
    <h1>Vue Todo App</h1>

    <TodoInput @add="addTodo" />

    <div class="filters">
      <button @click="filter = 'all'" :class="{ active: filter === 'all' }">
        All
      </button>
      <button @click="filter = 'active'" :class="{ active: filter === 'active' }">
        Active
      </button>
      <button
        @click="filter = 'completed'"
        :class="{ active: filter === 'completed' }"
      >
        Completed
      </button>
    </div>

    <p class="count">{{ remainingCount }} task<span v-if="remainingCount !== 1">s</span> left</p>

    <TodoList
      :todos="filteredTodos"
      @remove="removeTodo"
      @toggle="toggleTodo"
      @start-edit="startEdit"
      @save-edit="saveEdit"
      @cancel-edit="cancelEdit"
    />
  </div>
</template>

<style scoped>
.container {
  max-width: 700px;
  margin: 40px auto;
  font-family: Arial, sans-serif;
}

.filters {
  margin: 20px 0;
  display: flex;
  gap: 10px;
}

.filters button {
  padding: 8px 14px;
  border: 1px solid #ccc;
  background: white;
  cursor: pointer;
}

.filters button.active {
  font-weight: bold;
  border-color: #42b883;
}

.count {
  margin-bottom: 16px;
  color: #555;
}
</style>