<script setup>
import { ref, watch } from 'vue'

const props = defineProps({
  todo: {
    type: Object,
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

const editText = ref(props.todo.text)

watch(
  () => props.todo.text,
  (newVal) => {
    editText.value = newVal
  }
)

function handleSave() {
  emit('save-edit', {
    id: props.todo.id,
    text: editText.value
  })
}

function handleCancel() {
  editText.value = props.todo.text
  emit('cancel-edit', props.todo.id)
}
</script>

<template>
  <li class="todo-item">
    <template v-if="!todo.editing">
      <span
        class="todo-text"
        :class="{ done: todo.done }"
      >
        {{ todo.text }}
      </span>

      <div class="actions">
        <button @click="emit('toggle', todo.id)">
          {{ todo.done ? 'Undo' : 'Complete' }}
        </button>
        <button @click="emit('start-edit', todo.id)">Edit</button>
        <button @click="emit('remove', todo.id)">Delete</button>
      </div>
    </template>

    <template v-else>
      <input v-model="editText" class="edit-input" />
      <div class="actions">
        <button @click="handleSave">Save</button>
        <button @click="handleCancel">Cancel</button>
      </div>
    </template>
  </li>
</template>

<style scoped>
.todo-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 12px;
  padding: 12px 0;
  border-bottom: 1px solid #eee;
}

.todo-text {
  flex: 1;
}

.todo-text.done {
  text-decoration: line-through;
  color: #888;
}

.actions {
  display: flex;
  gap: 8px;
}

.actions button {
  padding: 6px 10px;
  cursor: pointer;
}

.edit-input {
  flex: 1;
  padding: 6px 8px;
}
</style>