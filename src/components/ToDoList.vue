<template>
  <div class="todo">
    <div class="todo__header">
      <h1>To Do List</h1>
    </div>
    <div class="todo__body">
      <form @submit.prevent="addToDo">
        <input type="text" v-model="todo" placeholder="To do..." />
      </form>
      <ul>
        <li v-for="(todo, index) in todos" :key="index">
          <input type="checkbox" id="done" v-model="todo.done" />
          {{ todo.item }}
          <i class="fa fa-minus-circle" @click="removeToDo(index)"></i>
        </li>
      </ul>
      <div class="todo__controls">
        <button @click="sortToDo">Sort</button>
        <button @click="clear">Clear</button>
      </div>
      
    </div>
  </div>
</template>

<script>
export default {
  name: 'ToDoList',
  data() {
    return {
      todo: "",
      todos: [
      ]
    }
  },
  methods: {
    addToDo() {
      this.todos.unshift({ item: this.todo, done: false });
      this.todo = '';
    },
    removeToDo(id) {
      this.todos.splice(id, 1);
      console.log(this.todos);
    },
    sortToDo() {
      this.todos.sort(function(a, b) { return a.done - b.done });
    },
    clear() {
      this.todos = [];
    }
  }
}
</script>

<style scoped>
  .todo__header {
    text-align: center;
  }

  .todo__body {
    width: 60%;
    margin: 0 auto;
    padding: 10px;
  }

  .todo__body input {
    padding: 10px 0px 10px 10px;
    width: 98%;
    font-size: 20px;
  }

  .todo__body input[type="checkbox"] {
    display: inline-block;
    width: 20px;
  }

  .todo__body i {
    float: right;
  }

  .todo__body ul li {
    padding: 10px;
    font-size: 25px;
  }

  .todo__controls {
    width: 80%;
    margin: 0 auto;
  }

  .todo__controls button{
    font-size: 20px;
    width: 45%;
    padding: 10px 0px;
    margin: 0 2.5%;
  }
</style>
