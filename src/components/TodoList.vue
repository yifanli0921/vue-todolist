<template>
  <div class="header">
    <input type="text" class="todo-input" placeholder="what needs to be done" v-model="newTodo" @keyup.enter="addTodo">
    <div v-for="(todo,index) in todos"
         :key="todo.id"
         class="todo-item">
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
    <div class="extra-container">
      <div><strong>{{remaining}} items left</strong></div>
    </div>
    <div><label class="remaining"><input type="checkbox" :checked="!anyRemaining" @change="checkAllTodos"><strong>Check All</strong></label></div>

    <div class="extra-container">
      <div>
        <button :class="{active: filter = 'all'}" @click="filter = 'all'">All</button>
        <button :class="{active: filter = 'active'}" @click="filter = 'active'">Active</button>
        <button :class="{active: filter = 'completed'}" @click="filter = 'all'">Completed</button>
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
      beforeEditCache: '',
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
  computed: {
    remaining () {
      return this.todos.filter(todo => !todo.completed).length
    },
    anyRemaining () {
      return this.remaining !== 0
    }
  },
  directives: {
    focus: {
      inserted: function (el) {
        el.focus()
      }
    }
  },
  methods: {
    addTodo () {
      if (this.newTodo.trim() === '') {
        return
      }
      this.todos.push({
        id: this.idForTodo,
        title: this.newTodo,
        completed: false,
        editing: false
      })
      this.newTodo = ''
      this.idForTodo++
    },
    editTodo (todo) {
      this.beforeEditCache = todo.title
      todo.editing = true
    },
    doneEdit (todo) {
      if (todo.title.trim() === '') {
        todo.title = this.beforeEditCache
      }
      todo.editing = false
    },
    cancelEdit (todo) {
      todo.title = this.beforeEditCache
      todo.editing = false
    },
    removeTodo (index) {
      this.todos.splice(index, 1)
    },
    checkAllTodos () {
      this.todos.forEach((todo) => todo.completed = event.target.checked)
    }
  }
}
</script>

<style scoped >

.header {
  display: block;
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
.todo-item:hover {
    color: cornflowerblue;
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
.completed {
  text-decoration: line-through;
  color: grey;
}
.remaining {
  color: mediumturquoise;
  font-size: 28px;
}
.extra-container {
  display: flex;
  align-items: center;
  justify-content: space-between;
  font-size: 28px;
  color: gold;
  border-bottom: 1px solid lightgrey;
  padding-top: 14px;
  margin-bottom: 14px;
  /*width: 50%;*/
}
.extra-container:hover {
    color: cornflowerblue;
  }
</style>
