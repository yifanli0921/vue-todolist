<template>
  <div class="header">
    <input type="text" class="todo-input" placeholder="what needs to be done" v-model="newTodo" @keyup.enter="addTodo">
    <div v-for="(todo,index) in todos" :key="todo.id"
    class="todo-item">
      <div class="todo-item-left">
      <div v-if="!todo.editing" @dblclick="editTodo(todo)"
           class="todo-item-label">{{todo.title}}</div>
      <input v-else class="todo-item-edit" type="text" v-model="todo.title">
      <div class="remove-item" @click="removeTodo(index)">
        <button>Delete</button>
      </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'todo-list',
  data () {
    return {
      newTodo: '',
      idForTodo: 3,
      todos: [
        {
          'id': 1,
          'title': 'Finish Todo List',
          'completed': false,
          'editing': false
        },
        {
          'id': 2,
          'title': 'Get a good feedback',
          'completed': false,
          'editing': false
        }
      ]
    }
  },
  methods: {
    addTodo () {
      if (this.newTodo.trim() === 0) {
        return
      }
      this.todos.push({
        id: this.idForTodo,
        title: this.newTodo,
        completed: false
      })
      this.newTodo = ''
      this.idForTodo++
    },
    editTodo (todo) {
      todo.editing = true
    },
    removeTodo (index) {
      this.todos.splice(index, 1)
    }
  }
}
</script>

<style scoped >

.header {
  display: block;
  text-align: center;
}

.todo-input {
  width: 100%;
  padding: 10px 18px;
  font-size: 18px;
  margin-bottom: 16px;
}
  :focus {
    outline: 0;
  }
.todo-item {
  margin-bottom: 12px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.todo-item-edit {
  font-size: 24px;
  font-family: Arial sans-serif;
  color: cornflowerblue;
  margin-left: 12px;
  width: 100%;
  padding: 10px;
  border: 1px solid #ccc;
}
</style>
