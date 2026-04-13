<script setup>
import { ref } from 'vue'

const emit = defineEmits(['add'])
const input = ref('')

function handleAdd() {
  const text = input.value.trim()
  if (text) {
    emit('add', text)
    input.value = ''
  }
}
</script>

<template>
  <div class="input-row">
    <input
      v-model="input"
      placeholder="Enter a new todo"
      @keyup.enter="handleAdd"
    />
    <button @click="handleAdd">Add</button>
  </div>
</template>

<style scoped>
.input-row {
  display: flex;
  gap: 10px;
}

.input-row input {
  flex: 1;
  padding: 8px 10px;
}

.input-row button {
  padding: 8px 14px;
  cursor: pointer;
}
</style>