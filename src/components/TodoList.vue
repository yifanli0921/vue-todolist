<template>
  <div class="header">
    <input type="text" class="todo-input" placeholder="what needs to be done">
    Todo list goes here !
  </div>
</template>

<script>
export default {
  name: 'todo-list',
  data () {
    return {
      msg: 'Welcome to Your Todo List!'
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

</style>
