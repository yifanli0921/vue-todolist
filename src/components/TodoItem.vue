<template>
  <div class="todo-item">
    <div class="todo-item-left">
      <input class="completed" type="checkbox" v-model="todo.completed">
      <div v-if="!todo.editing" @dblclick="editTodo(todo)"
           class="todo-item-label" v-bind:class = "{completed : todo.completed } ">{{todo.title}}</div>
      <input
        v-else class="todo-item-edit"
        type="text"
        v-model="todo.title"
        @blur="doneEdit(todo)"
        @keyup.esc="cancelEdit(todo)"
        v-focus
      >
      <div class="remove-item" @click="removeTodo(index)">
        <button class="delete-button">Delete</button>
      </div>
    </div>
  </div>

</template>

<script>
export default {
  name: 'todo-item',
  props: {
    todo: {
      type: Object,
      required: true
    },
    index: {
      type: Number,
      required: true
    }
  }
}
</script>

<style scoped>

</style>
